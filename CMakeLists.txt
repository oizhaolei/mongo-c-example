# Copyright 2017 MongoDB Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Demonstrates how to use the CMake 'find_package' mechanism to locate
# and build against libmongoc.

cmake_minimum_required (VERSION 2.8)

if (APPLE)
   cmake_policy (SET CMP0042 OLD)
endif ()

project (hello_mongoc LANGUAGES C)

# NOTE: For this to work, the CMAKE_PREFIX_PATH variable must be set to point to
# the directory that was used as the argument to CMAKE_INSTALL_PREFIX when
# building libmongoc.
# -- sphinx-include-start --
# Specify the minimum version you require.
find_package (libmongoc-1.0 1.7 REQUIRED)

message ("--   mongoc found version \"${MONGOC_VERSION}\"")
message ("--   mongoc include path \"${MONGOC_INCLUDE_DIRS}\"")
message ("--   mongoc libraries \"${MONGOC_LIBRARIES}\"")

# The "hello_mongoc.c" sample program is shared among four tests.
add_executable (hello_mongoc ./hello_mongoc.c)
target_include_directories (hello_mongoc PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (hello_mongoc PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (hello_mongoc PRIVATE "${MONGOC_DEFINITIONS}")

# The "json2bson.c" sample program is shared among four tests.
add_executable (json2bson ./json2bson.c)
target_include_directories (json2bson PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (json2bson PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (json2bson PRIVATE "${MONGOC_DEFINITIONS}")

# The "insertdoc.c" sample program is shared among four tests.
add_executable (insertdoc ./insertdoc.c)
target_include_directories (insertdoc PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (insertdoc PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (insertdoc PRIVATE "${MONGOC_DEFINITIONS}")


# The "finddoc.c" sample program is shared among four tests.
add_executable (finddoc ./finddoc.c)
target_include_directories (finddoc PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (finddoc PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (finddoc PRIVATE "${MONGOC_DEFINITIONS}")

# The "querydoc.c" sample program is shared among four tests.
add_executable (querydoc ./querydoc.c)
target_include_directories (querydoc PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (querydoc PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (querydoc PRIVATE "${MONGOC_DEFINITIONS}")

# The "updatedoc.c" sample program is shared among four tests.
add_executable (updatedoc ./updatedoc.c)
target_include_directories (updatedoc PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (updatedoc PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (updatedoc PRIVATE "${MONGOC_DEFINITIONS}")

# The "deletedoc.c" sample program is shared among four tests.
add_executable (deletedoc ./deletedoc.c)
target_include_directories (deletedoc PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (deletedoc PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (deletedoc PRIVATE "${MONGOC_DEFINITIONS}")

# The "countdoc.c" sample program is shared among four tests.
add_executable (countdoc ./countdoc.c)
target_include_directories (countdoc PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (countdoc PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (countdoc PRIVATE "${MONGOC_DEFINITIONS}")

# The "executecmd.c" sample program is shared among four tests.
add_executable (executecmd ./executecmd.c)
target_include_directories (executecmd PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (executecmd PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (executecmd PRIVATE "${MONGOC_DEFINITIONS}")

# The "threading.c" sample program is shared among four tests.
add_executable (threading ./threading.c)
target_include_directories (threading PRIVATE "${MONGOC_INCLUDE_DIRS}")
target_link_libraries (threading PRIVATE "${MONGOC_LIBRARIES}")
target_compile_definitions (threading PRIVATE "${MONGOC_DEFINITIONS}")

