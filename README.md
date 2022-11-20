a.) Lexical Rules: <br />
 <br />Begin File: BEGIN <br />
End of File: END <br />
If Token: when <br />
Else Token: elsewhen  <br />
Loop: loop <br />
Addition: + <br />
Subtraction: - <br />
Multiplication: * <br />
Division: / <br />
Modulo: % <br /> 
Exponent: E <br />
Assignment: = <br />
Declaration: num <br />
Greater Then: > <br />
Less Then: < <br />
Greater Then Or Equal To: >= <br />
Less Then Or Equal To: <= <br />
Equal To: == <br />
Not Equal To: != <br />
Not: ! <br />
Left Bracket: { <br />
Right Bracket: } <br />
Left Paren: ( <br />
Right Paren: ) <br />
Integer: (1 | 2 | 4 | 8)_[0-9]+ <br />
Identifier: [A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z]?[A-Za-z]? <br />
And: & <br />
Or: | <br />

b.) Production Rules: <br /> <br />

program -> BEGIN stmt_list END <br />
stmt_list -> stmt stmt_list* <br />
stmt_list* -> ''  <br />
stmt_list* -> stmt stmt_list* <br />
stmt -> if_stmt <br />
stmt -> declr <br />
stmt -> assign <br />
stmt -> loop_stmt <br />
if_stmt -> when ( bexpr ) { stmt_list } <br />
if_stmt -> when ( bexpr ) { stmt_list } elsewhen { stmt_list } <br />
loop_stmt -> loop ( expr ) { stmt_list } <br />
declr -> num id <br />
assign -> id = expr <br />
bexpr -> bor bexpr* <br />
bexpr* -> '' <br />
bexpr* -> & bexpr* <br />
bexpr* -> bor <br />
bor -> beq bor* <br />
bor* -> '' <br />
bor* -> | bor* <br />
bor* -> beq <br />
beq -> bcomp beq* <br />
beq* -> '' <br />
beq* -> == beq* <br />
beq* -> != beq* <br />
beq* -> bcomp <br />
bcomp -> bnot bcomp* <br />
bcomp* -> '' <br />
bcomp* -> > bcomp* <br />
bcomp* -> < bcomp* <br />
bcomp* -> >= bcomp* <br />
bcomp* -> <= bcomp* <br />
bcomp* -> bnot <br />
bnot -> ! expr <br />
bnot -> expr <br />
expr -> mul_op expr* <br />
expr* -> '' <br />
expr* -> + mul_op add_op* <br />
expr* -> mul_op <br />
mul_op -> sub_op mul_op* <br />
mul_op* -> '' <br />
mul_op* -> * sub_op mul_op* <br />
mul_op* -> sub_op <br />
sub_op -> div_op sub_op* <br />
sub_op* -> '' <br />
sub_op* -> - div_op sub_op* <br /> 
sub_op* -> div_op <br />
div_op -> mod_op div_op* <br />
div_op* -> '' <br />
div_op* -> / mod_op div_op* <br />
div_op* -> mod_op <br />
mod_op -> exp_op mod_op* <br />
mod_op* -> '' <br />
mod_op* -> % exp_op mod_op* <br />
mod_op* -> exp_op <br />
exp_op -> term exp_op* <br />
exp_op* -> '' <br />
exp_op* -> E term exp_op* <br />
exp_op* -> term <br />
term -> id <br />
term -> integer <br />
term -> ( expr ) <br />

c.) LL Grammar <br />

(FIRST) program -> {BEGIN} <br />
(FIRST) stmt_list -> {'', when, num, id, loop} <br />
(FIRST) stmt_list* -> {when, num, id, loop} <br />
(FIRST) stmt -> {when, num, id, loop} <br />
(FIRST) if_stmt -> {when} <br />
(FIRST) loop_stmt -> {loop} <br />
(FIRST) declr -> {num} <br />
(FIRST) assign -> {id} <br />
(FIRST) bexpr -> {!, id, integer , (} <br />
(FIRST) bexpr* -> {'', &, !, id, integer, (} <br />
(FIRST) bor -> {!, id, integer, (}
(FIRST) bor* -> {'', |, !, id, integer, (} <br />
(FIRST) beq -> {!, id, integer, ( }
beq* -> {'', ==, !=, !,  id, integer, (}
bcomp -> {!, id, integer, (}* <br />
bcomp* -> {'', >, <, >=, <=, !, id, integer, (} <br />
bnot -> {!, id, integer, (}
expr -> {id, integer, (} <br />
expr* -> {'', +, id, integer, (}
mul_op -> {id, integer , (} <br />
mul_op* -> {'',\*,id,integer,(} <br />
sub_op -> {id,integer,(} <br />
sub_op* -> '' <br />
sub_op* -> - div_op sub_op* <br /> 
sub_op* -> div_op <br />
div_op -> mod_op div_op* <br />
div_op* -> '' <br />
div_op* -> / mod_op div_op* <br />
div_op* -> mod_op <br />
mod_op -> exp_op mod_op* <br />
mod_op* -> '' <br />
mod_op* -> % exp_op mod_op* <br />
mod_op* -> exp_op <br />
exp_op -> term exp_op* <br />
exp_op* -> '' <br />
exp_op* -> E term exp_op* <br />
exp_op* -> term <br />
term -> id <br />
term -> integer <br />
term -> ( expr ) <br />
