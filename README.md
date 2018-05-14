# Dimension

A maths library for 3D graphics.

## Getting Started
- Run `get_latest_deps.sh` to pull down 3rd party dependencies from Github. Use `[-s|--ssh]` to use ssh.
- `mkdir build && cd build`
- `cmake -G "Your Favourite Build Type" ../` Supported options are (OFF by default): `-D<OPTION>=ON`
  - PROJECT_ENABLE_BENCHMARKING - Creates sample Google Benchmark project
  - PROJECT_ENABLE_TESTING - Creats sample Google Test project
  - PROJECT_USE_LIBCXX - Sets `-stdlib=libc++` for Clang only