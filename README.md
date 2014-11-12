Diet YAML
=========

Diet YAML is a light weight version of YAML that removes much of the complex aspects of the mainline YAML specification. In particular:

* No declarations.
* No type notation, only implicit core types are supported.
* Mapping keys must always be scalar.
* Anchors and merging are optional.

# EBNF

The EBNF looks something like this (still a work in progress):

```bnf
YAML ::= Start Data End
Start ::= ( "\n---" | "" )
End ::= ( "\n..." | "\n---" | "" )
Data ::= (Scalar | Sequence | Mapping )
Scalar ::= (Number | String | Date | Boolean | Nil)
Sequence ::= ( "[" Data ("," Data)* "]" | OptionalTab "-" Data ("\n" OptionalTab "-" Data)* )
Mapping ::= ( "{" Key ":" Data ("," Key ":" Data)* "}" | Tab Key ":" Data ("\n" Tab Key ":" Data)* )
OptinalTab ::= Space*
Tab ::= Space+
String ::= '"' .* '"' | [^-] .+
Number ::= ("+" | "-")? [0-9]* ("." [0-9]+)?
Date ::= [0-9][0-9][0-9][0-9] "-" [0-1][0-9] "-" [0-3][0-9] ( [0-2][0-9] ":" [0-5][0-9] ":" [0-5][0-9] )?
Boolean ::= "true" | "false"
Nil ::= "~"
Space ::= " "
```
