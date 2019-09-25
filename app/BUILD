package(default_visibility = ["//visibility:public"])

load("@rules_python//python:defs.bzl", "py_binary", "py_runtime")
load("@third_party_deps//:requirements.bzl", "all_requirements")
py_binary(
    name = "main",
    srcs = glob(["**/*.py"]),
    main = "main.py",
    deps = all_requirements,
    python_version = 'PY2'
)


load("@io_bazel_rules_docker//python:image.bzl", "py_image")
py_image(
    name = "app-img",
    srcs = [":main.py"],
    deps = [
        ":main"
    ],
    main = "main.py",
)

