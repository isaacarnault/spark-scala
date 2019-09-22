#### Simple if_else statement
a.) Create a ifelse.scala file in ```Atom```<br>
b.) launch your spark session ```:load```<br>
c.) ```:load``` your file with the following command: ```// load: url-path/ifelse.scala```


1.) COMPARISON operators - one condition
else if script 1
```r
val x = "goku"

if(x.endsWith("b")){
  println("value of x ends with b")
}else{
  println("value of x does not end with b")
}
```
else if script 2
```r
val person = "Champa"

if(person == "Beerus"){
  println("Your Majesty Beerus, this is your bento!")
}else{
  println("You can't have a bento, sorry!")
}
```

2.) LOGICAL operators - multiple conditions
else if script 3

AND operator - if both conditions are true, program will return "true", if not it will return "false"
```r
println((1 == 2) && (2 == 2)) // && means "AND"
```
```r
println((4 == 4) && ("b" == "b"))
```
OR operator - if one of both conditions is true, program will return "true", if not it will return "false"
```r
println((4 == 3) || ("e" == "e")) // "||" means "OR"
```
NOT operator - if condition is not "true", program will return "false"
```r
print(!(1 == 1)) // "!" biaises the results and program returns "false" in that case
```
