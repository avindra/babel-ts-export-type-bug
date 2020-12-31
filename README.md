This repo contains the minimum needed to demonstrate the type erasure bug seen in Babel's typescript mode.

## Issues

It was seen in [Recharts Issue #2360](https://github.com/recharts/recharts/issues/2360).

 * [Babel #12578](https://github.com/babel/babel/issues/12578)
 * [Babel #11464](https://github.com/babel/babel/issues/11464)


## Reproduce

Check the checked-in `es6` folder to see what babel is currently emitting, or run `npm run build` / `yarn build` locally.

Expected:

`SomeType` is erased from `es6/index.js`

Actual:

`SomeType` is still referenced in `es6/index.js`


This is a problem for all the JavaScript (non-Typescript) consumers since the type does not exist in the build. 

If we check `es6/ModuleA.js`, we can see `SomeType` is erased, so it's at least partly working.
