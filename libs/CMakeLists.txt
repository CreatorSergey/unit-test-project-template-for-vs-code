# заголовочные файлы
set(HEADER_FILES
	cpplib.h
)

# файлы для сборки
set(SOURCE_FILES
  cpplib.cpp
)

# сборка статической библиотеки
add_library(cpplib ${SOURCE_FILES} ${HEADER_FILES})