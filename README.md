# sapper-swallows-rollup-warnings

This repo is cloned from [sveltejs/sapper-template-rollup](https://github.com/sveltejs/sapper-template-rollup). A `tsconfig.json` file was then added which produces a Rollup warning.

To reproduce simply install and build the project. You will receive an error, but the accompanying warning that explains the error will not be produced:
```
$ npm install
$ npm run build
> Building...
@rollup/plugin-typescript: Couldn't process compiler options
```

To see the warning, you can override `onwarn` in `rollup.config.js` to manually print it.
```
const onwarn = (warning, onwarn) => console.error(warning.message);
```

Then run again:
```
$ npm run build
> Building...
@rollup/plugin-typescript TS18003: No inputs were found in config file '/home/bmccann/src/sapper-swallows-rollup-warnings/tsconfig.json'. Specified 'include' paths were '["src/**/*"]' and 'exclude' paths were '["node_modules"]'.
> @rollup/plugin-typescript: Couldn't process compiler options
```
