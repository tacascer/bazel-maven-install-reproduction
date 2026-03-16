# Renovate does not update Maven artifacts in `rules_jvm_external` `maven.install()`

## Current behavior

Renovate does not detect or update Maven artifact versions declared in `maven.install()` in `MODULE.bazel`. For example, `com.google.guava:guava:33.4.0-jre` is never flagged for update.

## Expected behavior

Renovate should detect Maven artifact versions in `maven.install()` and propose updates when newer versions are available (e.g., guava 33.4.0-jre -> 33.5.1-jre).

## Link to the Renovate issue or Discussion

Put your link to the Renovate issue or Discussion here.
