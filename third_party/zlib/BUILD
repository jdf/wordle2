package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # BSD/MIT-like license

exports_files(["README"])

cc_library(
    name = "zlib",
    srcs = glob(
        [
            "*.h",
            "*.c",
        ],
        exclude = ["zlib.h"],
    ),
    hdrs = ["zlib.h"],
)
