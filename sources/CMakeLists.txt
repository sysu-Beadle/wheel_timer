# generate wheel_timer.h
file(GLOB_RECURSE HEADERS RELATIVE ${PROJECT_SOURCE_DIR}/sources *.h)
list(REMOVE_ITEM HEADERS "wheel_timer.h")
file(WRITE wheel_timer.h "// Auto Generated By CMake\n")
file(APPEND wheel_timer.h "#pragma once\n\n")
foreach(header ${HEADERS})
    file(APPEND wheel_timer.h "#include \"${header}\"\n")
endforeach()

# find all cpps
file(GLOB_RECURSE SOURCES *.cpp)

# generate dynamic library
add_library(wheel_timer_so SHARED ${SOURCES})
set_target_properties(wheel_timer_so PROPERTIES POSITION_INDEPENDENT_CODE ON)
set_target_properties(wheel_timer_so PROPERTIES OUTPUT_NAME "wheel_timer")

# # generate static library
# add_library(wheel_timer_a STATIC ${SOURCES})
# set_target_properties(wheel_timer_a PROPERTIES OUTPUT_NAME "wheel_timer" PREFIX "")
