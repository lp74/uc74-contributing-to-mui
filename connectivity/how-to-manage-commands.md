@Author: Luca Polverini<br>
@E-mail: luca.polverini@it.abb.com<br>
@Date: 14 febbrary 2019

# How to manage commands

In the following paragraphs, we are going to describe how to manage UI commands through **abb-connectivity**.

Before, let's review the goals.

## Some useful factories

### Command
A <code>Command</code> is a factory that returns an object with two properties: 

- **id**:  a unique identifier for the command
- **action**: a function that performs the command action

An action may be everything needed to use the UI, such as:

- to fetch a REST resource,
- to change page (e.g tapping a menu item),
- to start a poller,
- to start a procedure,
- and so on ...

The action may return <code>any</code> and the application **shouldn't invoke the action directly**. That's because we want to have control over actions that are going to execute for the following concerns:

- Authentication (user identification) and Authorization (role management)
- Logging actions,
- Disable them temporary due to other concerns (e.g. during the firmware update),
- and so on ...

> encapsulating actions inside commands costs very little if compared with the benefits that we are going to see.

### CommandsList
In order to achieve our goals, we need a "commands manager" for all the actions that we need to check and execute. **Connectivity** provides a <code>CommandsList</code> factory that aggregates commands and permits to execute them. The <code>CommandsList</code> encapsulate commands and provides a method <code>execute({id: id, args: args})</code> to perform the command action with the desired parameters.

<code>CommandsList</code> delegate the command execution to a <code>SinglePointOfAccess</code>. This object contains a configurable security chain. Every node of the chain serves a specific task and passes the command execution to the next node after a successful check. For example, basic nodes are:

- SecurityContextNode: (create) retrieves the **singleton** security context,
- AuthenticationNode: checks the user identification,
- AuthorizationNode: checks the user rights over the command,
- SystemAvailableNode: checks if the application state permits the command execution, (TBD)
- CallNode: performs the command action,
- LoggingNode: logs the commands execution. (TBD) 


## Other benefits

Using <code>CommandsList</code>, <code>SecurityContext</code> (with AuthorizationRole), and <code>MenuItem</code> factories, it is possible to build auto-trimming menu.

## Notes
> the work on <code>CommandsList</code>, <code>SecurityContext</code>, and <code>MenuItem</code> is mature enough to start dealing with them in concrete applications.

## Design principles

- Design Patterns
- Factories 
- SOLID

## Periodic poll example

### Command Factory
Connectivity provides the <code>Command</code> factory.

```js
const security = Security(); // Facade
const commands = CommandsList(security.singlePointOfAccess);
...
const command = Command({id: 'getUnixEpoch', action: getUnixEpoch});
commands.add(command);
...
commands.execute({id:'getUnixEpoch', args: []}); // command execution
```

### IntervalNode
Connectivity provides the <code>IntervalNode</code> class.
The responsibility of this class is to periodically repeat a callback.

It implements the Observer pattern in order to update observers.

It provides other methods:
- <code>tick()</code>: to trigger an immediate execution
- <code>force(period)</code>: to take control over period
- <code>free()</code>: to restore the default period
- <code>subscribe()</code>: to update observers
- <code>map(fn)</code>: to map the value returned to something else
- ...

```js
const getUnixEpoch = () => Date.now();
const defaultPeriod = 1000;
const periodicPoll = new IntervalNode(getUnixEpoch, defaultPeriod);
periodicPoll.subscribe( data =>  {
	console.log(data);
});
```
### Composing the poller and the command
Given the <code>IntervalNode</code> class and the <code>Command</code> factory, we need to repeat a <code>Command</code> many times

```js
const callBack = () => commands.execute({id: 'getUnixEpoch', args: []});
const periodicPoll = new IntervalNode(callBack, defaultPeriod);
periodicPoll.subscribe( data =>  { ... });
```

## Role management example
```js
// Security context creation
const security = Security(); // Facade
// Commands definition
const commands = CommandsList(security.singlePointOfAccess);
commands.addCommand(Command({ id: 'getUnixEpoch', action: () => Date.now() }));
// Interval node definition (Poller)
const defaultPeriod = 100;
const action = () => commands.execute({ id: 'getUnixEpoch', args: [] });
const periodicPoll = new IntervalNode(action, defaultPeriod);
// Role definition
security.userRole.addCommandRight(CommandRight('getUnixEpoch', 7)); // rwx = 7 = 1*2**0 + 1*2**1 + 1*2**2
security.authorizationManager.addAuthorizationRole(security.userRole);
security.authenticationManager.setUserDetails({ username: 'foo',password: 'bar' });
// Consuming services
const observer = { update: promise => promise
  .then(data => {
    console.log(data);
  })
  .catch(err => {
    console.error(err);
  }) };
const subscription = periodicPoll.subscribe(observer.update);
```

The <code>Security</code> Factory

```js
function Security() {
  const authenticationProvider = AuthenticationProvider();
  const authorizationProvider = AuthorizationProvider();
  const securityContext = securityContextFn(authenticationProvider)(authorizationProvider)(SecurityContext);

  const authenticationManager = AuthenticationManager(authenticationProvider);
  const authorizationManager = AuthorizationManager(authorizationProvider);

  const callNode = CallNode();

  const authorizationNode = AuthorizationNode(authorizationManager);
  authorizationNode.setNext(callNode);

  const authenticationNode = AuthenticationNode(authenticationManager);
  authenticationNode.setNext(authorizationNode);

  const securityContextNode = SecurityContextNode(securityContext);
  securityContextNode.setNext(authenticationNode);

  const securityChain = SecurityChain();
  securityChain.setNext(securityContextNode);

  const singlePointOfAccess = SinglePointOfAccess(securityChain);

  const userRole = AuthorizationRole('USER');

  return {
    securityContext,
    singlePointOfAccess,
    authenticationManager,
    authorizationManager,
    userRole
  };
}
```
