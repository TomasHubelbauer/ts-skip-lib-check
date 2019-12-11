# TypeScript `skipLibCheck`

This repository began as a playground for me to find out why `skipLibCheck` doesn't ignore `*.d.ts` files in my
project. During my research I found out that the poorly documented compiler option actually doesn't skip the
definition files, instead it just loosens the type checking going on in them. This has been found in a Stack
Overflow answer:

[Usage of the TypeScript compiler argument `skipLibCheck`](https://stackoverflow.com/q/52311779/2715716)

> New --skipLibCheck TypeScript 2.0 adds a new --skipLibCheck compiler option that causes type checking of
> declaration files (files with extension .d.ts) to be skipped. When a program includes large declaration files,
> the compiler spends a lot of time type checking declarations that are already known to not contain errors, and
> compile times may be significantly shortened by skipping declaration file type checks.

> Since declarations in one file can affect type checking in other files, some errors may not be detected when
> `--skipLibCheck` is specified. For example, if a non-declaration file augments a type declared in a declaration
> file, errors may result that are only reported when the declaration file is checked. However, in practice such
> situations are rare.

This means that the compiler option will not exclude `*.d.ts` file from the project, instead it is a performance
boost which comes at an expense of the type checking soundness.

[TypeScript compiler options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)

I have originally started exploring this to see why TypeScript compiler goes to `node_modules` and check `.d.ts`
files there even though I have set this compiler option.

I have also used `exclude` in `tsconfig.json` to ignore `node_modules`, but in my other project,
[QR Channel](https://github.com/TomasHubelbauer/qr-channel), this didn't work. In this repro it does. Need to
find out why.
