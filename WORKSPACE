workspace(name = "io_bazel")

# Protobuf expects an //external:python_headers label which would contain the
# Python headers if fast Python protos is enabled. Since we are not using fast
# Python protos, bind python_headers to a dummy target.
bind(
    name = "python_headers",
    actual = "//:dummy",
)

# Bind to dummy targets if no android SDK/NDK is present.
bind(
    name = "android_sdk_for_testing",
    actual = "//:dummy",
)

bind(
    name = "android_ndk_for_testing",
    actual = "//:dummy",
)

# Protobuf code generation for GRPC requires three external labels:
# //external:grpc-java_plugin
# //external:grpc-jar
# //external:guava
bind(
    name = "grpc-java-plugin",
    actual = "//third_party/grpc:grpc-java-plugin",
)

bind(
    name = "grpc-jar",
    actual = "//third_party/grpc:grpc-jar",
)

bind(
    name = "guava",
    actual = "//third_party:guava",
)

# For tools/cpp/test/...
load("//tools/cpp/test:docker_repository.bzl", "docker_repository")
docker_repository()

# In order to run the Android integration tests, run
# scripts/workspace_user.sh and uncomment the next two lines.
# load("/WORKSPACE.user", "android_repositories")
# android_repositories()

# In order to run //src/test/shell/bazel:maven_skylark_test, follow the
# instructions above for the Android integration tests and uncomment the
# following lines:
# load("//tools/build_defs/repo:maven_rules.bzl", "maven_dependency_plugin")
# maven_dependency_plugin()

# This allows rules written in skylark to locate apple build tools.
bind(name = "xcrunwrapper", actual = "@bazel_tools//tools/objc:xcrunwrapper")

new_local_repository(
    name = "com_google_protobuf",
    path = "./third_party/protobuf/3.0.0/",
    build_file = "./third_party/protobuf/3.0.0/BUILD",
)

new_local_repository(
    name = "com_google_protobuf_java",
    path = "./third_party/protobuf/3.0.0/",
    build_file = "./third_party/protobuf/3.0.0/com_google_protobuf_java.BUILD",
)

# OpenJDK distributions used to create a version of Bazel bundled with the OpenJDK.
http_file(
    name = "openjdk_linux",
    url = "https://bazel-mirror.storage.googleapis.com/openjdk/azul-zulu-8.20.0.5-jdk8.0.121/zulu8.20.0.5-jdk8.0.121-linux_x64.tar.gz",
    sha256 = "7fdfb17d890406470b2303d749d3138e7f353749e67a0a22f542e1ab3e482745",
)

http_file(
    name = "openjdk_macos",
    url = "https://bazel-mirror.storage.googleapis.com/openjdk/azul-zulu-8.20.0.5-jdk8.0.121/zulu8.20.0.5-jdk8.0.121-macosx_x64.zip",
    sha256 = "2a58bd1d9b0cbf0b3d8d1bcdd117c407e3d5a0ec01e2f53565c9bec5cf9ea78b",
)

http_file(
    name = "openjdk_win",
    url = "https://bazel-mirror.storage.googleapis.com/openjdk/azul-zulu-8.20.0.5-jdk8.0.121/zulu8.20.0.5-jdk8.0.121-win_x64.zip",
    sha256 = "35414df28f17704546b9559b5e62b4d00cdc8fdfd349116be4f987abaeaaff68",
)
