## Publishing to Github packages using Projen

Projen is the project generator to create and maintain project configuration through code. It takes a "batteries included" approach and aims to offer dozens of different project types out of the box. One of the core functionality of the projen is publishing packages to different repositories like npm.

# Configuring projen to release to npm
We can set the following properties to configure the projen to set up release workflows for npm.
-   releaseToNpm = true
-  npmRegistryUrl = 'https://npm.pkg.github.com'
-  repository = Github Repository URL

## Projenrc

```js
const { typescript } = require('projen');

const project = new typescript.TypeScriptProject({
  name: '@username/package-name',
  authorName: 'Author Name',
  authorEmail: 'useremail@domain.com',
  defaultReleaseBranch: 'master',
  releaseToNpm: true,
  repository: 'https://github.com/username/package.git',
  npmDistTag: 'latest',
  npmRegistryUrl: 'https://npm.pkg.github.com',
});

project.synth();


``` 
