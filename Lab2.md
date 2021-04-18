# SUBC Parser
Andres Canas

## Description
The purpose of this project is to create a Recursive Descent Parser for the programming language SUBC. The executable file, subc, must be run with a file name as a parameter. It can also be ran with a switch -ast to print out the Abstract Syntax Tree associated with the program.

## Design
This Recursive Descent Parser is designed in C++ and uses three supporting modules: The Parser module, The Lexical Analyzer, and the First-Child, Next-Sibling Tree module. The parser is designed by leveraging the file.peek() command. By observing the next character the Parser can decide what function is must call next. There are several cases when the parser may observe a character that can belong to multiple function routes. This can be determined by calculating follow sets in the grammar. To account for this our system uses a try -> catch exception mechanism. For the n possibilites of commands that begin with file.peek(), the parser will call the lexicaly analyzer to read that command. Due to 'catch' it will not fail unless all possibilites have been checked. If a successful scan is processed by the lexical analyzer, the parser will continue with the respective function route.


## Verification
The folder contains a Makefile, which can be used to build the executable program 'subc'.  
The program can be ran as follows: ./subc path_to_program_text_file  
or as: ./subc -ast path_to_program_text_file  
to print out the Abstract Syntax Tree  

##Contact
Thank you, for any questions please email andrescanas001@ufl.eduk
