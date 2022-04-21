load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "nlohman_json",
    sha256 = "5daca6ca216495edf89d167f808d1d03c4a4d929cef7da5e10f135ae1540c7e4",
    strip_prefix = "json-3.10.5",
    urls = ["https://github.com/nlohmann/json/archive/refs/tags/v3.10.5.tar.gz"],
    build_file_content = """
# Description:
#    json lib or something
licenses(["notice"])

cc_library(
    name = "json",
    hdrs = ["single_include/nlohmann/json.hpp"],
    strip_include_prefix = "single_include",
    visibility = ["//visibility:public"],
)
""",
)

http_archive(
    name = "foxglove_ws-protocol",
    sha256 = "4fcbf939cbc0e557381dd8cfa2b38ef37148080d5ab6b640a5c0e124965df707",
    strip_prefix = "ws-protocol-42253ecad25729cd56f0f449bc56b67ec3f65bb6",
    urls = ["https://github.com/foxglove/ws-protocol/archive/42253ecad25729cd56f0f449bc56b67ec3f65bb6.tar.gz"],
    build_file_content = """
cc_library(
    name = "ws-protocol",
    hdrs = ["cpp/foxglove-websocket/include/foxglove/websocket/server.hpp"],
    deps = [
        "@zaphoyd_websocketpp//:websocketpp",
    ],
    visibility = ["//visibility:public"],
    strip_include_prefix = "cpp/foxglove-websocket/include",
)
cc_binary(
    name = "example_server",
    srcs = ["cpp/examples/example_server.cpp"],
    deps  = [":ws-protocol", "@nlohman_json//:json"],
    copts = ["-std=c++17"],
    defines = ["ASIO_STANDALONE"],
    linkopts = ["-lpthread"],
)
"""
)

http_archive(
    name = "zaphoyd_websocketpp",
    sha256 = "6ce889d85ecdc2d8fa07408d6787e7352510750daa66b5ad44aacb47bea76755",
    strip_prefix = "websocketpp-0.8.2",
    urls = ["https://github.com/zaphoyd/websocketpp/archive/refs/tags/0.8.2.tar.gz"],
    build_file_content = """
cc_library(
    name = "websocketpp",
    hdrs = glob(["websocketpp/**/*.hpp"]),  #+ ["websocketpp/config/asio_no_tls.hpp"],
    includes = [
        ".",
    ],
    copts = ["-DASIO_STANDALONE"],
    defines = ["ASIO_STANDALONE"],
    linkopts = ["-lpthread"],
    visibility = ["//visibility:public"],
    deps = [
        "@com_github_chriskohlhoff_asio//:asio",
    ],
)
"""
)

http_archive(
    name = "com_github_chriskohlhoff_asio",
    sha256 = "",
    build_file_content = """
cc_library(
    name = "asio",
    hdrs = glob(["asio/include/**/*.h*"] + ["asio/include/**/*.i*"]),
    defines = ["ASIO_STANDALONE"],
    includes = ["asio/include"],
    visibility = ["//visibility:public"],
)
""",
    strip_prefix = "asio-6c054e98f3f53352d12b6cd46d63b6d404cc044b",
    urls = ["https://github.com/chriskohlhoff/asio/archive/6c054e98f3f53352d12b6cd46d63b6d404cc044b.tar.gz"],
)
