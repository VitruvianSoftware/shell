"""Targets in the repository root"""

load("@gazelle//:def.bzl", "gazelle")

exports_files(
    [
        ".shellcheckrc",
    ],
    visibility = ["//:__subpackages__"],
)

# We prefer BUILD instead of BUILD.bazel
# gazelle:build_file_name BUILD
# gazelle:exclude githooks/*
# Standalone Pulumi IaC modules under infrastructure/pulumi/* are run via the
# pulumi CLI / //tools/pulumi bazel wrappers — not built by Bazel — so keep
# gazelle out of them (it otherwise collides with the pulumi_project targets).
# gazelle:exclude infrastructure
# tools/pulumi holds a hand-authored macro (defs.bzl) + wrapper scripts; gazelle
# would otherwise generate a bzl_library with an unresolvable rules_shell dep.
# gazelle:exclude tools/pulumi

gazelle(
    name = "gazelle",
    env = {
        "ENABLE_LANGUAGES": ",".join([
            "starlark",
        ]),
    },
    gazelle = "@multitool//tools/gazelle",
)
