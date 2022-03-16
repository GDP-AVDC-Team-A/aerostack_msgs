cmake_minimum_required(VERSION 2.8.3)

set(PROJECT_NAME aerostack_msgs)
project(${PROJECT_NAME})

### Use version 2011 of C++ (c++11). By default ROS uses c++98
add_definitions(-std=c++11)


# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)



set(AEROSTACK_MSGS_SOURCE_DIR
  src/sources
)

set(AEROSTACK_MSGS_INCUDE_DIR
  src/include
)

set(AEROSTACK_MSGS_SOURCE_FILES

)

set(AEROSTACK_MSGS_HEADER_FILES
)

find_package(catkin REQUIRED
  COMPONENTS
  message_generation
  std_msgs sensor_msgs
  geometry_msgs
  std_srvs
  opencv_apps
	shape_msgs
)

add_message_files(
    DIRECTORY msg
    FILES
    # Executive Layer
    ListOfBeliefs.msg
    Float32Stamped.msg
    PathWithID.msg
    FlightActionCommand.msg
    FlightState.msg
    FloatStamped.msg
    SharedRobotPosition.msg
    SocialCommunicationStatement.msg
    BehaviorActivationFinished.msg
    MotionControlMode.msg
    BehaviorCommandPriority.msg
    StringStamped.msg
    DynamicObstacle.msg
    DynamicObstacles.msg
    TaskCommand.msg
    TaskStopped.msg
    TaskBehavior.msg
    ListOfRunningTasks.msg
    RecoveryPlanFinished.msg
    ActivationChange.msg
)

add_service_files(
    DIRECTORY srv
    FILES
    # Executive Layer
    GeneratePath.srv
    CheckSituation.srv
    RequestBehaviorActivation.srv
    RequestBehaviorDeactivation.srv
    AddBelief.srv
    CheckBeliefFormat.srv
    CheckBehaviorFormat.srv
    QueryBelief.srv
    RemoveBelief.srv 
    ActivateBehavior.srv
    DeactivateBehavior.srv
    CheckActivationConditions.srv
    SetControlMode.srv
    StopTask.srv
    StartTask.srv
    RecoveryPlan.srv
)

generate_messages(
  DEPENDENCIES
  std_msgs
  sensor_msgs
  geometry_msgs
  std_srvs
  opencv_apps
	shape_msgs
)

catkin_package(
  INCLUDE_DIRS ${DRONEMSGS_INCLUDE_DIR}
  CATKIN_DEPENDS
  message_runtime
  std_msgs
  sensor_msgs
  geometry_msgs
  std_srvs
  opencv_apps
	shape_msgs
)

include_directories(${DRONEMSGS_INCLUDE_DIR})
include_directories(${catkin_INCLUDE_DIRS})


add_custom_target(${PROJECT_NAME}
            SOURCES ${DRONEMSGS_HEADER_FILES}
            )

