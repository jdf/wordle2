cc_binary(
    name = "main",
    srcs = ["main.cpp"],
    linkopts =
        select({
            "@bazel_tools//tools/osx:darwin": [
                "-Wl,-framework,OpenGL",
            ],
            "//conditions:default": [
                # ???
            ],
        }),
    deps = [
        "//third_party/SDL2",
        "//third_party/freetype",
        "//third_party/libpng",
    ],
)
