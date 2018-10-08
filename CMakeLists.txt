cmake_minimum_required(VERSION 2.8.3)

project(nclt_utilities)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(Boost REQUIRED COMPONENTS program_options)

find_package(catkin REQUIRED COMPONENTS sensor_msgs rosbag roscpp std_msgs)

catkin_package()

include_directories(include external/monads-cxx/include ${catkin_INCLUDE_DIRS}
							${Boost_INCLUDE_DIRS})

add_executable(transform_rosbag src/transform_rosbag.cpp)
target_link_libraries(transform_rosbag ${catkin_LIBRARIES} ${Boost_LIBRARIES})

catkin_install_python(PROGRAMS scripts/sensordata_to_rosbag.py
					  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

install(TARGETS transform_rosbag
        ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
        LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
        RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
