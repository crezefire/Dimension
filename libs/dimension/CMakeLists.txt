project(dimension
    VERSION 0.0
    LANGUAGES CXX
)

add_library(dimension
    STATIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src/engine.cpp
)

add_library(dime::dimension
    ALIAS
        dimension
)

target_include_directories(dimension
    PUBLIC
        $<BUILD_INTERFACE:${dimension_BINARY_DIR}/include>
        $<BUILD_INTERFACE:${dimension_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
)

target_link_libraries(dimension
    PRIVATE
        dime::compile-options-private
    PUBLIC
        dime::compile-options-public
)

install(
    TARGETS
        dimension
    EXPORT
        DimensionTargets
    LIBRARY DESTINATION
        lib
    ARCHIVE DESTINATION
        lib
    RUNTIME DESTINATION
        bin
    INCLUDES DESTINATION
        include
    PUBLIC_HEADER DESTINATION
        include
)

install(
    DIRECTORY
        include/
    DESTINATION
        include
)

install(
    EXPORT
        DimensionTargets
    FILE
        DimensionTargets.cmake
    NAMESPACE
        dime::
    DESTINATION
        lib/cmake/dimension
)

include(CMakePackageConfigHelpers)

write_basic_package_version_file(
    "DimensionConfigVersion.cmake"
    VERSION
        ${dimension_VERSION}
    COMPATIBILITY
        SameMajorVersion
)

install(
    FILES
        "DimensionConfig.cmake"
        "${CMAKE_CURRENT_BINARY_DIR}/DimensionConfigVersion.cmake"
    DESTINATION
        lib/cmake/dimension
)

export(
    PACKAGE
        dimension
)
