Lexical Rules:

Begin File: BEGIN
End of File: END
If Token: when
Else Token: elsewhen
Loop: loop
Addition: +
Subtraction: -
Multiplication: *
Division: /
Modulo: %
Exponent: E
Assignment: =
Declaration: num
Greater Than: >
Less Than: <
Greate Than Or Equal To: >=
Less Than Or Equal To: <=
Equal To: ==
Not Equal To: !=
Not: !
Left Bracket: {
Right Bracket: }
Left Paren: (
Right Paren: )
Integer: (1 | 2 | 4 | 8)_[0-9]+
Identifier: [A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z][A-Za-z]?[A-Za-z]?
And: &
Or: |

Production Rules:

program -> BEGIN stmt_list END
stmt_list -> stmt stmt_list*
stmt_list -> '' 
stmt_list* -> stmt stmt_list*
stmt -> if_stmt
stmt -> declr
stmt -> assign 
stmt -> loop_stmt
if_stmt -> when ( bexpr ) { stmt_list }
if_stmt -> when ( bexpr ) { stmt_list } elsewhen { stmt_list }
loop_stmt -> loop ( expr ) { stmt_list }
declr -> num id
assign -> id = expr
bexpr -> bor bexpr*
bexpr* -> ''
bexpr* -> & bexpr*
bexpr* -> bor
bor -> beq bor*
bor* -> ''
bor* -> | bor* 
bor* -> beq
beq -> bcomp beq*
beq* -> ''
beq* -> == beq*
beq* -> != beq*
beq* -> bcomp
bcomp -> bnot bcomp*
bcomp* -> ''
bcomp* -> > bcomp* 
bcomp* -> < bcomp*
bcomp* -> >= bcomp*
bcomp* -> <= bcomp*
bcomp* -> bnot
bnot -> ! expr 
bnot -> expr
expr -> mul_op expr*
expr* -> ''
expr* -> + mul_op add_op*
expr* -> mul_op
mul_op -> sub_op mul_op*
mul_op* -> ''
mul_op* -> * sub_op mul_op*
mul_op* -> sub_op
sub_op -> div_op sub_op*
sub_op* -> ''
sub_op* -> - div_op sub_op*
sub_op* -> div_op
div_op -> mod_op div_op*
div_op* -> ''
div_op* -> / mod_op div_op*
div_op* -> mod_op
mod_op -> exp_op mod_op*
mod_op* -> ''
mod_op* -> % exp_op mod_op*
mod_op* -> exp_op
exp_op -> term exp_op*
exp_op* -> ''
exp_op* -> E term exp_op*
exp_op* -> term
term -> id
term -> integer
term -> ( expr )
