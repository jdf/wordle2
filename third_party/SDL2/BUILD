licenses(["notice"])  # zlib, portions BSD, MIT, PostgreSQL

exports_files(["LICENSE"])

cc_library(
    name = "SDL2",
    srcs =
        select({
            "@bazel_tools//tools/osx:darwin": glob([
                "lib/osx/*.a",
                "lib/osx/*.dylib",
            ]),
            "//conditions:default": [
            ],
        }),
    hdrs = glob(["include/**/*.h"]),
    copts = [
        "-I/usr/X11R6/include",
        "-D_THREAD_SAFE",
    ],
    includes = ["include/SDL2"],
    linkopts =
        select({
            "@bazel_tools//tools/osx:darwin": [
                "-lm",
                "-liconv",
                "-Wl,-framework,CoreAudio",
                "-Wl,-framework,AudioToolbox",
                "-Wl,-framework,ForceFeedback",
                "-lobjc",
                "-Wl,-framework,CoreVideo",
                "-Wl,-framework,Cocoa",
                "-Wl,-framework,Carbon",
                "-Wl,-framework,IOKit",
            ],
            "//conditions:default": [
                # ???
            ],
        }),
    visibility = ["//visibility:public"],
)
