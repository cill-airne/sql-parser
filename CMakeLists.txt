cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

project(arrow LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR})

add_library(sql-parser SHARED src/parser/bison_parser.cpp
                                src/parser/bison_parser.h
                                src/parser/flex_lexer.h
                                src/parser/flex_lexer.cpp
                                src/sql/CreateStatement.h
                                src/sql/DeleteStatement.h
                                src/sql/DropStatement.h
                                src/sql/ExecuteStatement.h
                                src/sql/ExportStatement.h
                                src/sql/Expr.cpp
                                src/sql/Expr.h
                                src/sql/ImportStatement.h
                                src/sql/InsertStatement.h
                                src/sql/PrepareStatement.cpp
                                src/sql/PrepareStatement.h
                                src/sql/SelectStatement.h
                                src/sql/ShowStatement.h
                                src/sql/SQLStatement.cpp
                                src/sql/SQLStatement.h
                                src/sql/statements.cpp
                                src/sql/statements.h
                                src/sql/Table.h
                                src/sql/TransactionStatement.h
                                src/sql/UpdateStatement.h

                                src/util/sqlhelper.cpp
                                src/util/sqlhelper.h

                                src/SQLParser.cpp
                                src/SQLParser.h
                                src/SQLParserResult.cpp
                                src/SQLParserResult.h


)

install(TARGETS sql-parser
        LIBRARY DESTINATION lib
        PUBLIC_HEADER DESTINATION include)


install(DIRECTORY src/
    DESTINATION include
    FILES_MATCHING PATTERN "*.h*"
)