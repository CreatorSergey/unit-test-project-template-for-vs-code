# минимальная версия cmake
cmake_minimum_required(VERSION 3.6)

# название проекта
project(MyProgram)

# рекурсивный сбор директорий в список
MACRO(get_directories_recursive return_list from)
    FILE(GLOB_RECURSE new_list ${from})
    SET(dir_list "")
    FOREACH(file_path ${new_list})
        GET_FILENAME_COMPONENT(dir_path ${file_path} PATH)
        SET(dir_list ${dir_list} ${dir_path})
    ENDFOREACH()
    LIST(REMOVE_DUPLICATES dir_list)
    SET(${return_list} ${dir_list})
ENDMACRO()

# рекурсивный сбор файлов из папок в список
MACRO(get_files_from_directories_recursive return_list from)
    FILE(GLOB_RECURSE new_list ${from})
    SET(all_files "")
    FOREACH(file_path ${new_list})
        SET(all_files ${all_files} ${file_path})
    ENDFOREACH()
    LIST(REMOVE_DUPLICATES all_files)
    SET(${return_list} ${all_files})
ENDMACRO()

# подключение файлов для сборки
set(SOURCE_FILES src/main.cpp)

# заголовочные файлы из статической библиотеки
set(LIBRARY_NAME cpplib)
include_directories(libs)

# подключение вложенных проектов
add_subdirectory(libs)
add_subdirectory(tests)

# регистрация запускаемого файла
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

# линковка библиотек
target_link_libraries(${PROJECT_NAME} ${LIBRARY_NAME})