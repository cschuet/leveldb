# Bazel Build for [google/leveldb](https://github.com/google/leveldb)

Add to your WORKSPACE

```
http_archive(
    name = "com_github_cschuet_leveldb",
    sha256 = "ed9d0a7d2648bcbbc89556562622f4fe1adf49fa8564fd859934636e2d78a06c",
    strip_prefix = "leveldb-9b605d3be7938b378a8110e481933b531e8e22b0",
    urls = [
        "https://github.com/cschuet/leveldb/archive/9b605d3be7938b378a8110e481933b531e8e22b0.tar.gz",
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

## Limitations
* not using FDATASYNC
* not using Google crc32c
* not using Google Snappy
* assumes little endian
