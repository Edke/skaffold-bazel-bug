load("@io_bazel_rules_docker//python:image.bzl", "py_image")

py_image(
    name = "app-img",
    srcs = ["//app:main.py"],
    deps = [
        "//app:main"
    ],
    main = "main.py",
)

