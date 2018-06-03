if (DIMENSION_ENABLE_BENCHMARKING)
    add_subdirectory(benchmarks)
    set_property(TARGET dimension-benchmarks PROPERTY FOLDER "benchmarks")
endif()

if (DIMENSION_ENABLE_TESTING)
    add_subdirectory(tests)
    set_property(TARGET dimension-tests PROPERTY FOLDER "tests")
endif()
