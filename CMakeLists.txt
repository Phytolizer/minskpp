cmake_minimum_required(VERSION 3.16...3.23)

project(
    "minskpp"
    LANGUAGES CXX
    VERSION "0.1.0"
    DESCRIPTION "Minsk in modern C++"
    HOMEPAGE_URL "https://github.com/Phytolizer/minskpp"
)

set(CMAKE_CXX_STANDARD 20)

include(FetchContent)
FetchContent_Declare(
    fmt
    GIT_REPOSITORY "https://github.com/fmtlib/fmt.git"
    GIT_TAG "8.1.1"
)
FetchContent_MakeAvailable(fmt)

set(MC_SRC "program.cpp")
list(TRANSFORM MC_SRC PREPEND "source/mc/")
add_executable(mc ${MC_SRC})
target_include_directories(mc PRIVATE include)
target_link_libraries(mc PRIVATE fmt::fmt)
