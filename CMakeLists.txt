# **************************************************************************** #
#                                                                              #
#                                                         ::::::::             #
#    CMakeLists.txt                                     :+:    :+:             #
#                                                      +:+                     #
#    By: jvan-kra <jvan-kra@student.codam.nl>         +#+                      #
#                                                    +#+                       #
#    Created: 2022/11/03 15:22:00 by jvan-kra      #+#    #+#                  #
#    Updated: 2022/11/03 15:22:00 by jvan-kra      ########   odam.nl          #
#                                                                              #
# **************************************************************************** #

cmake_minimum_required(VERSION 3.23.0)

project(philosophers)
set (SRCS
	src/main.c
	src/parse.c
	src/utils.c
	src/mutex.c
	src/forks.c
	src/params.c
	src/threads.c
	src/run_sim.c
	src/monitoring.c
	src/philo.c
	src/philo_utils.c
	src/philo_eat.c
	src/philo_table.c
	src/ft_atoui_safe.c
	)
set (EXEC_NAME philo)

#compiler settings:
set (CMAKE_C_COMPILER gcc)
set (CMAKE_C_FLAGS "-Wall -Werror -Wextra -O3")
set (CMAKE_C_FLAGS_DEBUG "-g -fsanitize=address") #cmake -DCMAKE_BUILD_TYPE=DEBUG to add debug flags
set (CMAKE_C_FLAGS_THREAD "-g -fsanitize=thread")
set (CMAKE_C_FLAGS_TIMEOUT "-DTIMEOUT_CHECK=1")
set (CMAKE_EXPORT_COMPILE_COMMANDS ON) #vscode include path checking

#norm rules so flclean and re work
add_custom_target(fclean make clean)
add_custom_target(re make clean COMMAND make)

#make executable with output name specified under EXEC_NAME and sources specified under SRCS
add_executable(${EXEC_NAME} ${SRCS})

target_include_directories(${EXEC_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)
