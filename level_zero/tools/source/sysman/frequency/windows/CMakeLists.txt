#
# Copyright (C) 2019-2020 Intel Corporation
#
# SPDX-License-Identifier: MIT
#

set(L0_SRCS_TOOLS_SYSMAN_FREQUENCY_WINDOWS
    ${CMAKE_CURRENT_SOURCE_DIR}/os_frequency_imp.cpp
)

if(WIN32)
target_sources(${TARGET_NAME_L0}
    PRIVATE
    ${L0_SRCS_TOOLS_SYSMAN_FREQUENCY_WINDOWS}
)
endif()

# Make our source files visible to parent
set_property(GLOBAL PROPERTY L0_SRCS_TOOLS_SYSMAN_FREQUENCY_WINDOWS ${L0_SRCS_TOOLS_SYSMAN_FREQUENCY_WINDOWS})
