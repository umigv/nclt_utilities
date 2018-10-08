cmake_minimum_required(VERSION 2.8.3)

project(nclt_utilities)

find_package(PythonInterp 2 REQUIRED)

find_package(catkin REQUIRED)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS})

catkin_install_python(PROGRAMS scripts/sensordata_to_rosbag.py
					  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
