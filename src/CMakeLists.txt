

file(GLOB_RECURSE CppLinuxSerial_SRC
        "*.cpp")

file(GLOB_RECURSE CppLinuxSerial_HEADERS
        "${CMAKE_SOURCE_DIR}/include/*.hpp")
option(SERIAL_BUILD_SHARED_LIBS "Build CppLinuxSerial shared library" OFF)

if (SERIAL_BUILD_SHARED_LIBS)
  set(LibType SHARED)
else()
  set(LibType STATIC)
endif()

add_library(CppLinuxSerial ${LibType} ${CppLinuxSerial_SRC} ${CppLinuxSerial_HEADERS})
set_property(TARGET CppLinuxSerial PROPERTY POSITION_INDEPENDENT_CODE ON)

target_include_directories(CppLinuxSerial PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/../include>"
                                                "$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}>")                                                  
