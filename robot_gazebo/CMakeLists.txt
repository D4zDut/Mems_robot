cmake_minimum_required(VERSION 3.0.2)
project(robot_gazebo)

find_package(catkin REQUIRED)

catkin_package()

install(
  DIRECTORY worlds
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(
  FILES launch/robot_empty_world.launch
        launch/spawn_robot.launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
)

if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch/robot_empty_world.launch)
  roslaunch_add_file_check(launch/spawn_robot.launch)
endif()