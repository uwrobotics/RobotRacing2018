cmake_minimum_required(VERSION 2.8.3)
project(rr_traffic_light)

set(CMAKE_BUILD_TYPE Release)

find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  image_transport
  message_filters
  pluginlib
  rosconsole
  roscpp
  roslib
  sensor_msgs
  roslint
  darknet_ros_msgs
  std_srvs
)

find_package(OpenCV REQUIRED)

catkin_package()

include_directories(include ${catkin_INCLUDE_DIRS})
add_executable(rr_traffic_light src/rr_traffic_light.cpp src/main.cpp)
target_link_libraries(rr_traffic_light ${catkin_LIBRARIES} ${OpenCV_LIBS})
roslint_cpp(src/main.cpp src/rr_traffic_light.cpp include/rr_traffic_light.h)