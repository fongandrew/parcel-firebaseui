# Parcel FirebaseUI Bug Repro

This is a minimal repro for a weird bug where `require('firebaseui')` instead returns the `dialog-polyfill` module, a dependency of the `firebaseui` package.

## Repro Steps

* Call `npm run serve`
* Go to `localhost:1234` and open the console.
* You can now inspect the output of both `require('firebaseui')` and `require('dialog-polyfill')`.

## Observations

* Per its README, the `firebaseui` module is supposed to have an `auth` property. That's not present at all on what's returned by `require('firebaseui')`.
* The objects for `require('firebaseui')` and `require('dialog-polyfill')` seem to be shallowly equal but not identical.
* This only happens with Parcel. I'm unable to repro this with Webpack or in the Node CLI with JSDOM.
