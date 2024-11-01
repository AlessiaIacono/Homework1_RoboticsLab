cmake_minimum_required(VERSION 3.8)
project(arm_control)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

add_executable(arm_controller src/pub_sub.cpp)

ament_target_dependencies(arm_controller  rclcpp std_msgs sensor_msgs)

install (
  DIRECTORY config launch  
  DESTINATION share/${PROJECT_NAME}
)

install(
  TARGETS arm_controller
  DESTINATION lib/${PROJECT_NAME}
)
ament_package()
