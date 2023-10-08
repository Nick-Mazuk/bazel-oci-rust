load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

#
# rules_rust
#

RULES_RUST_VERSION = "0.28.0"

RULES_RUST_SHA = "c46bdafc582d9bd48a6f97000d05af4829f62d5fee10a2a3edddf2f3d9a232c1"

RUST_EDITION = "2021"

RUST_VERSION = "1.73.0"

http_archive(
    name = "rules_rust",
    sha256 = RULES_RUST_SHA,
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/{}/rules_rust-v{}.tar.gz".format(RULES_RUST_VERSION, RULES_RUST_VERSION)],
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")

rules_rust_dependencies()

rust_register_toolchains(
    edition = RUST_EDITION,
    versions = [RUST_VERSION],
)

#
# rules_pkg
#

http_archive(
    name = "rules_pkg",
    sha256 = "8f9ee2dc10c1ae514ee599a8b42ed99fa262b757058f65ad3c384289ff70c4b8",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_pkg/releases/download/0.9.1/rules_pkg-0.9.1.tar.gz",
        "https://github.com/bazelbuild/rules_pkg/releases/download/0.9.1/rules_pkg-0.9.1.tar.gz",
    ],
)

load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")

rules_pkg_dependencies()

#
# rules_oci
#

http_archive(
    name = "rules_oci",
    sha256 = "21a7d14f6ddfcb8ca7c5fc9ffa667c937ce4622c7d2b3e17aea1ffbc90c96bed",
    strip_prefix = "rules_oci-1.4.0",
    url = "https://github.com/bazel-contrib/rules_oci/releases/download/v1.4.0/rules_oci-v1.4.0.tar.gz",
)

load("@rules_oci//oci:dependencies.bzl", "rules_oci_dependencies")

rules_oci_dependencies()

load("@rules_oci//oci:repositories.bzl", "LATEST_CRANE_VERSION", "oci_register_toolchains")

oci_register_toolchains(
    name = "oci",
    crane_version = LATEST_CRANE_VERSION,
)

load("@rules_oci//oci:pull.bzl", "oci_pull")

oci_pull(
    name = "distroless_cc",
    digest = "sha256:8aad707f96620ee89e27febef51b01c6ff244277a3560fcfcfbe68633ef09193",
    image = "gcr.io/distroless/cc",
    platforms = [
        "linux/amd64",
        "linux/arm64",
    ],
)
