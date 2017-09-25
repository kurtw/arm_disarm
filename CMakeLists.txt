cmake_minimum_required(VERSION 2.8.3)
project(arm_disarm)

# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS
  roscpp
  mavros_msgs
)

include_directories(include ${catkin_INCLUDE_DIRS})

#
###################################
## catkin specific configuration ##
###################################

catkin_package(
  CATKIN_DEPENDS
    roscpp
    mavros_msgs
)


###########
## Build ##
###########

add_executable(arm
  src/arm.cpp
)

target_link_libraries(arm ${catkin_LIBRARIES})
add_dependencies(arm arm)


add_executable(disarm
  src/disarm.cpp
)

target_link_libraries(disarm ${catkin_LIBRARIES})
add_dependencies(disarm disarm)

install(TARGETS arm disarm 
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
