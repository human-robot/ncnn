
#find_package(OpenCV REQUIRED core highgui imgproc imgcodecs)
find_package(OpenCV REQUIRED core highgui imgproc )
if(NOT OpenCV_FOUND)
    find_package(OpenCV REQUIRED core highgui imgproc)
endif()

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../src)
include_directories(${CMAKE_CURRENT_BINARY_DIR}/../src)

add_executable(squeezenet squeezenet.cpp)
target_link_libraries(squeezenet ncnn ${OpenCV_LIBS})

add_executable(fasterrcnn fasterrcnn.cpp)
target_link_libraries(fasterrcnn ncnn ${OpenCV_LIBS})

add_subdirectory(ssd)
