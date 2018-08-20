<h1>Node.js</h1>

- [Using Node.js](#using-nodejs)
- [Using Node Package Manager](#using-node-package-manager)
  - [The Package Configuration File *package.json*](#the-package-configuration-file-packagejson)
  - [Adding Packages](#adding-packages)
  - [Removing Packages](#removing-packages)
- [Using Node Version Manager for Windows](#using-node-version-manager-for-windows)

# Using Node.js

See [Node.js docs](https://nodejs.org/en/docs/).

# Using Node Package Manager

See also [npm docs](https://docs.npmjs.com).

## The Package Configuration File *package.json*

Optional, but highly recommended. Configures a project's dependencies in a central JSON file,
including custom scripts to be run by npm, etc.

```js
{
    // Dependencies
    "dependencies": {
        "@angular/common": "6.1.3",
        "@angular/compiler": "6.1.3",
        // etc.
    },
    // Dependencies needed only at development time
    "devDependencies": {
        "lite-server": "2.4.0",
        "typescript": "3.0.1",
      // etc.
    },
    // Abbreviations for <command> in npm run <command>
    "scripts": {
        "start": "concurrently \"npm run tscwatch\" \"npm run lite\" ",
        "tsc": "tsc",
        // etc.
    }
}
```

Use [Node.js semantic version syntax](https://github.com/npm/node-semver) to specify
version ranges (e.g., `~1.2.3`) or prerelease tags (e.g., `1.2.3-alpha.3`), or to use
functions in the version logic. 


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

2. Delete any node..., .node..., npm... subfolders from 
   _%programfiles%_ and _%programfiles(x86)%_.

3. Delete any paths from *Path* environment variable leading to npm.

4. Install [Node Version Manager](https://github.com/coreybutler/nvm-windows) for Windows. 
   This creates _%NVM_HOME%_ and _%NVM_SYMLINK%_ entries in the Path environment variable.

5. From now on, install, list, etc. Node.js versions exclusively via `nvm install...`,
   and use nvm for Node.js version switching. There is a symbolic link _%programfiles%\nodejs_,
   who is resolved to a version-specific subfolder in *%appdata%\Roaming\nvm*, depending
   on the Node.js version you are currently using (e.g., *v 10.9.0*).

   **Note**: If npm is not available after installing a new Node.js version with `nvm install...`
   (e.g., `npm --version` returns an error),
      1. Make sure you have the latest version of *Node Version Manager for Windows* installed.
         (`nvm --version` should return the
         [latest release](https://github.com/coreybutler/nvm-windows/releases).)
      3. If you are running an old version,
         1. in Windows Explorer, go to `%NVM_HOME%`.
         2. Manually delete the incomplete Node.js version folder (who is missing npm,
            e.g., *v10.9.0*).
         3. Go to step 4 above (install the latest version of *Node Version Manager for Windows*),
            and continue from there.

6. Before installing any Node.js *packages* with `npm install...,` ensure `nvm on` first and 
   check the currently active Node.js version using `nvm list`. When runing `npm install...,`
   npm packages will be installed only in the currently active version-specific subfolder.  
