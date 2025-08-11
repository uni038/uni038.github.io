# npm
version: 11.5.2

## `npm access`
## `npm adduser`
## `npm audit`
## `npm bugs`
## `npm cache`
## `npm ci`
clean install a project

## `npm completion`
## `npm config`
```sh
npm config set <key>=<value> [<key>=<value> ...]
npm config get [<key> [<key> ...]]
npm config delete <key> [<key> ...]
npm config list [--json]
npm config edit
npm config fix
```
- alias: c

## `npm dedupe`
## `npm deprecate`
  - `npm undeprecate`
## `npm diff`
## `npm dist-tag`
## `npm docs`
## `npm doctor`
## `npm edit`
## `npm exec`
```sh
npm exec -- <pkg>[@<version>] [args...]
npm exec --package=<pkg>[@<version>] -- <cmd> [args...]
npm exec -c '<cmd> [args...]'
npm exec --package=foo -c '<cmd> [args...]'
```
- alias: x
- 

## `npm explain`
print the chain of dependencies causing a given package to be installed in the current project
```sh
npm explain <package-spec>
```
- alias: why

## `npm explore`
## `npm find-dupes`
## `npm fund`
## `npm help`
## `npm help-search`
## `npm init`
```sh
npm init <package-spec> (same as `npx create-<package-spec>`)
npm init <@scope> (same as `npx <@scope>/create`)
```
- aliases: create, innit


## `npm install`
```sh
npm install [<package-spec> ...]
```
- aliases: add, i, in, ins, inst, insta, instal, isnt, isnta, isntal, isntall


- `npm uninstall`


## `npm install-ci-test`
npm ci & npm test

## `npm install-test`
npm install & npm test

## `npm link`
## `npm login`
## `npm logout`
## `npm ls`
list installed packages
```sh
npm ls <package-spec>
```
alias: list

## `npm org`
## `npm outdated`
## `npm owner`
## `npm pack`
create a tarball
## `npm ping`
## `npm pkg`
manage your `package.json`

## `npm prefix`
```sh
npm prefix
```
Print the local prefix to standard output. This is the closest parent directory to contain a package.json file or node_modules directory, unless -g is also specified.

## `npm profile`
## `npm prune`
## `npm publish`
  - `npm unpublish`
## `npm query`
## `npm rebuild`
## `npm repo`
## `npm restart`
## `npm root`
display npm root
```sh
npm root
```

## `npm run`
runs an arbitrary command from a package's `"scripts"` object
```sh
npm run <command> [-- <args>]
```
- aliases: run-script, rum, urn


## `npm sbom`
## `npm search`
## `npm shrinkwrap`
## `npm star`
  - `npm unstar`
## `npm stars`
## `npm start`
runs a predefined command specified in the "start" property of a package's "scripts" object
```sh
npm start [-- <args>]
```

## `npm stop`
runs a predefined command specified in the "stop" property of a package's "scripts" object
```sh
npm stop [-- <args>]
```

## `npm team`
## `npm test`
runs a predefined command specified in the "test" property of a package's "scripts" object
```sh
npm test [-- <args>]
```
- aliases: tst, t

## `npm token`
## `npm update`
update all the packages
```sh
npm update [<pkg>...]
```
- aliases: up, upgrade, udpate

## `npm version`
## `npm view`
view registry info

## `npm whoami`
Display npm username

## `npx`

