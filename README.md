# Bazel Build for [google/leveldb](https://github.com/google/leveldb)

[![Build Status](https://travis-ci.org/cschuet/leveldb.svg?branch=master)](https://travis-ci.org/cschuet/leveldb)

Add to your WORKSPACE

```
http_archive(
    name = "com_github_cschuet_leveldb",
    strip_prefix = "leveldb-aa785abf30e043110a6258eeefad25ae4d27f677",
    sha256 = "b484e7a4777741c82d265d1192985d9e662b2e0a193638253ebb3060ac62890c",
    urls = [
        "https://github.com/cschuet/leveldb/archive/aa785abf30e043110a6258eeefad25ae4d27f677.tar.gz",
    ],
)

load("@com_github_cschuet_leveldb//:bazel/repositories.bzl", "repositories")

repositories()

load("@com_github_cschuet_snappy//:bazel/repositories.bzl", "repositories")

repositories()

load("@com_github_cschuet_crc32c//:bazel/repositories.bzl", "repositories")

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
* uses FDATASYNC
* assumes little endian
