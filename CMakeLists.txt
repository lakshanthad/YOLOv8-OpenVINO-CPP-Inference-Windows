cmake_minimum_required(VERSION 3.12)
project(yolov8_openvino_example)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(OpenCV REQUIRED)

set(OPENVINO_DIR "[path_to_vcpkg]/packages/openvino_x64-windows")

include_directories(
	${OpenCV_INCLUDE_DIRS}
	${OPENVINO_DIR}/include
)

add_executable(detect 
	main.cc
	inference.cc
)

target_link_libraries(detect
	${OpenCV_LIBS}
	"${OPENVINO_DIR}/lib/openvino.lib"
)