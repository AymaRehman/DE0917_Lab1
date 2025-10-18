# DE0917_Lab1

Author: Ayma Rehman  
Student ID: 241ADB165  
GitHub Repository: https://github.com/AymaRehman/DE0917_Lab1   

## Aim of the Assignment

Write a C program that evaluates arithmetic expressions from text files using Python-like operator rules and standard C arithmetic semantics. It should read input files (or directories), parse and evaluate expressions, report results or error locations, and save outputs using a defined naming convention.  

## The parser supports:

- Integers and floating-point numbers (double)  
- Operators: +, -, *, /, and exponentiation **  
- Parentheses for grouping expressions ( ... )  
- Multiple lines in input files (up to 10,000 characters)  
- Error reporting with precise 1-based character positions  
- Batch processing of multiple .txt files in a folder  
- Comment lines starting with # (ignored during parsing)  
- Custom output directory with default fallback  

## Compilation Instructions

Compile using GCC:  
`gcc -v calc.c -o calc.exe`    

Run with:  
`./calc -d e:/c/source_folder -o e:/c/output_folder text-file_to_process.txt`  

## Main Arguments  

This program expects at least 2 and at most 5 arguments:  

`-d or --dir and then source dirctory name`  
These are mandatory.  

` -o or --output-dir and then output directory name`   
These are optional, however, if omitted, default will be created.  

`source file name`  
This is optional, however, if omitted, all .txt files in source directory will be processed.  
