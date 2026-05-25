# Android DPI test APKs

Built on 2026-05-25 from the Android release configuration (`TARGET=ANDROID`,
`PLAY=y`, `DEBUG=n`).

These APKs are test artifacts for the display DPI work only. They do not include
maps, profiles, screenshots, or device data.

## Files

- `XCSoar-android-bigme-dpi-workaround-2026-05-25.apk`
  - Source branch: `android-bigme-dpi-workaround`
  - Commit: `4a9c0e6327 Android: Work around Bigme HiBreak display DPI`
  - Scope: exact Bigme HiBreak OpenAndroid symptom only.
- `XCSoar-android-display-dpi-correction-2026-05-25.apk`
  - Source branch: `android-display-dpi-correction`
  - Commit: `7c3d08080e Android: Add display DPI correction option`
  - Scope: generic expert option and startup prompt for inconsistent Android
    physical DPI reports.
- `XCSoar-android-bigme-and-display-dpi-correction-2026-05-25.apk`
  - Source branch: `android-bigme-and-display-dpi-correction`
  - Commit: `66dbf37904 Merge branch 'android-display-dpi-correction' into android-bigme-and-display-dpi-correction`
  - Scope: integration build containing both branches.

## Background

The Bigme device reports a normal logical density (`densityDpi=300`) but
inconsistent physical DPI values (`xdpi=188`, `ydpi=667`) to XCSoar. Android's
`DisplayMetrics.xdpi` and `ydpi` are vendor/firmware calibration values; they
are not recalculated from `wm size` and `wm density`. XCSoar uses these
physical DPI values for layout scaling, so the inconsistent firmware values can
make text look too thick and connected on the color e-paper display.
