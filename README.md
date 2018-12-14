# Circle CI React Native Orb

## Overview

An orb for building React Native applications. Assumes the usage of Fastlane. By default, it:

- Installs dependencies with yarn and caches them
- Installs gem dependencies (typically for Fastlane) and caches them
- Installs gradle dependencies and caches them
- Runs jest tests via `yarn test:ci`, which is expected to leverage junit reporter like so: `jest --reporters=default --reporters=jest-junit`. This does require jest-junit to be installed as a devDependency.
- Decodes an Android keystore from \$ANDROID_ENCODED_KEYSTORE and saves to android.keystore for later use. encode with `cat <path-to-keystore-file> | base64 | pbcopy`
- Override ENV vars with branch-specific ENV vars if they exist. example: API_URL_BETA or BETA_API_URL would override API_URL (use pre_build hook to override this)
- Creates an .env file containing current ENV vars for use by react-native-config and others (use pre_build hook to override this)

## Other useful features

- pre_build, build, and post_build hooks to customize your build process
- overridable test_steps for jest

## Caveats

- Assumes that Fastlane will inject signing config for Android via gradle properties and uses the encoded keystore mentioned above.

## TODO

- Detox config coming soon

---

## Fastlane Configuration

You'll want to use it. Examples coming soon.
