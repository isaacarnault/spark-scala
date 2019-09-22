#### for loops

```r
// Looping an integer

for(item <- List(1,2,3)){
  println(item)
}
```
```r
// Looping an array

for(item <- Array.range(0,5)){
  println(item)
}

```r
// Looping a set

for(item <- Set(2,4,9,1,3)){
  println(item)
}
```
```r
// Looping with If Else

// for loop and else if script

for(num <- Range(0,10)){
  if(num%2 == 0){
    println(s"$num is even")
  }else{
    println(s"$num is odd")
  }
}
```
```r
// Looping from a list and retrieving one or more results

val names = List("Beerus", "Champa", "Karin", "Kaio", "Dende", "Dodoria")

for(name <- names){
  if(name.startsWith("D")){
    println(s"$name starts with a D")
  }
}
```
