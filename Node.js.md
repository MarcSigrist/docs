<h1>Node.js</h1>

- [Using Node.js](#using-nodejs)
- [Using Node Package Manager](#using-node-package-manager)
  - [Adding Packages](#adding-packages)
  - [Removing Packages](#removing-packages)
- [Using Node Version Manager for Windows](#using-node-version-manager-for-windows)

# Using Node.js

See [Node.js docs](https://nodejs.org/en/docs/).

# Using Node Package Manager

See also [npm docs](https://docs.npmjs.com).

## Adding Packages

**Adding packages from package.json**

* `npm install`: Install/update the modules listed in *package.json* in a local *node_modules* folder.
* `npm install --production`: Ignore devDependencies from *package.json*.

**Adding specific packages**

* `npm install somePackage`: Install the default (usually latest, as configured in npm-config) 
  version of somePackage from the default registry in a local *node_modules* folder.
* `npm install @someRegistry/somePackage`: Install the default version of @someRegistry/somePackage
  in a local *node_modules* folder.
* `npm install @someRegistry/somePackage@2.4.1`: Install the 2.4.1 version of @someRegistry/somePackage
  in a local *node_modules* folder.
* Parameters:
    * `-P` or `--save-prod`: Also write to *package.json* under `dependencies` (productive runtime).
    * `-D` or `--save-dev`: Also write to *package.json* under `devDependencies` 
      (non-productive runtime, e.g., unit tests, minification, typescript, ...).

**General parameters**

* `--dry-run`: Report, but don't install.
* `-f` or `--force`: Reinstall even if a local copy already exists.
* `-g` or `--global`: Install globally.
  

**Further information**: See npm CLI [install](https://docs.npmjs.com/cli/install) documentation.

## Removing Packages

* `npm uninstall somePackage`: Uninstall somePackage from the local *node_modules* folder.
* `npm uninstall @someRegistry/somePackage`: Uninstall @someRegistry/somePackage
  from the a local *node_modules* folder.
* `npm uninstall @someRegistry/somePackage@2.4.1`: Uninstall the 2.4.1 version of @someRegistry/somePackage
  from the local *node_modules* folder.
* Parameters:
    * `-S` or `--save`: Also delete from *package.json* under `dependencies` (productive runtime).
    * `-D` or `--save-dev`: Also delete from *package.json* under `devDependencies` 
      (non-productive runtime, e.g., unit tests, minification, typescript, ...).
    * `-g` or `--global`: Uninstall globally.

**Furtner information**: See npm CLI [uninstall](https://docs.npmjs.com/cli/uninstall) documentation.

# Using Node Version Manager for Windows

1. Uninstall *Node.js* from Windows if existing.
2. Delete any node..., .node..., npm... subfolders from _%programfiles%_ and _%programfiles(x86)%_.
3. Delete any paths from *Path* environment variable leading to npm.
4. Install [Node Version Manager](https://github.com/coreybutler/nvm-windows) for Windows. This creates _%NVM_HOME%_ and _%NVM_SYMLINK%_ entries in the Path environment variable.
5. From now on, install, list, etc. Node.js versions exclusively via `nvm install...`, and use nvm for Node.js version switching. There is a symbolic link _%programfiles%\nodejs_. Depending on the Node.js version you are using, the symbolic link is resolved to a Node.js version-specific subfolder in %appdata%\Roaming\nvm*.
6. Before installing any Node.js *packages* with `npm install...,` ensure `nvm on` first and check the currently active Node.js version using `nvm list`. When runing `npm install...,` npm packages will be installed only in the currently active version-specific subfolder.
