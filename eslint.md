[contributing](contributing.md)

---

# ESLint

The pluggable linting utility for JavaScript and JSX.

- [eslint web site](https://eslint.org/)
- [getting started](https://eslint.org/docs/user-guide/getting-started)

## Installation

```bash
# Local
npm install eslint --save-dev

# Global
npm install -g eslint
```

## Usage

```bash
# Local
./node_modules/.bin/eslint yourfile.js

# Global
eslint yourfile.js
```

Eslint can fix

```bash
eslint yourfile.js --fix
```

### project configuration files

- .eslintignore
- .eslintrc.json

## Visual Studio Code

Visual Studio Code plugin: ESLint

### Configuration

```json
{
	"editor.tabSize": 2,
	"editor.insertSpaces": true,
	"editor.detectIndentation": true,
	"eslint.autoFixOnSave": false
}
```

---

- [contributing](contributing.md)
