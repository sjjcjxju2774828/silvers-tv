# silver's TV build notes
Rebrand applied: app name, in-app texts (all locales), logo, launcher icons.
Build (JDK 17+, Android Studio / Android SDK installed):
  ./gradlew :androidApp:assembleFullDebug  # quick test build, installs as com.nuviodebug.com (debug-signed)
  ./gradlew :androidApp:assembleRelease   # needs release keystore properties, otherwise unsigned

Changes beyond the rebrand:
- In-app updater disabled (androidFull AppFeaturePolicy): it pointed at the original NuvioMedia/NuvioMobile GitHub releases.
- Release builds already minify + shrink resources by default; per-ABI APKs are produced by assembleRelease (use the arm64-v8a one for most phones).
- Crash reporting (Sentry) only activates if SENTRY_DSN is set in your build config; leave it unset to keep it off.
