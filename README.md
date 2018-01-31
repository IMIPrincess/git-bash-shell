git-bash-shell
===========

[![NPM version](https://img.shields.io/npm/v/git-bash-shell.svg?style=flat-square)](https://www.npmjs.com/package/git-bash-shell)
[![AppVeyor](https://img.shields.io/appveyor/ci/gucong3000/git-bash-shell.svg)](https://ci.appveyor.com/project/gucong3000/git-bash-shell)

Use Linux command under Windows

## Why

- Use Git [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) as cross-platform shell for child process or [npm run scripts](https://docs.npmjs.com/cli/run-script).
- Support [POSIX](https://en.wikipedia.org/wiki/POSIX) file path.
- Support [shebangs](https://en.wikipedia.org/wiki/Shebang_(Unix))
- Support [PATHEXT](https://github.com/joyent/node/issues/2318)

## Install

```bash
npm install --save git-bash-shell
```

## Usage

Use cross-platform shell for [npm run scripts](https://docs.npmjs.com/cli/run-script).
In your package.json file, you can add scripts using `bash` or `sh`:

```json
"scripts": {
	"foo": "bash bin/my_script.sh",
	"bar": "sh -c \"[ ! `git diff` ]\" || echo file(s) changed!"
}
```

```javascript
require('git-bash-shell');
const spawn = require('child_process').spawn;
const ls = spawn('cat', ['README.md']);

ls.stdout.on('data', (data) => {
	console.log(`stdout: ${data}`);
});

ls.stderr.on('data', (data) => {
	console.log(`stderr: ${data}`);
});

ls.on('close', (code) => {
	console.log(`child process exited with code ${code}`);
});
```
