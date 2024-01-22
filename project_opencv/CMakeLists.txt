# Cmake 프로그램의 최소 버전
cmake_minimum_required(VERSION 3.28)

# 프로젝트 정보
project(
    OpenCV_Project
    VERSION 0.0
    DESCRIPTION "OpenCV Project with C/C++."
    LANGUAGES CXX
)

# 외부 패키지 사용 : OpenCV
find_package(OpenCV)

# include 설정
include_directories(./include)

# 소스 파일들
add_subdirectory(src)

# 운영체제 관련 설정
if(APPLE) # 타겟 Xcode : Working Directory 설정
set_target_properties(
    opencv_project PROPERTIES
    XCODE_GENERATE_SCHEME TRUE
    XCODE_SCHEME_WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/src_io/
)
elseif(WIN32) # 타겟 VS : Working Directory 설정
set_target_properties(
    opencv_project PROPERTIES
    VS_DEBUGGER_WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/src_io/
)
endif()
