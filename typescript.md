# Typescript

## installation

```bash
npm install -D typescript ts-node @types/node
```
## Use
```
tsc filename
```

## debug with VS Code

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch current file w/ ts-node",
            "protocol": "inspector",
            "args": [
                "${relativeFile}"
            ],
            "cwd": "${workspaceRoot}",
            "runtimeArgs": [
                "-r",
                "ts-node/register"
            ],
            "internalConsoleOptions": "openOnSessionStart",
            "console": "integratedTerminal"
        }
    ]
}
```