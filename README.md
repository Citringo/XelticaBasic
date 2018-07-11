# XelticaBasic

XelticaBasic is an implementation of the BASIC language.

## Sample Code

```bas

' Hello World
PRINT "Hello, world!"

' Expression
A = 3 + 5
B = 3 + 4
C = a + b

' Combine string
S$ = A + " + " + B + " = " + C
PRINT S$

' Input
T = VAL(SCAN("数値> "))

' Inline If
IF T < 5 THEN ?"Tは5未満です" ELSE ?"Tは5以上です"

' Block Style If
IF T < 6 THEN
	?"Tは6未満"
ELSEIF T < 10 THEN
	?"Tは6以上10未満"
ELSE
	?"Tは10以上"
ENDIF

' Switch
SWITCH T
	CASE 0
		?"Tは0"
	CASE 1
		?"Tは1"
	CASE 2
		?"Tは2"
	CASE 3
		?"Tは3"
	DEFAULT
		?"Tは0, 1, 2, 3以外
END
' Define a func
DEF SAYSAYSAY TEXT$
	'for statement
	FOR I = 0 TO 10
		?TEXT$
	NEXT
END

SAYSAYSAY "ピザ"

' Define an array
VAR ARR[10]
FOR I = 0 TO 9
	ARR[I] = (I + 4)  % 10
NEXT

' Define an array 2
ARR2 = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

' Define a struct
STRUCT VEC2
	VAR X
	VAR Y
END

' Use a struct variable

VAR V:VEC2
V.X = 10
V.Y = 20

' syntax sugar
V2:VEC2 = [10, 20]

' Both these are same
VALUE = 3
VALUE:NUM = 3

VALUE$ = "aa"
VALUE:STRING = "aa"

' while
I = 0
WHILE I < 50
	?I
	' inclement
	INC I
WEND

' Use a function

F = SIN(100)

' define a class

' + public
' - private
' * internal
' ~ protected

CLASS +MYCLASS
	' Field
	VAR -_A
	VAR -_B$

	' Properties
	PROP +A
		GET
			RETURN _A
		SET
			_A = VALUE
	END

	PROP +B$
		GET
			RETURN _B$
		-SET
			IF VALUE != "yes" && VALUE != "no" THEN
				THROW INIT EXCEPTION("A wrong value!")
			ENDIF
			
			_B$ = VALUE
	end

	' Auto Property
	PROP +C GETSET

	' constructor
	INIT(A, B$, C)
		MY.A = A
		MY.B$ = B$
		MY.C = C
	END

	' member operation
	DEF +SHOW
		?B$
	END

	' member function
	DEF +PLUS()
		 RETURN A + C
	END

	DEF +MINUS()
		 RETURN A - C
	END

	DEF +MULTIPLY()
		 RETURN A * C
	END
	
	DEF +DIVIDE()
		 RETURN A / C
	END
END

' instantiate my class
VAR OBJ = INIT MYCLASS(3, "yes", 2)

' call a member function
?OBJ.PLUS()
?OBJ.MINUS()
?OBJ.MULTIPLY()
?OBJ.DIVIDE()

' call a member operation
OBJ.SHOW

' exception handling
TRY
	' inline initialize
	?(INIT MYCLASS(3, "aaksasa", 2).PLUS())
CATCH EX
	?EX.MESSAGE
end

' define a group (same as namespace) named "sample"
GROUP SAMPLE
	CLASS +TEST
		+PROP A GETSET
		+PROP B GETSET
		INIT(A, B)
			MY.A = A : MY.B = B
		RNF

		+MOD()
			RETURN a % b
		END
	END
END

' initialize in-group class without 'use' statement
?INIT SAMPLE.TEST(7, 5).MOD()

' use a namespace
USE SAMPLE
?INIT TEST(5, 3).MOD()

' use a standard library
USE STD.COLLECTIONS

VAR A = INIT TEST()
A.ADD 44
A.ADD 55

?A[0]
?A[1]

VAR B = INIT LIST$()
B.ADD "hage"
B.ADD "neko"
B.ADD "inu"
B.REMOVE 1

?B[1]

' generic class
USE STD.COLLECTIONS.GENERIC
VAR C = INIT LIST:TEST()
C.ADD INIT TEST(5, 2)
C.ADD INIT TEST(8, 2)
```

# LICENSE

See [LICENSE](LICENSE).
