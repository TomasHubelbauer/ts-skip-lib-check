# TypeScript `skilLibCheck`

An experiment in finding out whether `skipLibCheck` actually works.

I have set up `skipLibCheck` in the `tsconfig.json` file as well as in the command line of `azure-pipelines.yml`.

The TypeScript project is invoked in an Azure Pipeline defined by `azure-pipelines.yml`:

[
  ![](https://dev.azure.com/tomashubelbauer/ts-skip-lib-check/_apis/build/status/ts-skip-lib-check-CI?branchName=master)
](https://dev.azure.com/tomashubelbauer/ts-skip-lib-check/_build/latest?definitionId=11?branchName=master)

Project option is used to let TypeScript know to pick up the `tsconfig.json` file.

- [ ] Try `skipDefaultLibCheck` & `noLib` as well

[TypeScript compiler options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
