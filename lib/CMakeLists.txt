# 디렉토리에 있는 *.cpp 파일을 SRC_LIST 변수에 추가한다
file(
    GLOB_RECURSE SRC_LIST CONFIGURE_DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
)