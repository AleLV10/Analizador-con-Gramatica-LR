Gramática y Sintaxis del Lenguaje

Descripción general

Nuestra gramática permite a los usuarios declarar y asignar variables al inicio del programa. Es posible solo declarar variables o también asignarles valores iniciales.
Posteriormente, se pueden desarrollar sentencias aritméticas (operaciones), condicionales (if) o de bucle (for). Se pueden crear estructuras anidadas (if dentro de if, for dentro de for) tantas veces como se necesite para construir el programa.
Esta gramática está diseñada para que el usuario pueda escribir código de manera clara, con declaraciones, operaciones, condicionales y bucles, respetando la sintaxis definida.

Gramática Formal
G(L) = {T, N, Z, S}

Terminales (T)
{id, int, float, char, , , ;, +, -, /, *, (, ), {, }, <, >, =, !, num, numf, litchar, for, if, else}

No terminales (N)
{P, Tipo, V, Sen, A, Exp, Term, F, T, E, I, Con, D, EL, For, in, C, ad}

Producciones (Z)
P   -> Tipo id V | Sen
Tipo -> int | float | char
V   -> , id V | ; P
Sen -> A Sen | I Sen | For Sen | &
A   -> id = Exp ;
Exp -> Term E
Term -> F T
E   -> + Term E | - Term E | &
F   -> id | ( Exp ) | num | numf | litchar
T   -> * F T | / F T | &
I   -> if ( Con ) { Sen } EL
Con -> id D id
D   -> < | > | <= | >= | == | !=
EL  -> else { Sen } | &
For -> for ( in ; Con ; ad ) { Sen }
in  -> int C | C
C   -> id = num
ad  -> id++ | id-- | ++id | --id

Símbolo inicial (S)
S = {Z}

Primeros y Siguientes
No Terminal	Primeros	Siguientes
P’	int, float, char, id, if, for	$
P	int, float, char, id, if, for	$
Tipo	int, float, char	id
V	,, ;	$
Sen	id, if, for, &	$, }
A	id	id, if, for, $, }
Exp	id, (, num, numf, litchar	;, )
Term	id, (, num, numf, litchar	+, -, ;, )
E	+, - , &	;, )
F	id, (, num, numf, litchar	*, /, +, -, ;, )
T	*, /, &	+, -, ;, )
I	if	id, if, for, $, }
Con	id	;, )
D	<, >, =, !	id
EL	else, &	id, if, for, $, }
For	for	id, if, for, $, }
in	int, id	;
C	id	;
ad	id, +, -	)
