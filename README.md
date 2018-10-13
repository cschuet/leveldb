# Bazel Build for [google/leveldb](https://github.com/google/leveldb)

[![Build Status](https://travis-ci.org/cschuet/leveldb.svg?branch=master)](https://travis-ci.org/cschuet/leveldb)

Add to your WORKSPACE

```
http_archive(
    name = "com_github_cschuet_leveldb",
    strip_prefix = "leveldb-ebf975ddd3bb3ee289d215211a402c20107546f3",
    urls = [
        "https://github.com/cschuet/leveldb/archive/ebf975ddd3bb3ee289d215211a402c20107546f3.tar.gz",
    ],
)

load("@com_github_cschuet_leveldb//:bazel/repositories.bzl", "repositories")

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
* not using FDATASYNC
* not using Google Snappy
* assumes little endian
