FIND_PACKAGE(BISON)
FIND_PACKAGE(FLEX)

BISON_TARGET(
    CTMParser
    mc_parser.yy ${CMAKE_CURRENT_BINARY_DIR}/mc_parser.tab.cpp
)

FLEX_TARGET(
    CTMLexer
    mc_lexer.l ${CMAKE_CURRENT_BINARY_DIR}/mc_lexer.cpp
)

ADD_FLEX_BISON_DEPENDENCY(CTMLexer CTMParser)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR)