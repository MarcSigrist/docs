<h1>Node.js</h1>

- [Using Node Version Manager for Windows](#using-node-version-manager-for-windows)

# Using Node Version Manager for Windows

1. Uninstall *Node.js* from Windows if existing.
2. Delete any node..., .node..., npm... subfolders from _%programfiles%_ and _%programfiles(x86)%_.
3. Delete any paths from *Path* environment variable leading to npm.
4. Install [Node Version Manager](https://github.com/coreybutler/nvm-windows) for Windows. This creates _%NVM_HOME%_ and _%NVM_SYMLINK%_ entries in the Path environment variable.
5. From now on, install, list, etc. Node.js versions exclusively via `nvm install...`, and use nvm for Node.js version switching. There is a symbolic link _%programfiles%\nodejs_. Depending on the Node.js version you are using, the symbolic link is resolved to a Node.js version-specific subfolder in %appdata%\Roaming\nvm*.
6. Before installing any Node.js *packages* with `npm install...,` ensure `nvm on` first and check the currently active Node.js version using `nvm list`. When runing `npm install...,` npm packages will be installed only in the currently active version-specific subfolder.
