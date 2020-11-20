cmake_minimum_required(VERSION 3.5)


SET( TOOLS_DIR "/home/dsr/lib/android-ndk-r21d/toolchains/llvm/prebuilt/linux-x86_64/bin")
SET(CMAKE_C_COMPILER     ${TOOLS_DIR}/armv7a-linux-androideabi21-clang)
SET(CMAKE_CXX_COMPILER   ${TOOLS_DIR}/armv7a-linux-androideabi21-clang++)
SET(CMAKE_AR   ${TOOLS_DIR}/arm-linux-androideabi-ar)

project( GL )

SET(CMAKE_INSTALL_PREFIX "/home/dsr/lib/android-sysroot/usr")
SET(CMAKE_INSTALL_LIBDIR "lib/arm-linux-androideabi")

include(GNUInstallDirs)
add_library(GL SHARED src/gl.c)
set_target_properties(GL PROPERTIES
    SOVERSION 1
    PUBLIC_HEADER include/gl.h)
target_include_directories(GL PRIVATE .)
install(TARGETS GL
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
 
