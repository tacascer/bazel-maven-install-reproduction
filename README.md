# Renovate + Bazel `maven.install()` reproduction

Minimal reproduction showing that Renovate **can** detect and update Maven artifacts in `rules_jvm_external` `maven.install()` — but only when the `repositories` parameter is explicitly set.

## Key finding

Without an explicit `repositories` field in `maven.install()`, Renovate's `bazel-module` manager has no registry URL to query and silently skips Maven dependency updates. Adding `repositories` pointing to Maven Central fixes this:

```starlark
maven.install(
    artifacts = [
        "com.google.guava:guava:33.4.0-jre",
    ],
    lock_file = "//:maven_install.json",
    repositories = [
        "https://repo1.maven.org/maven2/",
    ],
)
```

With the `repositories` field present, Renovate correctly proposes updating guava from `33.4.0-jre` to `33.5.0-jre`.

## Link to the Renovate issue or Discussion

https://github.com/renovatebot/renovate/discussions/27467
