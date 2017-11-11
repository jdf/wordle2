licenses(["notice"])  # "old MIT"

exports_files(["COPYING"])

cc_library(
    visibility=["//visibility:public"],
    name = "harfbuzz",
    srcs = glob(
        [
            "src/hb-*.cc",
            "src/hb-*.hh",
        ],
        exclude = [
            "src/hb-coretext.cc",
            "src/hb-fallback-shape.cc",
            "src/hb-glib.cc",
            "src/hb-gobject-enums.cc",
            "src/hb-gobject-structs.cc",
            "src/hb-graphite2.cc",
            "src/hb-icu.cc",
            "src/hb-uniscribe.cc",
            "src/hb-directwrite.cc",
        ],
    ) + ["src/hb-ucdn/ucdn.c"],
    hdrs = [
        "src/hb.h",
        "src/hb-blob.h",
        "src/hb-buffer.h",
        "src/hb-common.h",
        "src/hb-deprecated.h",
        "src/hb-face.h",
        "src/hb-font.h",
        "src/hb-ft.h",
        "src/hb-ot.h",
        "src/hb-ot-font.h",
        "src/hb-ot-layout.h",
        "src/hb-ot-math.h",
        "src/hb-ot-shape.h",
        "src/hb-ot-tag.h",
        "src/hb-ot-var.h",
        "src/hb-set.h",
        "src/hb-shape.h",
        "src/hb-shape-plan.h",
        "src/hb-ucdn/ucdn.h",
        "src/hb-ucdn/ucdn_db.h",
        "src/hb-unicode.h",
        "src/hb-version.h",
    ],
    copts = [
        "-Wno-deprecated",
    ],
    defines = [
        "HAVE_OT",
        "HAVE_UCDN",
        "HAVE_FREETYPE",
    ],
    includes = [
        "src",
        "src/hb-ucdn",
    ],
    deps = [
        "//third_party/freetype:freetype_noharfbuzz",
    ],
)
