load("@io_bazel_rules_scala//scala:scala.bzl", "scala_library", "scala_binary")

scala_library(
    name = "module_b",
    srcs = [
        "ModuleB.scala",
        ],
    visibility = ["//visibility:public"],
    deps = [
        "//module_a/sources/scala/com/comma/moda:mod_a",
    ]
)