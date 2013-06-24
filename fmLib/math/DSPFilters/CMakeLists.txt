cmake_minimum_required(VERSION 2.8.3)
project(DSPFilters)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)

## System dependencies are found with CMake's conventions
# find_package(Boost REQUIRED COMPONENTS system)


## Uncomment this if the package has a setup.py. This macro ensures
## modules and global scripts declared therein get installed
## See http://ros.org/doc/groovy/api/catkin/html/user_guide/setup_dot_py.html
# catkin_python_setup()

#######################################
## Declare ROS messages and services ##
#######################################

## Generate messages in the 'msg' folder
# add_message_files(
#   FILES
#   Message1.msg
#   Message2.msg
# )

## Generate services in the 'srv' folder
# add_service_files(
#   FILES
#   Service1.srv
#   Service2.srv
# )

## Generate added messages and services with any dependencies listed here
# generate_messages(
#   DEPENDENCIES
#   std_msgs  # Or other packages containing msgs
# )

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
  INCLUDE_DIRS src/DSPFilters/shared/DSPFilters/include
  LIBRARIES DSPFilters
#  CATKIN_DEPENDS other_catkin_pkg
#  DEPENDS system_lib
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(include ${catkin_INCLUDE_DIRS} src/DSPFilters/shared/DSPFilters/include)

## Declare a cpp library
 add_library(DSPFilters
   src/${PROJECT_NAME}/shared/DSPFilters/source/Bessel.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Biquad.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Butterworth.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Cascade.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/ChebyshevI.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/ChebyshevII.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Custom.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Design.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Documentation.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Elliptic.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Filter.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Legendre.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/Param.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/PoleFilter.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/RBJ.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/RootFinder.cpp
   src/${PROJECT_NAME}/shared/DSPFilters/source/State.cpp
 )

## Declare a cpp executable
 add_executable(DSPFilters_node src/filter_test_node.cpp)

## Add cmake target dependencies of the executable/library
## as an example, message headers may need to be generated before nodes
# add_dependencies(DSPFilters_node DSPFilters_generate_messages_cpp)

## Specify libraries to link a library or executable target against
 target_link_libraries(DSPFilters_node
   ${catkin_LIBRARIES} DSPFilters
 )

#############
## Install ##
#############

# all install targets should use catkin DESTINATION variables
# See http://ros.org/doc/groovy/api/catkin/html/adv_user_guide/variables.html

## Mark executable scripts (Python etc.) for installation
## in contrast to setup.py, you can choose the destination
# install(PROGRAMS
#   scripts/my_python_script
#   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

## Mark executables and/or libraries for installation
 install(TARGETS DSPFilters 
   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
 )

## Mark cpp header files for installation
 install(DIRECTORY src/DSPFilters/shared/DSPFilters/include/
   DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
   FILES_MATCHING PATTERN "*/*.h"
   PATTERN ".svn" EXCLUDE
 )

## Mark other files for installation (e.g. launch and bag files, etc.)
# install(FILES
#   # myfile1
#   # myfile2
#   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
# )

#############
## Testing ##
#############

## Add gtest based cpp test target and link libraries
# catkin_add_gtest(${PROJECT_NAME}-test test/test_DSPFilters.cpp)
# if(TARGET ${PROJECT_NAME}-test)
#   target_link_libraries(${PROJECT_NAME}-test ${PROJECT_NAME})
# endif()

## Add folders to be run by python nosetests
# catkin_add_nosetests(test)
