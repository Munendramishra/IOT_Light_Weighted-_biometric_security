CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(LSHBOX)

IF(WIN32)
    IF(CMAKE_CL_64)
        IF(${CMAKE_BUILD_TYPE} MATCHES "Debug")
            SET(SAVE_CLASS x64/Debug)
        ELSE()
            SET(SAVE_CLASS x64/Release)
        ENDIF()
    ELSE()
        IF(${CMAKE_BUILD_TYPE} MATCHES "Debug")
            SET(SAVE_CLASS x86/Debug)
        ELSE()
            SET(SAVE_CLASS x86/Release)
        ENDIF()
    ENDIF()
ELSEIF(LINUX)
    SET(SAVE_CLASS linux)
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
ELSE()
    SET(SAVE_CLASS darwin)
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
ENDIF()

INCLUDE_DIRECTORIES(
    ${LSHBOX_SOURCE_DIR}/include
)

ADD_SUBDIRECTORY(tools)
# ADD_SUBDIRECTORY(python)
# ADD_SUBDIRECTORY(matlab)