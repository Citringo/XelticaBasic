# XelticaBasic

XelticaBasic is an implementation of the BASIC language.

## Sample Code

```bas

' Hello World
print "Hello, world!"

' Expression
a = 3 + 5
b = 3 + 4
c = a + b

' Combine string
s$ = a + " + " + b + " = " + c
print s$

' Input
t = val(scan("数値> "))

' Inline If
if t < 5 then ?"tは5未満です" else ?"tは5以上です"

' Block Style If
if t < 6 then
	?"tは6未満"
elseif t < 10 then
	?"tは6以上10未満"
else
	?"tは10以上"
endif

' Switch
switch t
	case 0
		?"tは0"
	case 1
		?"tは1"
	case 2
		?"tは2"
	case 3
		?"tは3"
	default
		?"tは0, 1, 2, 3以外"
endswitch

' Define a func

def saysaysay text$

'for statement
	for i = 0 to 10
		?text$
	next

end

saysaysay "ピザ"

' Define an array
dim arr[10]
for i = 0 to 9
	arr[i] = (i + 4)  % 10
next

' Define an array 2
arr2 = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

' Define a struct
struct vec2
	var x
	var y
end

' Use a struct variable

dim v:vec2
v.x = 10
v.y = 20

// syntax sugar
v2:vec2 = [10, 20]

// Both these are same
value = 3
value:num = 3

text$ = "aa"
text:str = "aa"
```

# LICENSE

See [LICENSE](LICENSE).
