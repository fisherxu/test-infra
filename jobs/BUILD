package(default_visibility = ["//visibility:public"])

py_binary(
    name = "config_sort",
    srcs = ["config_sort.py"],
    data = [
        ":jobs",
        "//boskos:resources.json",
        "//prow:configs",
    ],
    deps = ["@ruamel_yaml//ruamel/yaml:ruamel.yaml"],
)

py_test(
    name = "config_test",
    srcs = [
        "config_test.py",
    ],
    data = [
        "//boskos:resources.json",
        "//jobs",
        "//prow:config.yaml",
    ],
    deps = [
        ":config_sort",
        ":env_gc",
    ],
)

py_binary(
    name = "env_gc",
    srcs = ["env_gc.py"],
    data = [
        ":jobs",
    ],
)

filegroup(
    name = "jobs",
    srcs = glob([
        "*.sh",
        "*.env",
        "*.json",
    ]),
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [":package-srcs"],
    tags = ["automanaged"],
)
