Lexical Rules: <br /> <br />
 <br />Begin File: BEGIN <br />
End of  <br />File: END <br />
If Token: when <br /> <br />
Else Token: elsewhen  <br /><br />
Loop: loop <br /> <br />
Addition: + <br /> <br />
Subtraction: - <br />
Multipl <br />ication: * <br />
Division: / <b <br />r />
Modulo: % <br /> <br />
Exponent: E <br /> <br />
Assignment: = <br /> <br />
Declaration: num <br />
G <br />reater Than: > <br />
Less Tha <br />n: < <br />
Greate Than Or  <br />Equal To: >= <br />
Less Than Or Equal To: <br /> <= <br />
Equal To: == <br />
Not Equal <br /> To: != <br />
Not: ! <br />
Left Bracket: { <br />
Right Bracket: } <br />
Left Paren: ( <br />
Right Paren: ) <br />
Integer: (1 | 2 | 4 | 8)_[0-9]+ <br />
Identifier: [A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z]?[A-Za-z]? <br />
And: & <br />
Or: | <br />

Production Rules: <br /> <br />

program -> BEGIN stmt_list END <br />
stmt_list -> stmt stmt_list* <br />
stmt_list -> ''  <br />
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
