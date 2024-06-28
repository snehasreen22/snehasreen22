cmake_minimum_required(VERSION 3.8)
project(viperx_controller)

# Find dependencies
# find_package(ament_cmake REQUIRED)
# find_package(rclcpp REQUIRED)
# find_package(moveit_core REQUIRED)


set(THIS_PACKAGE_INCLUDE_DEPENDS
  ament_cmake
  Boost
  Eigen3
  moveit_core
  moveit_msgs
  moveit_ros_planning
  moveit_ros_planning_interface
  moveit_visual_tools
  rclcpp
  rclcpp_action
  tf2_geometry_msgs
  tf2_geometry_msgs
  tf2_ros
)

foreach(Dependency IN ITEMS ${THIS_PACKAGE_INCLUDE_DEPENDS})
  find_package(${Dependency} REQUIRED)
endforeach()
# Include directories
include_directories(include)

# Add executables
add_executable(viperctrl src/main.cpp src/viperx_controller.cpp)
target_link_libraries (viperctrl Eigen3::Eigen)
# Link the executable with the required libraries
ament_target_dependencies(viperctrl rclcpp moveit_core Eigen3  ${THIS_PACKAGE_INCLUDE_DEPENDS})

# Install executables
install(TARGETS viperctrl
  DESTINATION lib/${PROJECT_NAME})

# Install include directory
install(DIRECTORY include/
  DESTINATION include/${PROJECT_NAME})

# Install launch files, config files, etc. if any

ament_package()


<!---
snehasreen22/snehasreen22 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
