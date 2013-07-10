cmake_minimum_required(VERSION 2.8.3)
project(hubo_ach_ros)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS interactive_markers moveit_core moveit_ros_perception moveit_ros_planning_interface pluginlib roscpp rospy std_msgs sensor_msgs)

find_package(Eigen REQUIRED)
find_package(Boost REQUIRED system filesystem date_time thread)



catkin_package(
   INCLUDE_DIRS include
   CATKIN_DEPENDS 
     interactive_markers
     moveit_core 
     moveit_ros_perception 
     moveit_ros_planning_interface 
     pluginlib 
     roscpp rospy 
     std_msgs
     sensor_msgs
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations

include_directories(SYSTEM ${Boost_INCLUDE_DIR} ${EIGEN_INCLUDE_DIRS})
include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})


## Declare a cpp executable
add_executable(hubo_ach_ros src/hubo_ach_ros.cpp)
add_executable(hubo_float src/hubo_float.cpp)
target_link_libraries(hubo_ach_ros ach ${catkin_LIBRARIES} ${Boost_LIBRARIES})
target_link_libraries(hubo_float ${catkin_LIBRARIES} ${Boost_LIBRARIES})
install(TARGETS hubo_ach_ros DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION})

 

