licenses(["notice"])  # Apache 2

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_package",
)
load("//bazel/wasm:wasm.bzl", "wasm_cc_binary")

envoy_package()

envoy_cc_library(
    name = "test_cpp_plugin",
    srcs = [
        "test_cpp.cc",
        "test_cpp_null_plugin.cc",
    ],
    copts = ["-DNULL_PLUGIN=1"],
    deps = [
        "//external:abseil_node_hash_map",
        "//source/common/common:assert_lib",
        "//source/common/common:c_smart_ptr_lib",
        "//source/extensions/common/wasm:wasm_hdr",
        "//source/extensions/common/wasm:wasm_lib",
        "//source/extensions/common/wasm:well_known_names",
        "//source/extensions/common/wasm/ext:envoy_null_plugin",
        "@proxy_wasm_cpp_sdk//contrib:contrib_lib",
    ],
)

wasm_cc_binary(
    name = "test_cpp.wasm",
    srcs = ["test_cpp.cc"],
    deps = [
        "//source/extensions/common/wasm/ext:declare_property_cc_proto",
        "//source/extensions/common/wasm/ext:envoy_proxy_wasm_api_lib",
        "@proxy_wasm_cpp_sdk//:proxy_wasm_intrinsics_lite",
        "@proxy_wasm_cpp_sdk//contrib:contrib_lib",
    ],
)
