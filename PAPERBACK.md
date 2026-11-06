# Reader — Paperback foundation

Personal Mihon fork. The first implementation adds a black/white/red Paperback theme,
condensed library typography, square comfortable-grid covers with divider rules,
and a three-column portrait default for fresh installs. Existing categories, filters,
selection actions, reader and extension APIs are retained.

Application ID: `app.abhavsm.reader` (debug: `.dev`). Installs beside Mihon.
Telemetry and the upstream Mihon app updater default to disabled. Extension updates
are independent and remain available.

## Keiyoushi

Open More → Settings → Browse → Extension stores → Add. Choose **Use Keiyoushi URL**,
then confirm Add. The shortcut only fills the official index URL; it does not silently
install or trust extensions. Install the extensions you want using the existing flow.

## Build and preview

Use Java 21 and the Android SDK required by the upstream build configuration.

```
./gradlew spotlessCheck testDebugUnitTest verifySqlDelightMigration
./gradlew assembleRelease -Pdist=ci -Pinclude-telemetry=false -Penable-updater=false
```

The branch Build & Test workflow uploads `reader-paperback-<commit>` with a universal
APK after checks succeed. GitHub may require enabling Actions on a new fork.
These are development builds using the debug signing configuration. A stable private
signing key must be configured before relying on upgrades between CI builds; never
commit that key. Back up test data before reinstalling an APK with a different signer.

## Scope and validation

This is an initial visual foundation, not the entire mockup. A library-level resume
row, bespoke masthead/navigation, and series-screen redesign are still pending.
No fabricated collections or reading progress are injected into the real library.

Local compilation was blocked by network access to services.gradle.org. Compilation,
formatting, device layout, extension installation/update and reading must be verified
before this branch is considered ready to merge. Test small phones, large text, dark
mode, library selection/search, restore and side-by-side installation with Mihon.

Mihon's Apache 2.0 licence and attribution remain in the repository.
