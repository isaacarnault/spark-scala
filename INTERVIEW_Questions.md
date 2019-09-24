 # Spark - Scala
 
#### Questions - Set N°1
  
1.) What is 2 to the power of 5?

2.) What is the remainder of 180 divided by 7?

3.) Given variable pet_name = "Sammy", use string interpolation to print out
 "My dog's name is Sammy."

4.) Use scala to find out if the letter sequence "xyz" is contained in:
"sadfjshfjyuyxyzjkfuidkjklhasyysdfk"

5.) What is the difference between a value and a variable?

6.) Given the tuple (1,2,3,(4,5,6)) retrieve the number 6.

</p>
</details><br>
 
#### Solutions

1.) What is 2 to the power of 5?
```r
  scala> math.pow(2,5)
  res39: Double = 32.0
```
2.) What is the remainder of 180 divided by 7?
```r
  scala> 180%7
  res40: Int = 5
```
3.) Given variable pet_name = "Sammy", use string interpolation to print out
 "My dog's name is Sammy."
```r
  scala> s"My dog's name is ${pet_name}"
  res42: String = My dog's name is Sammy

  scala> f"My dog's name is $pet_name"
  res43: String = My dog's name is Sammy
```
4.) Use scala to find out if the letter sequence "xyz" is contained in:
"sadfjshfjyuyxyzjkfuidkjklhasyysdfk"
```r
  scala> val s = "sadfjshfjyuyxyzjkfuidkjklhasyysdfk"
  s: String = sadfjshfjyuyxyzjkfuidkjklhasyysdfk
```
```r
  scala> s contains "xyz"
  res45: Boolean = true
```
5.) What is the difference between a value and a variable?

A value is an immutable storage unit, it can be assigned data when defined but
can not be reassigned.<br>

A variable is a mutable storage unit, data can be assigned at definition and
reassigned later on.<br>

6.) Given the tuple (1,2,3,(4,5,6)) retrieve the number 6.
```r
  scala> val t = (1,2,3,(4,5,6))
  t: (Int, Int, Int, (Int, Int, Int)) = (1,2,3,(4,5,6))
```
```r
  scala> t._4
  res49: (Int, Int, Int) = (4,5,6)
```
```r
  scala> t._4._3
  res50: Int = 6
```
#### Questions - Set N°2

1.) Can you figure out what method you can use to find out if the list:
List(1,2,3,4,5) contains the number 3?

2.) How can you add all the elements of the previous list?

3.) Create an Array of all the odd numbers from 0 to 15

4.) What are the unique elements in the list: List(2,3,1,4,5,6,6,1,2)?

5.) Create a mutable map that maps together Names to Ages.
It should have the following key value pairs:<br>
Sammy, 3<br>
Frankie, 7<br>
John, 45

6.) Print out all the keys
Add the key value pair ("Mike",27)

#### Solutions

1.) Can you figure out what method you can use to find out if the list:
List(1,2,3,4,5) contains the number 3?
```r
scala> val li = List(1,2,3,4,5)
li: List[Int] = List(1, 2, 3, 4, 5)
```
```r
scala> li.contains(3)
res42: Boolean = true
```
2.) How can you add all the elements of the previous list?
```r
scala> li.sum
res43: Int = 15
```
3.) Create an Array of all the odd numbers from 0 to 15
```r
scala> val odds = Array.range(1,15,2)
odds: Array[Int] = Array(1, 3, 5, 7, 9, 11, 13)
```
4.) What are the unique elements in the list: List(2,3,1,4,5,6,6,1,2)?
```r
scala> val mylist = List(2,3,1,4,5,6,6,1,2)
mylist: List[Int] = List(2, 3, 1, 4, 5, 6, 6, 1, 2)
```
```r
scala> mylist.toSet
res68: scala.collection.immutable.Set[Int] = Set(5, 1, 6, 2, 3, 4)
```
5.) Create a mutable map that maps together Names to Ages.
 > It should have the following key value pairs
```r
Sammy, 3
Frankie, 7
John, 45
```
```r
scala> val names = collection.mutable.Map(("Sammy",3),("Frankie",7),("Joh
n",45))
names: scala.collection.mutable.Map[String,Int] = Map(Sammy -> 3, Frankie
 -> 7, John -> 45)
```
6.) Print out all the keys
```r
scala> names.keys
res44: Iterable[String] = Set(Sammy, Frankie, John)
```
 > Add the key value pair ("Mike",27)
```r
scala> names += ("Mike"->27)
res46: names.type = Map(Sammy -> 3, Mike -> 27, Frankie -> 7, John -> 45)
```
