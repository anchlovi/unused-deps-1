workspace(name = "ext_repo")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

rules_scala_version="dd699df9d65c4768f09e9135f1f3673d599dd330" # update this as needed
rules_scala_version_sha256="e14011a7698bf7442bc7083658a6ebbed038b94916c344529a239225d0bb7a3a"

http_archive(
    name = "io_bazel_rules_scala",
    url = "https://github.com/Jamie5/rules_scala/archive/%s.zip"%rules_scala_version,
    type = "zip",
    strip_prefix= "rules_scala-%s" % rules_scala_version,
    sha256 = rules_scala_version_sha256,
)


load("@io_bazel_rules_scala//scala:scala.bzl", "scala_repositories")
scala_repositories(scala_version_shas = (
    "2.12.10",
    {
        "scala_compiler": "cedc3b9c39d215a9a3ffc0cc75a1d784b51e9edc7f13051a1b4ad5ae22cfbc0c",
        "scala_library": "0a57044d10895f8d3dd66ad4286891f607169d948845ac51e17b4c1cf0ab569d",
        "scala_reflect": "56b609e1bab9144fb51525bfa01ccd72028154fc40a58685a1e9adcbe7835730",
    }
))

register_toolchains("//:toolchain")

protobuf_version="09745575a923640154bcf307fba8aedff47f240a"
protobuf_version_sha256="416212e14481cff8fd4849b1c1c1200a7f34808a54377e22d7447efdf54ad758"

http_archive(
    name = "com_google_protobuf",
    url = "https://github.com/protocolbuffers/protobuf/archive/%s.tar.gz" % protobuf_version,
    strip_prefix = "protobuf-%s" % protobuf_version,
    sha256 = protobuf_version_sha256,
)

# bazel-skylib 0.8.0 released 2019.03.20 (https://github.com/bazelbuild/bazel-skylib/releases/tag/0.8.0)
skylib_version = "0.8.0"
http_archive(
    name = "bazel_skylib",
    type = "tar.gz",
    url = "https://github.com/bazelbuild/bazel-skylib/releases/download/{}/bazel-skylib.{}.tar.gz".format (skylib_version, skylib_version),
    sha256 = "2ef429f5d7ce7111263289644d233707dba35e39696377ebab8b0bc701f7818e",
)