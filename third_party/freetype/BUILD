licenses(["notice"])  # BSD-style

exports_files(["LICENSE"])

COMPILED_SOURCES = [
    "src/autofit/autofit.c",
    "src/base/ftbase.c",
    "src/base/ftbbox.c",
    "src/base/ftbdf.c",
    "src/base/ftbitmap.c",
    "src/base/ftcid.c",
    "src/base/ftdebug.c",
    "src/base/ftfntfmt.c",
    "src/base/ftfstype.c",
    "src/base/ftgasp.c",
    "src/base/ftglyph.c",
    "src/base/ftgxval.c",
    "src/base/ftinit.c",
    "src/base/ftlcdfil.c",
    "src/base/ftmm.c",
    "src/base/ftotval.c",
    "src/base/ftpatent.c",
    "src/base/ftpfr.c",
    "src/base/ftstroke.c",
    "src/base/ftsynth.c",
    "src/base/ftsystem.c",
    "src/base/fttype1.c",
    "src/base/ftwinfnt.c",
    "src/bzip2/ftbzip2.c",
    "src/cache/ftcache.c",
    "src/cff/cff.c",
    "src/cid/type1cid.c",
    "src/gxvalid/gxvalid.c",
    "src/gzip/ftgzip.c",
    "src/lzw/ftlzw.c",
    "src/otvalid/otvalid.c",
    "src/psaux/psaux.c",
    "src/pshinter/pshinter.c",
    "src/psnames/psnames.c",
    "src/sfnt/sfnt.c",
    "src/smooth/smooth.c",
    "src/truetype/truetype.c",
    "src/type1/type1.c",
]

IMPL_SRCS = COMPILED_SOURCES + glob([
    "src/**/*.h",
    "include/freetype/internal/**/*.h",
])

HEADERS = glob([
    "include/freetype/*.h",
    "include/freetype/config/*.h",
]) + ["include/ft2build.h"]

IMPL_HEADERS = HEADERS + ["include/freetype/internal/internal.h"] + glob(
    ["src/**/*.c"],
    exclude = COMPILED_SOURCES,
)

IMPL_DEPS = ["//third_party/libpng"]

COPTS = [
    "-Wno-covered-switch-default",
    "-DFT_CONFIG_OPTION_SYSTEM_ZLIB",
    "-DFT_CONFIG_CONFIG_H=<ftconfig.h>",
    "-DFT_CONFIG_OPTION_USE_PNG",
    "-DFT2_BUILD_LIBRARY",
    "-DFT_CONFIG_MODULES_H=<ftmodule.h>",
    "-Ithird_party/freetype/include",
    "-Ithird_party/freetype/include/freetype",
    "-Ithird_party/freetype/include/freetype/config",
    # below due to src/cff/cf2intrp.c 'cf2_interpT2CharString'
    "$(STACK_FRAME_UNLIMITED)",
]

HARFBUZZ_COPTS = ["-DFT_CONFIG_OPTION_USE_HARFBUZZ"]

# This target is just for harfbuzz to dep on; it doesn't dep on harfbuzz.
cc_library(
    name = "freetype_noharfbuzz",
    hdrs = HEADERS,
    copts = COPTS,
    includes = ["include"],
    visibility = ["//third_party/harfbuzz:__pkg__"],
    deps = [":freetype_noharfbuzz_impl"],
)

cc_library(
    name = "freetype_noharfbuzz_impl",
    srcs = IMPL_SRCS,
    hdrs = IMPL_HEADERS,
    copts = COPTS,
    visibility = ["//visibility:private"],
    deps = IMPL_DEPS,
)

# This target is for application code to dep on; it has access to harfbuzz.
cc_library(
    name = "freetype",
    hdrs = HEADERS,
    copts = COPTS + HARFBUZZ_COPTS,
    includes = ["include"],
    visibility = ["//visibility:public"],
    deps = [":freetype_impl"],
)

cc_library(
    name = "freetype_impl",
    srcs = IMPL_SRCS,
    hdrs = IMPL_HEADERS,
    copts = COPTS + HARFBUZZ_COPTS,
    visibility = ["//visibility:private"],
    deps = IMPL_DEPS + ["//third_party/harfbuzz"],
    alwayslink = 1,
)
