# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

COPTS = [
    "-D__STDC_FORMAT_MACROS",
    "-DBTHREAD_USE_FAST_PTHREAD_MUTEX",
    "-D__const__=__unused__",
    "-D_GNU_SOURCE",
    "-DUSE_SYMBOLIZE",
    "-DNO_TCMALLOC",
    "-D__STDC_LIMIT_MACROS",
    "-D__STDC_CONSTANT_MACROS",
    "-fPIC",
    "-Wno-unused-parameter",
    "-fno-omit-frame-pointer",
    "-DGFLAGS_NS=google",
] + select({
    "//:with_glog": ["-DBRPC_WITH_GLOG=1"],
    "//conditions:default": ["-DBRPC_WITH_GLOG=0"],
})

proto_library(
    name = "echo_c++_proto",
    srcs = [
        "echo_c++/echo.proto",
    ],
)

cc_proto_library(
    name = "cc_echo_c++_proto",
    deps = [
        ":echo_c++_proto",
    ],
)

cc_binary(
    name = "echo_c++_server",
    srcs = [
        "echo_c++/server.cpp",
    ],
    includes = [
        "echo_c++",
    ],
    deps = [
        ":cc_echo_c++_proto",
        "//:brpc",
    ],
    copts = COPTS,
)

cc_binary(
    name = "echo_c++_client",
    srcs = [
        "echo_c++/client.cpp",
    ],
    includes = [
        "echo_c++",
    ],
    deps = [
        ":cc_echo_c++_proto",
        "//:brpc",
    ],
    copts = COPTS,
)
