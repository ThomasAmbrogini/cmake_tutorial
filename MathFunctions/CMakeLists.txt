# TODO 14: Remove mysqrt.cxx from the list of sources

add_library(MathFunctions MathFunctions.cpp)

option(USE_MYMATH "Use custom math library" FALSE)
set(USE_MYMATH TRUE)

if(USE_MYMATH)
    add_library(SqrtLibrary STATIC mysqrt.cpp)
    target_compile_definitions(MathFunctions PRIVATE "USE_MYMATH")
    target_link_libraries(MathFunctions PRIVATE SqrtLibrary)
endif()

