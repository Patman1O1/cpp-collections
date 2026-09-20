# ── Google Test ──────────────────────────────────────────────────────────────
include(GoogleTest)
enable_testing()

# ───────────────────────────────────────────────────────────────────────────── 
# Target: cpp_collections_test
# Alias: cpp_collections::cpp_collections_test
# Type: Executable
# Dependencies: GTest::gtest_main,
#               GTest::gmock_main,
#               cpp_collections::cpp_collections_headers
# ─────────────────────────────────────────────────────────────────────────────
# Target definition
add_executable(cpp_collections_test)

# Target alias
add_executable(cpp_collections::cpp_collections_test
    ALIAS cpp_collections_test
)

# Target sources
target_sources(cpp_collections_test
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/cpp_collections_test.cpp
)

# Target dependencies
target_link_libraries(cpp_collections_test
    PRIVATE
        cpp_collections::cpp_collections_headers
        GTest::gtest_main
        GTest::gmock_main
)

# Test discovery
gtest_discover_tests(cpp_collections_test)
