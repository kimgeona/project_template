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

# ==== include 디렉토리 설정 ====
include_directories(
    ./include
)

# ==== 파일 조사, 타겟 생성 ====
add_subdirectory(include)
add_subdirectory(lib)
add_subdirectory(src)

# ==== 운영체제 관련 설정 ====
if(APPLE)
    # Xcode : Apple Framework 만들기
    #set_target_properties(
    #    my_library PROPERTIES
    #    FRAMEWORK TRUE
    #    FRAMEWORK_VERSION ${CMAKE_PROJECT_VERSION} # 프로젝트 버전과 동일하게 가려고 함.
    #    MACOSX_FRAMEWORK_IDENTIFIER org.cmake.my_library
    #)
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
    # 컴파일 문자 포멧 : utf-8 지정
    #target_compile_options(my_library PRIVATE "/utf-8")
    #target_compile_options(my_program PRIVATE "/utf-8")
endif()

# ==== 프로젝트 설치 ====
# ...나중에 작성 예정

# ==== 변수 출력 ====
# include(CMakePrintHelpers)
# cmake_print_variables(CMAKE_PROJECT_VERSION)
# cmake_print_variables(INCLUDE_LIST)
# cmake_print_variables(LIB_LIST)
# cmake_print_variables(SRC_LIST)