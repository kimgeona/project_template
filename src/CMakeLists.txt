# 디렉토리에 있는 *.cpp 파일을 LIB_LIST 변수에 추가한다
file(
    GLOB_RECURSE LIB_LIST CONFIGURE_DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
)