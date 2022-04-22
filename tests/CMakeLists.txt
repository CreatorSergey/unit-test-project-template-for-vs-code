# заголовочные файлы
set(HEADER_FILES
	catch.hpp
)

# файлы для сборки
set(SOURCE_FILES	
	tests.cpp
)

# имя библиотеки
set(LIBRARY_NAME cpplib)

# запускаемый файл
add_executable(tests ${SOURCE_FILES})

# линковка библиотек
target_link_libraries(tests ${LIBRARY_NAME})