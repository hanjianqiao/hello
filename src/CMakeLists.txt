SET(CMAKE_SYSROOT /)
SET(CMAKE_C_COMPILER gcc)
SET(CMAKE_CXX_COMPILER g++)

find_package(Intl)
find_package(Threads)

include_directories(${Intl_INCLUDE_DIRS})
link_directories()

add_executable(hello main.cc hello.cc voice.cc)

set(EXTRA_LIBS ${EXTRA_LIBS} SDL2 ${Intl_LIBRARIES} ${CMAKE_THREAD_LIBS_INIT})

target_link_libraries(hello ${EXTRA_LIBS})

add_definitions(-DLOCALPKG="hello" -DLOCALDIR="${CMAKE_SOURCE_DIR}/po")
add_definitions(-DAUDIODIR="${CMAKE_SOURCE_DIR}/media4hello/audio/")