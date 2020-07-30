workspace(name = "basic_scala")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

bazel_toolchains_version="3.3.0"
bazel_toolchains_sha256="a802b753e127a6f73f3f300db5dd83fb618cd798bc880b6a87db9a8777b7939f"
http_archive(
    name = "bazel_toolchains",
    urls = [
        "https://github.com/bazelbuild/bazel-toolchains/releases/download/%s/bazel-toolchains-%s.tar.gz" % (bazel_toolchains_version, bazel_toolchains_version),
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-toolchains/archive/%s.tar.gz" % bazel_toolchains_version,
    ],
    strip_prefix = "bazel-toolchains-%s" % bazel_toolchains_version,
    sha256 = bazel_toolchains_sha256,
)

load("@bazel_toolchains//rules:rbe_repo.bzl", "rbe_autoconfig")
rbe_autoconfig(
    name = "engflow_rbe_default",
    detect_java_home = True,
    #digest = "sha256:d318041b3a16e36550e42c443e856d93710e10252e7111431802fe54b99f2dc9",
    digest = "sha256:bf084dba7794ed682dba1fdecfa7c9f924fdd7f42d35f2618826919162287629",
    registry = "gcr.io",
    #repository = "bazel-public/ubuntu1804-bazel-java11",
    repository = "bazel-public/ubuntu1604-bazel-java8",
    use_legacy_platform_definition = False,
)


skylib_version = "0.8.0"
http_archive(
    name = "bazel_skylib",
    type = "tar.gz",
    url = "https://github.com/bazelbuild/bazel-skylib/releases/download/{}/bazel-skylib.{}.tar.gz".format (skylib_version, skylib_version),
    sha256 = "2ef429f5d7ce7111263289644d233707dba35e39696377ebab8b0bc701f7818e",
)
rules_scala_version = "fb6e0f0c9383816bddccdbb1e04c90f51a8edb89"
rules_scala_version_sha256 = "3bd0152f59c28947020fb9717eb57f8e5093c7abd8da361780752d4088e5ea17"
http_archive(
    name = "io_bazel_rules_scala",
    url = "https://github.com/bazelbuild/rules_scala/archive/%s.zip" % rules_scala_version,
    type = "zip",
    strip_prefix = "rules_scala-%s" % rules_scala_version,
    sha256 = rules_scala_version_sha256,
)

load("@io_bazel_rules_scala//scala:scala.bzl", "scala_repositories")
scala_repositories()

load("@io_bazel_rules_scala//specs2:specs2_junit.bzl", "specs2_junit_dependencies", "specs2_junit_repositories")
specs2_junit_repositories()

load("@io_bazel_rules_scala//scala:toolchains.bzl", "scala_register_toolchains")
scala_register_toolchains()
