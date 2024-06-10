    %let pgm=utl-roots-of-a-non-linear-function-using-python-sympy;

    Roots of a non linear function using python sympy

    inspired by
    https://blogs.sas.com/content/iml/2011/08/03/finding-the-root-of-a-univariate-function.html

    Sympy provides symbolic closed form solutons or numerical solutions.

    github
    https://tinyurl.com/bde2kzpt
    https://github.com/rogerjdeangelis/utl-roots-of-a-non-linear-function-using-python-sympy

    Related Repos
    https://github.com/rogerjdeangelis/utl-calculating-the-cube-root-of-minus-one-with-drop-down-to-python-symbolic-math-sympy
    https://github.com/rogerjdeangelis/utl-sorting-the-roots-of-a-polynomial-in-ascending-order-of-the-imaginary-part
    https://github.com/rogerjdeangelis/utl_roots_cubic_equations

    /****************************************************************************************************************************/
    /*                                               |                             |                                            */
    /*               INPUT                           |   PROCESS                   |                OUTPUT                      */
    /*                                               |                             |                                            */
    /*                            2                  |                             |                                            */
    /*           3              -x                   |                             |                                            */
    /*    y = - x  + 5*x + 1 + e                     | %utl_pybegin;               |     Roots                                  */
    /*                                               | parmcards4;                 |                                            */
    /*    root guesses                               | from sympy import \         |     Root: -2.12715                         */
    /*                                               |  symbols \                  |     Root: -0.38390                         */
    /*    -4 -2 0 2 3 4                              |  ,exp \                     |     Root:  2.33044                         */
    /*                                               |  ,pprint \                  |                                            */
    /*                       X                       |  ,nsolve                    |                                            */
    /*     -4     -2         0         2       4     | x = symbols('x')            |   -4        -2         0         2      4  */
    /*    --+------+---------+---------+-------+--   | expr= \                     | Y-+---------+---------+---------+------+   */
    /*    |    +  |        |             |       |   |   exp(-x**2)-x**3+5*x+1     |  |                                     |   */
    /* 10 +       |        |             |       +10 | pprint(expr)                |  |    y = exp(-x**2) - x**3 + 5*x +1   |   */
    /*    |    +  |        |             |       |   | initial_guesses = [(-4,4)]  |  |                                     |   */
    /*    |       |        |             |       |   | for guess in range(-4,4,2): |  |      +  |        | + Observed  |    |   */
    /*    |     + |        |             |       |   |   root= \                   |10+         |        | R=Roots     |    +10 */
    /*    |     + |        |       +     |       |   |    nsolve(expr,(x),guess)   |  |      +  |        |   -2.127    |    |   */
    /*  5 +       |        |     ++++++  |       + 5 |   print(f"Root: {root}")    |  |         |        |    0.384    |    |   */
    /*    |      +|        |   ++     ++ |       |   | ;;;;                        |  |       + |        |    2.330    |    |   */
    /*    |      +|        |  ++       + |       |   | %utl_pyend;                 |  |       + |        |       +     |    |   */
    /*  Y |       +        | ++         +|       | Y |                             | 5+         |        |     ++++++  |    + 5 */
    /*    |       +        |++          +|       |   |                             |  |        +|        |   ++     ++ |    |   */
    /*  0 +-------++-------++------------+-------+ 0 |                             |  |        +|        |  ++       + |    |   */
    /*    |       |+      ++             +       |   |                             | Y|        +|        | ++         +|    |Y  */
    /*    |       | +    ++|             |+      |   |                             |  |        +|        +            +|    |   */
    /*    |       |  ++++  |             |       |   |                             | 0+- =2.127>R -0.384>R ------2.33->R ---+ 0 */
    /*    |       |        |             |+      |   |                             |  |         |+      ++             +    |   */
    /* -5 +       |        |             | +     +-5 |                             |  |         | +    ++|             |+   |   */
    /*    |       |        |             |       |   |                             |  |         |  ++++  |             |    |   */
    /*    |       |        |             | +     |   |                             |  |         |        |             |+   |   */
    /*    |       |        |             |       |   |                             |-5+         |        |             | +  +-5 */
    /*    |       |        |             |  +    |   |                             |  |         |        |             |    |   */
    /* 10 +       |        |             |       +10 |                             |  |         |        |             | +  |   */
    /*    |       |        |             |  +    |   |                             |  |         |        |             |    |   */
    /*    --+------+---------+---------+-------+--   |                             |  |         |        |             |  + |   */
    /*     -4     -2         0         2       4     |                             |10+         |        |             |    +10 */
    /*                       X                       |                             |  |         |        |             |  + |   */
    /*                                               |                             |  -+---------+---------+---------+------+   */
    /*                                               |                             |  -4        -2         0         2      4   */
    /*                                               |                             |                                            */
    /****************************************************************************************************************************/


    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */
                            2
           3              -x
    y = - x  + 5*x + 1 + e

    root guesses

    -4 -2 0 2 3 4

    SAS & SYMPY

    y = exp(-x**2) - x**3 + 5*x +1


    options ls=80 ps=32;
    proc plot data=sd1.have(rename=y=y123456789012345678901234567890);
      plot y123456789012345678901234567890*x='+'/
       box href=-2.13 -0.38 2.33
       vref=0
       vaxis=-10 to +10 by 5;
    run;quit;
                           X
         -4     -2         0         2       4
        --+------+---------+---------+-------+--
        |    +  |        |             |       |
     10 +       |        |             |       +10
        |    +  |        |             |       |
        |       |        |             |       |
        |     + |        |             |       |
        |     + |        |       +     |       |
      5 +       |        |     ++++++  |       + 5
        |      +|        |   ++     ++ |       |
        |      +|        |  ++       + |       |
      Y |       +        | ++         +|       | Y
        |       +        |++          +|       |
      0 +-------++-------++------------+-------+ 0
        |       |+      ++             +       |
        |       | +    ++|             |+      |
        |       |  ++++  |             |       |
        |       |        |             |+      |
     -5 +       |        |             | +     +-5
        |       |        |             |       |
        |       |        |             | +     |
        |       |        |             |       |
        |       |        |             |  +    |
     10 +       |        |             |       +10
        |       |        |             |  +    |
        --+------+---------+---------+-------+--
         -4     -2         0         2       4

                               X

    /*
     _ __  _ __ ___   ___ ___  ___ ___  ___  ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|/ _ \/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \  __/\__ \
    | .__/|_|  \___/ \___\___||___/___/\___||___/
    |_|
    */

    %utl_pybegin;
    parmcards4;
    from sympy import symbols,exp,pprint, nsolve
    x = symbols('x')
    expr =exp(-x**2) - x**3 + 5*x +1
    pprint(expr)
    initial_guesses = [(-4,4)]
    for guess in range(-4,4,2):
    root = nsolve(expr, (x), guess)
    print(f"Root: {root}")
    ;;;;
    %utl_pyend;

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */

    /****************************************************************************************************************************/
    /*                                                                                                                          */
    /*          Roots                                                                                                           */
    /*                                                                                                                          */
    /*          Root: -2.12715                                                                                                  */
    /*          Root: -0.38390                                                                                                  */
    /*          Root:  2.33044                                                                                                  */
    /*                                                                                                                          */
    /*                             X                                                                                            */
    /*        -4        -2         0         2      4                                                                           */
    /*      Y-+---------+---------+---------+------+                                                                            */
    /*       |                                     |                                                                            */
    /*       |    y = exp(-x**2) - x**3 + 5*x +1   |                                                                            */
    /*       |                                     |                                                                            */
    /*       |      +  |        | + Observed  |    |                                                                            */
    /*     10+         |        | R=Roots     |    +10                                                                          */
    /*       |      +  |        |   -2.127    |    |                                                                            */
    /*       |         |        |    0.384    |    |                                                                            */
    /*       |       + |        |    2.330    |    |                                                                            */
    /*       |       + |        |       +     |    |                                                                            */
    /*      5+         |        |     ++++++  |    + 5                                                                          */
    /*       |        +|        |   ++     ++ |    |                                                                            */
    /*       |        +|        |  ++       + |    |                                                                            */
    /*      Y|        +|        | ++         +|    |Y                                                                           */
    /*       |        +|        +            +|    |                                                                            */
    /*      0+- =2.127>R -0.384>R ------2.33->R ---+ 0                                                                          */
    /*       |         |+      ++             +    |                                                                            */
    /*       |         | +    ++|             |+   |                                                                            */
    /*       |         |  ++++  |             |    |                                                                            */
    /*       |         |        |             |+   |                                                                            */
    /*     -5+         |        |             | +  +-5                                                                          */
    /*       |         |        |             |    |                                                                            */
    /*       |         |        |             | +  |                                                                            */
    /*       |         |        |             |    |                                                                            */
    /*       |         |        |             |  + |                                                                            */
    /*     10+         |        |             |    +10                                                                          */
    /*       |         |        |             |  + |                                                                            */
    /*       -+---------+---------+---------+------+                                                                            */
    /*       -4        -2         0         2      4                                                                            */
    /*                                                                                                                          */
    /****************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
# utl-roots-of-a-non-linear-function-using-python-sympy
Roots of a non linear function using python sympy 
