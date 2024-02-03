# project_template
C/C++ 기반 다양한 프로젝트에서 사용하기위한 cmake 프로젝트 템플릿입니다.

>운영체제(IDE) : MacOS(Xcode), Windows(VisualStudio2022)

## 프로젝트 구조
해당 프로젝트의 구조는 다음과 같습니다.

    (base) chorokmoo@kimgeonaui-MacBookPro project_template % tree    
    .
    ├── CMakeLists.txt
    ├── LICENSE
    ├── README.md
    ├── include
    │   ├── CMakeLists.txt
    │   └── hello.hpp
    ├── lib
    │   ├── CMakeLists.txt
    │   └── hello.cpp
    ├── src
    │   ├── CMakeLists.txt
    │   └── main.cpp
    └── src_io
        └── theory.txt

    5 directories, 10 files

## 구조 설명
루트 디렉토리 project_template 에는 CMakeLists.txt와 각각의 소스들을 저장하는 include, lib, src, src_io 폴더들이 있습니다. 각 폴더의 역할은 다음과 같습니다.

>include : include 파일들(.hpp)을 보관합니다.   
>lib : 라이브러리 파일들(.cpp)을 보관합니다.   
>src : 현재 작성하는 소스파일들(.cpp)을 보관합니다.   
>src_io : src 소스로부터 컴파일된 실행파일의 입출력(파일 쓰기, 읽기)이 이루어지는 공간입니다.

## CMakeLists.txt
project_template에 작성된 CMakeLists.txt는 위에 명시된 구조를 이용하여 IDE 프로젝트를 생성하고 사용할 수 있도록 기술된 파일입니다. CMakeLists.txt에는 폴더 내에 있는 소스파일들을 조사하고 위에 명시된 구조대로 프로젝트를 진행할 수 있게끔 Xcode와 VisualStudio 설정이 되어 있습니다.

## 프로젝트 생성방법
project_template을 이용하여 자신의 운영체제에 설치된 IDE 프로젝트를 생성하시려면 다음과 같이 터미널에 입력하시면 됩니다.

    $ cmake -S<project_template 주소> -B<생성할 프로젝트 주소> -G<IDE 종류>
    $ cmake -S./project_template -B./project_template_project -GXcode

-G 에는 자신이 사용할 IDE의 종류를 입력해주시면 됩니다. (-A옵션은 사용할 아키텍처입니다. Xcode의 경우 지정x)

    -G Xcode
    -G "Visual Studio 17 2022" -A x64

CLI 로 CMake로 프로젝트 생성 옵션에 관해서는 다음 링크를 참조하시길 바랍니다. https://cmake.org/cmake/help/latest/manual/cmake.1.html#options

