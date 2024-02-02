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

# ==== 파일 조사, 타겟 생성 ====
add_subdirectory(include)
add_subdirectory(lib)
add_subdirectory(src)

# ==== 운영체제 관련 설정 ====
if(APPLE)
    # Xcode : Working Directory 설정
    set_target_properties(
        my_program PROPERTIES
        XCODE_GENERATE_SCHEME TRUE
        XCODE_SCHEME_WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/src_io/
    )
elseif(WIN32)
    # MSVC : Working Directory 설정
    set_target_properties(
        my_program PROPERTIES
        VS_DEBUGGER_WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/src_io/
    )
endif()

# ==== 프로젝트 설치 ====
# ...나중에 작성 예정