project(dimension-compile-options-public
    VERSION 0.0
    LANGUAGES CXX
)

add_library(dimension-compile-options-public
    INTERFACE
)

add_library(dime::compile-options-public
    ALIAS
        dimension-compile-options-public
)

if (MSVC)
    target_compile_options(dimension-compile-options-public
        INTERFACE
            /Oi         # Enable intrinsic functions
            /std:c++17  # Enable C++ 17 features
    )
elseif (UNIX)
    target_compile_options(dimension-compile-options-public
        INTERFACE
            -std=c++17
    )
endif()

install(
    TARGETS
        dimension-compile-options-public
    EXPORT
        CompileOptionsPublicTargets
)

install(
    EXPORT
        CompileOptionsPublicTargets
    FILE
        CompileOptionsPublicTargets.cmake
    NAMESPACE
        dime::
    DESTINATION
        lib/cmake/CompileOptionsPublicTargets
)
