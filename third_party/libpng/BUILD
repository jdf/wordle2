package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # BSD/MIT-like license

exports_files(["LICENSE"])


cc_library(
    name = "libpng",
    srcs = glob(
        [
            "*.h",
            "*.c",
        ],
        exclude = ["png.h"],
    ),
    hdrs = ["png.h"],
    includes = ["."],
    #linkopts = ["-lm"],
    deps = ["//third_party/zlib"],
)
