8/20/2013
==========
Reading: Learn You a Haskell for Great Good: Chapters 1-8


8/22/2013

8/29/2013
HW will be in .lhs file (Literate Haskell file)
Contains Latex code with:

Some text (or Latex source)
\begin{code} 
   Source code
    .
    .
    .
\end{code}

Use preprocessor that takes lhs and produces a tex file (Lhs2Tex)

9/12/2013
==========
HW Exercises:

Show that:
cross (f,g) .  cross(h,k) = cross (f . h, g . k)

Show that:
map f (xs ++ ys) = map f xs ++ map f ys

Show that:
map f . concat = concat . map (map f)

9/17/2013
==========
Reading: Chapters 1-3
Specifications of Programming Languages

Grammars:
BNF example of a BNF grammar:

<statement> ::= <assignment>
                         | <expression>
                         | <conditional statement>
.
.
.

<assignment> ::= <expression> = <expression> ;

<block> ::= { <list of statements or blocks> }
<list of statements or blocks> ::= 
                                    | <statement> <list of statements or blocks>
                                    | <block> <list of statements or blocks>

Context Free Grammar (CFG)

S -> A
S -> C
.
.
.
A -> E = E;
.
.
.
Is the string derivable from the given grammar?
-------------------------------------------------------------
CFG
S
S -> A
S -> B
A -> a
B -> Ab

"aa"?   No!
"a"?    Yes!    S => A => a
S => B => Ab => ab

--------------------------------------------------------------
S -> A      S -> B
A -> aA     B -> bB
A ->        B -> 

--------------------------------------------------------------
Ambiguous grammar - Don't want them.

S -> A      
A -> aA     
A -> Aa
A ->         

"aaa" can be created by 2 or more different parse trees.

S -> A
A -> Aa
A -> epsilon
For parsing top-down, make sure grammar is not left recursive.

--------------------------------------------------------------
Syntax for a language of arithmetic expression (numbers & booleans)


t ::= true                  (boolean constant true)
    | false
    | if t then t else t    (conditional)
    | 0                     (intended constant)
    | succ t                (1 more than t)
    | pred t                (1 less than t)
    | iszero t              (test for zero)

Syntax describes trees.

-------------------------------------------------------------------
Same syntax written as inference rules:

T = ret of all terms in the language

9/19/2013
==========
t ::= true                  (boolean constant true)
     false
     if t then t else t    (conditional)
     0                     (intended constant)
     succ t                (1 more than t)
     pred t                (1 less than t)
     iszero t              (test for zero)

if false then if false then 0 else 0 else 0  (In the language)
if false then 0 else false (In the language)
false if then 0 else if (NOT in the language)

Maybe rule out terms through type structure?

--------------------------------------------------------------------

Don't worry about types for today.

How do you describe the semantics of a language? i.e. the value of a syntactic expression.

!!Operational semantics!!

Ties the meaning of the program to the operations of a machine.

                                             execution                              read out
t ---> initial state of an abstract machine ----------> final state of the machine ----------> value

-------------------------------------------------------------------------
Even simpler: Abstract machine at the term level

    execution
t -------------> final term
