project(dimension-benchmarks
    VERSION 0.0
    LANGUAGES CXX
)

add_executable(dimension-benchmarks
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
)

add_executable(dime::dimension-benchmarks
    ALIAS
        dimension-benchmarks
)

target_link_libraries(dimension-benchmarks
    INTERFACE
        dime::compile-options-private
)

if (MSVC)
    target_link_libraries(dimension-benchmarks
        PRIVATE
            dime::ext_google_benchmark $<$<CONFIG:Release>:-LTCG>
    )
else()
    target_link_libraries(dimension-benchmarks
        PRIVATE
            dime::ext_google_benchmark
    )
endif()
