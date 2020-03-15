This repo demonstrates the use of Android Gradle Plugin's `matchingFallbacks` and `missingDimensionStrategy` features. These are used when an Android project has multiple modules with dependencies on each other, and these **modules do not agree on the number of flavor dimensions** or flavors.

## Repo structure

The app itself is a shell. It has no activities, no functionality and almost no Android code. It has 4 modules:

1. `app` module. Depends on `intermediate-1`,`intermediate-2` and `leaf`
2. `intermediate-1` module. Depends on `leaf`
3. `intermediate-2` module. Depends on `leaf`
4. `leaf` module. Has no dependencies

### Flavors

  - Only `app` and `leaf` modules care about flavors. I named the dimension as "target" and the flavors as "emulator" and "realdevice" but it doesn't really matter what you call them.
  - The intermediate modules don't care and don't even need to know about flavors.

### String resources

To demonstrate how flavors work, I've created some string resources (using gradle's `resValue` feature) in every flavor, in every module that does care about the flavor. When I build an APK for a particular flavor, I can inspect the string resource in APK analyzer to figure out which variant was used.

In this commit that you're seeing, there's a build error.

[!Build Error](screenshots/build_error.png)