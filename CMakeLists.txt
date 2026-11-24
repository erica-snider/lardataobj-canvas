# ======================================================================
#  lardataobj-canvas main build file
#
#  cd .../path/to/build/directory
#  source .../path/to/lardataobj-canvas/ups/setup_for_development <-d|-p>
#  buildtool [-I /install/path] -bt[i] -jN
# ======================================================================

cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

find_package(cetmodules 3.24.00 REQUIRED)
project(lardataobj-canvas VERSION 10.00.00 LANGUAGES CXX)

include(CetCMakeEnv)
cet_cmake_env()

cet_set_compiler_flags(DIAGS CAUTIOUS
  WERROR
  NO_UNDEFINED
  EXTRA_FLAGS -pedantic -Wno-unused-local-typedefs
)

cet_report_compiler_flags(REPORT_THRESHOLD VERBOSE)

find_package(canvas REQUIRED EXPORT)

# source
add_subdirectory(lardataobj-canvas)

# tests
add_subdirectory(test)

# packaging utility
cet_cmake_config()
