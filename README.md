# Expo DocumentPicker: Inconsistent 'cancelled' Status on Android

This repository demonstrates an intermittent bug in Expo's `DocumentPicker.getDocumentAsync()` API on Android.  The issue is that the promise sometimes resolves with a `cancelled` status despite the user successfully selecting a file. This is inconsistent and occurs unpredictably.

## Bug Reproduction

1.  Run the `bug.js` example.
2.  Select a file in the Android file picker.
3.  Observe that the promise may resolve with `cancelled` even when a file was chosen.

## Potential Causes and Workarounds (Solution in bugSolution.js)

The root cause isn't definitively known, but potential factors include race conditions or subtle timing issues within the Android file picker integration.  The solution explored uses a retry mechanism to improve consistency, although this doesn't guarantee a perfect fix and may not be suitable for all applications.  Alternative solutions might involve investigating asynchronous task management within the app, although it's likely the source is in the Expo DocumentPicker integration itself.

## Additional Notes

This bug was observed on [Insert Android version and device information here].  Additional testing on various Android versions and devices is encouraged to determine the scope of the problem.