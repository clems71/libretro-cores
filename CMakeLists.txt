cmake_minimum_required(VERSION 3.2)
project(libretro-cores)

include(ExternalProject)

set(CORES_INSTALL_DIR ${CMAKE_BINARY_DIR}/cores)

ExternalProject_Add(
  gba
  GIT_REPOSITORY https://github.com/libretro/gpsp.git
  GIT_TAG 4b00c74784ad607fb62220ef27c79b12bc6d7678
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make platform=unix CC=${CMAKE_C_COMPILER} CXX=${CMAKE_CXX_COMPILER}
  BUILD_IN_SOURCE 1
  INSTALL_DIR ${CORES_INSTALL_DIR}
  INSTALL_COMMAND cp gpsp_libretro.so ${CORES_INSTALL_DIR}/
)

ExternalProject_Add(
  gb
  GIT_REPOSITORY https://github.com/libretro/gambatte-libretro.git
  GIT_TAG 9df855665f43c96944eff3085a082aad12be6723
  CONFIGURE_COMMAND ""
  BUILD_COMMAND cd libgambatte && make -f Makefile.libretro platform=unix CC=${CMAKE_C_COMPILER} CXX=${CMAKE_CXX_COMPILER}
  BUILD_IN_SOURCE 1
  INSTALL_DIR ${CORES_INSTALL_DIR}
  INSTALL_COMMAND cp libgambatte/gambatte_libretro.so ${CORES_INSTALL_DIR}/
)

ExternalProject_Add(
  genesis
  GIT_REPOSITORY https://github.com/libretro/picodrive.git
  GIT_TAG edddf9975128324c8aecf33560a5642f7f7195dc
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make -f Makefile.libretro platform=unix CC=${CMAKE_C_COMPILER} CXX=${CMAKE_CXX_COMPILER}
  BUILD_IN_SOURCE 1
  INSTALL_DIR ${CORES_INSTALL_DIR}
  INSTALL_COMMAND cp picodrive_libretro.so ${CORES_INSTALL_DIR}/
)

ExternalProject_Add(
  nes
  GIT_REPOSITORY https://github.com/libretro/libretro-fceumm.git
  GIT_TAG 417b8c60228d9e828d14c89dd0a4d5b9b94b3e6f
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make -f Makefile.libretro platform=unix CC=${CMAKE_C_COMPILER} CXX=${CMAKE_CXX_COMPILER}
  BUILD_IN_SOURCE 1
  INSTALL_DIR ${CORES_INSTALL_DIR}
  INSTALL_COMMAND cp fceumm_libretro.so ${CORES_INSTALL_DIR}/
)
