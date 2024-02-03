# 디렉토리에 있는 *.cpp 파일을 LIB_LIST 변수에 추가한다
file(
    GLOB_RECURSE LIB_LIST CONFIGURE_DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
)
file(
    GLOB_RECURSE INCLUDE_LIST CONFIGURE_DEPENDS
    ${CMAKE_SOURCE_DIR}/include/*.hpp
)

# my_library
add_library(my_library ${LIB_LIST} ${INCLUDE_LIST})

# my_library 의 include 디렉토리
target_include_directories(my_library PRIVATE ${CMAKE_SOURCE_DIR}/include)