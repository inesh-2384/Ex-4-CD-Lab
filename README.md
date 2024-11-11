Ex. No : 4
RECOGNITION OF A VALID VARIABLE WHICH STARTS WITH A LETTER FOLLOWED BY ANY NUMBER OF LETTERS OR DIGITS USING YACC
Register Number : 212223220036

Aim:
To write a YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits.

ALGORITHM
Start the program.
Write a program in the vi editor and save it with .l extension.
In the lex program, write the translation rules for the keywords int, float and double and for the identifier.
Write a program in the vi editor and save it with .y extension.
Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
Compile the yacc program with YACC compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
Compile these with the C compiler as gcc lex.yy.c y.tab.c
Enter a statement as input and the valid variables are identified as output.
PROGRAM
Program name:ex4.l
%{
/* This LEX program returns the tokens for the Expression */
#include"y.tab.h"
%}
%%
"int" {return INT;}
"float" {return FLOAT;}
"double" {return DOUBLE;}
[a-zA-Z]*[0-9]* {printf("\nIdentifier is %s",yytext);
return ID;
}
. return yytext[0];
\n return 0;
%%
int yywrap()
{
return 1;
}
Program name:ex4.y
%{
#include<stdio.h>
/* This YACC program is for recognising the Expression*/
 %}
%token ID INT FLOAT DOUBLE
%%
D: T L
;
L: L,ID
| ID
;
T: INT
| FLOAT
| DOUBLE
;
%%
extern FILE*yyin;
main()
{
do
{
yyparse();
}while(!feof(yyin));
}
yyerror(char*s)
{
}
Output
![image](https://github.com/user-attachments/assets/c01e813f-f7de-4771-b723-47508251d17f)


Result
A YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits is executed successfully and the output is verified.

