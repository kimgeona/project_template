# 디렉토리에 있는 *.cpp 파일을 SRC_LIST 변수에 추가한다
file(
    GLOB_RECURSE SRC_LIST CONFIGURE_DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
)

# my_program
add_executable(my_program ${SRC_LIST})

# my_program 의 include 디렉토리
target_include_directories(my_program PRIVATE ${CMAKE_SOURCE_DIR}/include)

# my_program 의 의존성 라이브러리
target_link_libraries(my_program PRIVATE my_library)