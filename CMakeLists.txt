cmake_minimum_required(VERSION 3.6)
project(weather_backend_app)

set(CMAKE_CXX_STANDARD 11)
set(EXECUTABLE_OUTPUT_PATH bin)

include(conanbuildinfo.cmake)
conan_basic_setup()

#CORE FILES
set(CORE_FILES  src/components/processing-component/DataProcessingInterface.hpp
                src/components/processing-component/ProcessingComponent.hpp
                src/components/processing-component/ProcessingComponent.cpp src/shared/Shared.cpp src/shared/Shared.h)

#TEST FILES

set(TEST_FILES  tests/components/processing-component/ProcessingComponentTests.h
                tests/components/processing-component/ProcessingComponentTests.cpp
                tests/main-test.cpp)

add_executable(weather_processor_tests ${TEST_FILES} ${CORE_FILES})
target_link_libraries(weather_processor_tests ${CONAN_LIBS})

#SOURCE FILES
set(SOURCE_FILES src/main.cpp ${CORE_FILES})
add_executable(weather_processor ${SOURCE_FILES})