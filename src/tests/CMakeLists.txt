project(dimension-tests
    VERSION 0.0
    LANGUAGES CXX
)

add_executable(dimension-tests
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
)

add_executable(dime::dimension-tests
    ALIAS
        dimension-tests
)

target_link_libraries(dimension-tests
    INTERFACE
        dime::compile-options-private
    PRIVATE
        dime::ext_google_test
)
