#
# Copyright (C) 2019-2020 Intel Corporation
#
# SPDX-License-Identifier: MIT
#

set(L0_SRCS_TOOLS_METRICS
)

if(HAVE_INSTRUMENTATION)
    list(APPEND L0_SRCS_TOOLS_METRICS
        ${L0_SRCS_TOOLS_LINUX}
        ${L0_SRCS_TOOLS_WINDOWS}
        ${CMAKE_CURRENT_SOURCE_DIR}/metric.cpp
        ${CMAKE_CURRENT_SOURCE_DIR}/metric_enumeration_imp.cpp
        ${CMAKE_CURRENT_SOURCE_DIR}/metric_tracer_imp.cpp
        ${CMAKE_CURRENT_SOURCE_DIR}/metric_query_imp.cpp)
else()
    list(APPEND L0_SRCS_TOOLS_METRICS
        ${CMAKE_CURRENT_SOURCE_DIR}/metric_stubs.cpp)
endif()

if(UNIX)
    add_subdirectory(linux)
else()
    add_subdirectory(windows)
endif()

target_include_directories(${TARGET_NAME_L0}
    PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/
)

target_sources(${TARGET_NAME_L0}
    PRIVATE
        ${L0_SRCS_TOOLS_METRICS}
        ${CMAKE_CURRENT_SOURCE_DIR}/CMakeLists.txt
)

# Make our source files visible to parent
set_property(GLOBAL PROPERTY L0_SRCS_TOOLS_METRICS ${L0_SRCS_TOOLS_METRICS})
