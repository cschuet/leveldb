licenses(["notice"])

exports_files(["LICENSE"])

genrule(
    name = "port_config_h",
    srcs = ["@com_github_cschuet_leveldb//bazel/third_party/leveldb:port_config.h"],
    outs = ["port/port_config.h"],
    cmd = "cp $< $@",
)

genrule(
    name = "port_h",
    srcs = ["@com_github_cschuet_leveldb//bazel/third_party/leveldb:port.h"],
    outs = ["port/port.h"],
    cmd = "cp $< $@",
)

cc_library(
    name = "leveldb",
    srcs = glob(
        ["**/*.cc"],
        exclude = [
            "doc/**",
            "**/*_test.cc",
            "db/leveldbutil.cc",
            "db/db_bench.cc",
        ],
    ),
    hdrs = glob(
        ["**/*.h"],
        exclude = ["doc/**"],
    ) + [
        ":port_h",
        ":port_config_h",
    ],
    includes = ["include"],
    deps = [
        "@com_github_google_crc32c//:crc32c",
    ],
)

[cc_test(
    name = src.replace("/", "_").replace(".cc", ""),
    srcs = [src],
    deps = [
        ":leveldb",
        "@com_google_googletest//:gtest_main",
    ],
) for src in glob(
    ["**/*_test.cc"],
)]
