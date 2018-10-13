# Bazel Build for [google/leveldb](https://github.com/google/leveldb)

Add to your WORKSPACE

```
http_archive(
    name = "com_github_cschuet_leveldb",
    strip_prefix = "leveldb-<SHA-1>",
    urls = [
        "https://github.com/cschuet/leveldb/archive/<SHA-1>.tar.gz",
    ],
)

load("@com_github_cschuet_leveldb//:bazel/repositories.bzl", "repositories")

repositories()
```

Compile with
```
bazel build @com_github_google_leveldb//:leveldb
```

Test with
```
bazel test @com_github_google_leveldb//...
```
