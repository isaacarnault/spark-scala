## Entry level in Spark-Scala using Atom (text editor)

You can try the following commands in your `Atom` Terminal. Make sure `Spark` is launched priorly.<br>

<b>Your first Scala script</b>
  
```r
scala> printf("%s is a string, %d is an integer, %f is a float", "Hello Scala!", 12, 34.254)
```

#### 1. Arithmetic and Numbers

# Two types of Numbers:
1. Integers (Whole)
```r
scala> 100
res0: Int = 100
```
2. Doubles (Floating Point)
```r
scala> 2.5
res1: Double = 2.5
```
# Operations in Scala
Addition
```r
scala> 1 + 1
res2: Int = 2
```
Subtraction
```r
scala> 2 - 1
res3: Int = 1
```
```r
Multiplication
scala> 2 * 5
res4: Int = 10
```

Division with Integers (Classic)
```r
scala> 1 / 2
res5: Int = 0
```

Division with Doubles (True)
```r
scala> 1.0/2
res6: Double = 0.5
```
```r
scala> 1/2.0
res7: Double = 0.5
```
Exponents
```r
scala> math.pow(4,2)
res36: Double = 16.0
```
Modulo (Remainder)
```r
scala> 10 % 4
res8: Int = 2

scala> 9 % 4
res9: Int = 1
```
You can call back results
```r
scala> res0
res10: Int = 100
```
Order of Operations with Parenthesis
```r
scala> (1 + 2) * (3 + 4)
res11: Int = 21

scala> 1 + 2 * 3 + 4
res12: Int = 11
```
Convert 3 feet to meters using scala
```r
scala> 3 * 0.3048
res13: Double = 0.9144000000000001
```
#### 2. Booleans and Compariton operators

```r
scala> true
res21: Boolean = true
```
```r
scala> false
res22: Boolean = false
```
```r
scala> 1 > 2
res23: Boolean = false
```
```r
scala> 2 < 1
res24: Boolean = false
```
```r
scala> 3 >= 1
res27: Boolean = true
```
```r
scala> 3 <= 3
res28: Boolean = true
```
```r
scala> 2 == 1
res25: Boolean = false
```
```r
scala> 2 != 1
res26: Boolean = true
```

# 3. Strings and RegEx (Regular Expressions)  

Printing
```r
scala> println("hello")
hello
```
Concatenation
```r
scala> val fairwell = "Good" + "Bye"
fairwell: String = GoodBye
```
Repeating
```r
scala> val repeat = "Dance!"*5
repeat: String = Dance!Dance!Dance!Dance!Dance!
```
String Length
```r
scala> val st = "hello"
st: String = hello
scala> st.length()
res14: Int = 5
```
Inserting Objects
```r
scala> val name = "Jose"
name: String = Jose
```
```r
String Interploation
scala> val greet = s"Hello ${name}"
greet: String = Hello Jose
```
printf
```r
scala> printf("A string: %s , an integer %d, a float %f","hi",10,2.5)
A string: hi , an integer 10, a float 2.500000
```
```r
scala> printf("A string: %s , an integer %d, a float %1.2f","hi",10,2.5)
A string: hi , an integer 10, a float 2.50
```
'f' Interploation
```r
scala> val greet = f"Hello ${name}"
greet: String = Hello Jose
```
```r
scala> val greet = f"Hello $name"
greet: String = Hello Jose
```
String Indexing
```r
scala> f"First letter of name is $name%.1s"
res8: String = First letter of name is J
```

// Regular Expressions 

Index Location
```r
scala> val st = "This is a long string"
st: String = This is a long string
```
```r
scala> st.charAt(0)
res18: Char = T
```
```r
scala> st.indexOf("a")
res19: Int = 8
```
Pattern matching
```r
scala> val st = "term1 term2 term3"
st: String = term1 term2 term3
```
```r
scala> st contains "term1"
res20: Boolean = true
```
```r
scala> st matches "term1"
res11: Boolean = false
```
```r
scala> st matches "term1 term2 term3"
res12: Boolean = true
```
Slicing
```r
scala> val st = "hello"
st: String = hello
```
```r
scala> st slice (0,2)
res2: String = he
```
```r
scala> st slice (2,st.length)
res4: String = llo
```

# 4. Tuples

An ordered sequence of values can be of multiple data types
```r
scala> val my_tup = (1,2,"hello",23.2,true)
my_tup: (Int, Int, String, Double, Boolean) = (1,2,hello,23.2,true)
```
Can also be nested
```r
scala> (3,1,(2,3))
res46: (Int, Int, (Int, Int)) = (3,1,(2,3))
```
Accessing elements with ._n notation<br>
Indexing starts at 1
```r
scala> val greeting = my_tup._3
greeting: String = hello
```
```r
scala> my_tup._1
res37: Int = 1
```

# 5. Values and variables

General Format
```r
val <name>: <type> = <literal>
var <name>: <type> = <literal>
```
var or val determines whether it is a variable or a value.<br>
Values (val) are Immutable.<br>
Variables (var) can be reassigned.<br>
```r
scala> var myvar: Int = 10
myvar: Int = 10
```
```r
scala> val myval: Double = 2.5
myval: Double = 2.5
```
Reassignments
```r
Fails for different data type
scala> myvar = "hello"
<console>:12: error: type mismatch;
 found   : String("hello")
 required: Int
       myvar = "hello"
```
Works for same data type and being a var
```r
scala> myvar = 200
myvar: Int = 200
```
Values can not be reassigned!
```r
scala> myval = 2.5
<console>:12: error: reassignment to val
       myval = 2.5
```
Creating variables and values without types:
```r
Scala can infer data types
scala> val c = 12
c: Int = 12
```
```r
scala> val s = "my string"
s: String = my string
```
Valid Names
```r
scala> val my_string = "Hello"
my_string: String = Hello
```
Not Recommended, but possible
```r
scala> val `my.string` = "hello"
my.string: String = hello
```
InValid Names
```r
scala> val 2strings = "hello hello"
<console >:1: error: Invalid literal number
val 2strings = "hello hello"
```
```r
scala> val my.string = "hello"
<console>:11: error: not found: value my
       val my.string = "hello"
```

# 6. Arrays

Collection of variables<br>

Should I use a list or an array?<br>
What is the difference?<br>
Resource link:<br>
http://stackoverflow.com/questions/2712877/difference-between-array-and-list-in-scala
<br>

#### Examples
  
```r
scala> val arr = Array(1,2,3)
arr: Array[Int] = Array(1, 2, 3)
```
```r
scala> val arr = Array("a","b","c")
arr: Array[String] = Array(a, b, c)
```
<b>Range</b>
Use of range() method to generate an array containing
a sequence of increasing integers in a given range.<br>
```r
scala> Array.range(0,10)
res64: Array[Int] = Array(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```
```r
scala> Array.range(0,10,2)
res65: Array[Int] = Array(0, 2, 4, 6, 8)
```
Or just call Range with a capital R
```r
scala> Range(0,5)
res1: scala.collection.immutable.Range = Range(0, 1, 2, 3, 4)
```
```r
scala> Range(0,10,2)
res2: scala.collection.immutable.Range = Range(0, 2, 4, 6, 8) 
```

# 7. Lists
Lists are an immutable sequence of elements<br>
```r
Basic List of Numbers
scala> val evens = List(2,4,6,8,10,12)
evens: List[Int] = List(2, 4, 6, 8, 10, 12)
```
Indexing Items (Starts at zero)
```r
scala> evens(0)
res0: Int = 2
```
```r
scala> evens(1)
res1: Int = 4
```
Head and Tail
```r
scala> evens.head
res3: Int = 2
```
```r
scala> evens.tail
res4: List[Int] = List(4, 6, 8, 10, 12)
```
```r
scala> evens
res5: List[Int] = List(2, 4, 6, 8, 10, 12)
```
Element Types<br>
Any
```r
scala> val my_list = List("a",2,true)
my_list: List[Any] = List(a, 2, true)
```
Nested
```r
scala> val my_list = List(List(1,2,3),List(4,5,6))
my_list: List[List[Int]] = List(List(1, 2, 3), List(4, 5, 6))
```
Double and Int
```r
scala> val my_list = List(1,2,3.0)
my_list: List[Double] = List(1.0, 2.0, 3.0)
```
List of Tuple Pairs
```r
scala> val my_list = List(("a",1),("b",2),("c",3))
my_list: List[(String, Int)] = List((a,1), (b,2), (c,3))
```
List Operations
```r
scala> val my_list = List(3,6,1,7,10)
my_list: List[Int] = List(3, 6, 1, 7, 10)
```
```r
scala> my_list.sorted
res7: List[Int] = List(1, 3, 6, 7, 10)
```
```r
scala> my_list.size
res8: Int = 5
```
```r
scala> my_list.max
res9: Int = 10
```
```r
scala> my_list.min
res39: Int = 1
```
```r
scala> my_list.sum
res40: Int = 27
```
```r
scala> my_list.product
res41: Int = 1260
```
Using drop for slicing<br>
```r
scala> val x = List(1,2,3,4)
x: List[Int] = List(1, 2, 3, 4)
```
```r
scala> x.drop(2)
res3: List[Int] = List(3, 4)
```
```r
scala> x.takeRight(3)
res4: List[Int] = List(2, 3, 4)
// Use Tab to explore the other methods.
```
# 8. Maps  
(Key,Value) Pair Storage aka Hash Table or Dictionary

```r
scala> val mymap = Map(("a",1),("b",2),("c",3))
mymap: scala.collection.immutable.Map[String,Int] = Map(a -> 1, b -> 2, c
 -> 3)
```
Lookups
```r
scala> mymap("a")
res12: Int = 1
```
None if not present
```r
scala> mymap get "b"
res15: Option[Int] = Some(2)
```
Temp additions on immutable
```r
scala> mymap + ("z"->99)
res19: scala.collection.immutable.Map[String,Int] = Map(a -> 1, b -> 2, c
 -> 3, z -> 99)
```
Mutable maps
```r
scala> val mymutmap = collection.mutable.Map(("x",1),("y",2),("z",3))
mymutmap: scala.collection.mutable.Map[String,Int] = Map(z -> 3, y -> 2,
x -> 1)
```
Permanent Additions
```r
scala> mymutmap += ("new"->999)
res29: mymutmap.type = Map(z -> 3, y -> 2, x -> 1, new -> 999)
```
scala> mymutmap
```r
res30: scala.collection.mutable.Map[String,Int] = Map(z -> 3, y -> 2, x -
> 1, new -> 999)
```
A few useful methods
```r
scala> mymap.keys
res34: Iterable[String] = Set(a, b, c)
```
```r
scala> mymap.values
res35: Iterable[Int] = MapLike(1, 2, 3)
```
# 9. Sets  
Set is a collection that contains no duplicate elements.<br>
There are two kinds of Sets, the immutable and the mutable.<br>
Examples
```r
scala> val s = Set()
s: scala.collection.immutable.Set[Nothing] = Set()
```
```r
scala> val s = Set(1,2,3)
s: scala.collection.immutable.Set[Int] = Set(1, 2, 3)
```
```r
scala> val s = Set(1,1,2,2,2,3,3,3)
s: scala.collection.immutable.Set[Int] = Set(1, 2, 3)
```
Mutable Sets
```r
scala> val s = collection.mutable.Set(1,2,3)
s: scala.collection.mutable.Set[Int] = Set(1, 2, 3)
```
```r
scala> s += 4
res50: s.type = Set(1, 2, 3, 4)
```
```r
scala> s
res51: scala.collection.mutable.Set[Int] = Set(1, 2, 3, 4)
```
```r
scala> s.add(5)
res52: Boolean = true
```
```r
scala> s
res53: scala.collection.mutable.Set[Int] = Set(1, 5, 2, 3, 4)
```
Set Operations
```r
scala> s.max
res54: Int = 5
```
```r
scala> s.min
res55: Int = 1
```
Cast to Set
```r
scala> val mylist = List(1,2,3,1,2,3)
mylist: List[Int] = List(1, 2, 3, 1, 2, 3)
```
```r
scala> mylist.toSet
res59: scala.collection.immutable.Set[Int] = Set(1, 2, 3)
```

# 10. Loops  
##### For loops

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
##### While loops
```r
// Looping with a variable 

var x = 0

while(x < 5){ // boolean condition
  println(s"x is currenly $x")
  println("x is still less than 5, adding 1 to x")
  x = x+1 // adding 1 to x and iterating until we reach 5
  println(s"x is currenly $x")
}
```

#### 11. if else
a.) Create a ifelse.scala file in ```Atom```<br>
b.) launch your spark session ```:load```<br>
c.) ```:load``` your file with the following command: ```// load: url-path/ifelse.scala```


  > 1. COMPARISON operators - one condition
```r
// if else - script 1
val x = "goku"

if(x.endsWith("b")){
  println("value of x ends with b")
}else{
  println("value of x does not end with b")
}
```

```r
// if else - script 2
val person = "Champa"

if(person == "Beerus"){
  println("Your Majesty Beerus, this is your bento!")
}else{
  println("You can't have a bento, sorry!")
}
```

  > 2. LOGICAL operators - multiple conditions

```r
// if else - script 3
// AND operator - if both conditions are true, program will return "true", if not it will return "false"

println((1 == 2) && (2 == 2)) // && means "AND"
```

```r
println((4 == 4) && ("b" == "b"))
```

```r
// OR operator - if one of both conditions is true, program will return "true", if not it will return "false"
println((4 == 3) || ("e" == "e")) // "||" means "OR"
```

```r
// NOT operator - if condition is not "true", program will return "false"
print(!(1 == 1)) // "!" biaises the results and program returns "false" in that case
```

#### 12. Other commands you can try
#### Reverse object

```r
object Reverse {
    def apply (s: String): String =
    s.reverse
}
```
```r
Reverse("Kiara")
```
<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala1.png](https://i.postimg.cc/N018f4QN/isaac-arnault-scala1.png)](https://postimg.cc/Z95vw6B3)

</p>
</details>

#### Arrays
```r
Array (1, 2, 3, 4, 5, 6, 7, 8, 9)
```
```r
res0(2)
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala2.png](https://i.postimg.cc/wjNL0VR6/isaac-arnault-scala2.png)](https://postimg.cc/dhqh0G9X)

</p>
</details>

#### hashCode

```r
case class Time(hours: Int = 0, minutes: Int = 0)
```
```r
Time (9, 45).hashCode()
```
<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-3.png](https://i.postimg.cc/65kG2vjF/isaac-arnault-scala-3.png)](https://postimg.cc/VdFN2dcF)

</p>
</details>

#### flatMap

```r
List ("Goten", "Trunks", "Gotenks")
```
```r
res0.map(lang => lang + "#")
```
```r
res0.flatMap (lang => lang + "#")
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala4.png](https://i.postimg.cc/fRQJThkN/isaac-arnault-scala4.png)](https://postimg.cc/SJVyD3WT)

</p>
</details>

#### filter

```r
List ("Goku", "Vegeta", "Broly", "Freezer")
```
```r
res0.filter(lang => lang.contains("e"))
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-5.png](https://i.postimg.cc/8C1cMBhX/isaac-arnault-scala-5.png)](https://postimg.cc/qN5pdKD2)

</p>
</details>

#### reduce

```r
1 to 10
```
```r
res0.reduce(_+_)
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-6.png](https://i.postimg.cc/261ZL7YR/isaac-arnault-scala-6.png)](https://postimg.cc/S2psw8jD)

</p>
</details>

#### fold, foldLeft, foldRight

```r
1 to 6
```
```r
res0.product
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-7.png](https://i.postimg.cc/yxXYDDDC/isaac-arnault-scala-7.png)](https://postimg.cc/7JhycY1K)

</p>
</details>

#### exists

```r
1 to 18
```
```r
res0.exists(num => num == 12)
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-7.png](https://i.postimg.cc/yxXYDDDC/isaac-arnault-scala-7.png)](https://postimg.cc/7JhycY1K)

</p>
</details>

#### copy
```r
val fighter1 = K9("Trunks", "Goten Trunks Fusion")
fighter1
```
```r
val fighter2 = fighter1.copy()
fighter2
```
```r
fighter1 == fighter2
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-9.png](https://i.postimg.cc/KvnDbT2c/isaac-arnault-scala-9.png)](https://postimg.cc/Wh1k6hzx)

</p>
</details>
