package(default_visibility = ["//visibility:public"])

config_setting(
    name = "use_pre_cxx11_abi",
    values = {
        "define": "abi=pre_cxx11_abi",
    }
)

cc_library(
    name = "logging",
    hdrs = [
        "TRTorchLogger.h",
    ],
    srcs = [
        "TRTorchLogger.cpp",
    ],
    deps = [
        "@tensorrt//:nvinfer"
    ] + select({
        ":use_pre_cxx11_abi":  ["@libtorch_pre_cxx11_abi//:libtorch"],
        "//conditions:default":  ["@libtorch//:libtorch"],
    })
)

load("@rules_pkg//:pkg.bzl", "pkg_tar")

pkg_tar(
    name = "include",
    package_dir = "core/util/logging",
    srcs = ["TRTorchLogger.h"],
)
