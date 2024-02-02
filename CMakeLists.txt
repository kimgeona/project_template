# ==== cmake 설정 ====
cmake_minimum_required(VERSION 3.28)
project(
    My_Project
    VERSION 0.0
    DESCRIPTION "my little cpp project template"
    LANGUAGES CXX
)

# ==== 패키지 ====
# find_package(OpenCV)
# OpenCV include : ${OpenCV_INCLUDE_DIRS}
# OpenCV Library : ${OpenCV_LIBS}

# ==== 파일들 조사 ====
add_subdirectory(lib) # 해당 디렉토리 CMakeLists.txt 실행
add_subdirectory(src)

# ==== 타겟 관련 ====
include_directories(./include)

# my_library
add_library(my_library ${LIB_LIST})
# my_program
add_executable(my_program ${SRC_LIST})
target_link_libraries(my_program PUBLIC my_library)

# ==== 운영체제 관련 설정 ====
if(APPLE)
    # 타겟 Xcode : Working Directory 설정
    set_target_properties(
        my_program PROPERTIES
        XCODE_GENERATE_SCHEME TRUE
        XCODE_SCHEME_WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/src_io/
    )
elseif(WIN32)
    # 타겟 VS : Working Directory 설정
    set_target_properties(
        my_program PROPERTIES
        VS_DEBUGGER_WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/src_io/
    )
endif()