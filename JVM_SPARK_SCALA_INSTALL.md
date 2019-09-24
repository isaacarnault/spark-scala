We'll perform the installation on Linux. <br>
I performed this setup on my `Ubuntu 18.04.2 LTS`.<br>
To check your OS version, execute `$ lsb_release -a` in your Terminal.

### 1. Installation of JVM, Spark, Scala on a Linux System

`Ctrl + Alt + t`: to open a new `Terminal` on your `Linux` OS. I am using `Ubuntu 18.04 LTS` 

## Java
```sh
$ sudo apt update  
$ sudo apt install oracle-java8-installer  
$ sudo apt install oracle-java8-set-default  
```
To make sure `Java` is correctly installed, use `$ java -version` in your Command Line Interface. <br>
If you already have `Java` installed, you can bypass this step.<br>

<details>
<summary>🔴 See output</summary>
<p> 
  
[![4.png](https://i.postimg.cc/9fKbYWbn/4.png)](https://postimg.cc/kVNWnPkQ)

</p>
</details>

## scala
```r
$ sudo apt-get remove scala-library scala  
$ sudo apt-get update  
$ sudo apt-get install scala
```

To make sure `Scala` is correctly installed  use `$ scala` in your Command Line Interface. <br>
If you already have `Scala` installed, you can bypass this step.<br>

<details>
<summary>🔴 See output</summary>
<p> 
  
[![3.png](https://i.postimg.cc/3NgtwPgb/3.png)](https://postimg.cc/YLC6nDD1)

</p>
</details>

## spark
```r
$ sudo apt-get install git '''use "y + entrer" when prompted by the Command Line Interface'''
Go to : https://spak.apache.org > Download > Step3: Download Spark (click to download the .tgz file)<br>
You can also download the Spark package directly at https://bit.ly/2KYLLZQ
$ cd Desktop : to go to your Desktop<br>
$ sudo mkdir spark : to create a folder named spark<br>
$ cd Downloads : to go to your Downloads folder
$ tar -xvf spark-2.4.3-bin-hadoop2.7.tgz : to extract the package
$ sudo mv spark-2.4.3-bin-hadoop2.7 */Desktop/spark
Verify that your spark folder was moved correctly
$ sudo mv spark-2.4.3-bin-hadoop2.7 */Desktop/spark
$ cd Desktop/spark
$ ls
```

<details>
<summary>🔴 See output</summary>
<p> 
  
[![11.png](https://i.postimg.cc/qR5BX8k8/11.png)](https://postimg.cc/hzVqKQQj)

</p>
</details>

We can now start using `Spark`:<br>
. `$ cd Desktop/spark/bin`
. `$ ./spark-shell`

<details>
<summary>🔴 See output</summary>
<p> 
  
[![12.png](https://i.postimg.cc/brSy6sJ4/12.png)](https://postimg.cc/0Kx1j57C)

</p>
</details>

## atom text editor - installation

Go to https://atom.io/ > Click on "download .deb" to get the `Debian` package.<br>
Once downloaded, right click the package and select "Open with Software install", then click on "Install.

<details>
<summary>🔴 See output</summary>
<p> 
  
[![atom.png](https://i.postimg.cc/JnsyZjnF/atom.png)](https://postimg.cc/ZBhKhB6P)

</p>
</details>

Click on the `Atom` icon on your Applications to start it.<br>

Then cick on  "Install a Package"<br>

Install <b>language-scala</b> package.

<details>
<summary>🔴 See output</summary>
<p> 
  
[![atom-install.png](https://i.postimg.cc/3J4BYDFn/atom-install.png)](https://postimg.cc/xcQHP87z)

</p>
</details>

Then search for "terminal" in the search bar of `Atom`.<br>

Select "atom-ide-terminal" and proceed to installation.<br>

Once both packages are installed, click on the cross "+" to open a new `Terminal`.<br>

Now, we are ready to write your first scala script. Click on File > New File<br>

To check if everything works fine, type the following script:<br>

`println ("Hello Scala!")`. Note that saving the file to "one_script.scala" will make it interpretable by `Scala`.<br>

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-3.png](https://i.postimg.cc/zv35v1zZ/isaac-arnault-scala-3.png)](https://postimg.cc/XBMt1mBQ)

</p>
</details>

We will save <b>one_script.scala</b> file in a directory on our Desktop which we'll name "scala".<br>

At this point, we should have two directories "spark" and "scala" on our Desktop.<br>

<hr>

<b>Execute a `Scala` script from your `Atom` terminal<br>

To make our `Scala` script executable by `Spark` on `Atom`, we should first launch `Spark` in our `Atom` Terminal:

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-4.png](https://i.postimg.cc/RC3ZvcN3/isaac-arnault-scala-4.png)](https://postimg.cc/grWWDLyd)

</p>
</details>

Then let's try to launch our script from the Terminal. Use the following command:<br>

`scala > load: filepath/one_script.scala`<br>

<details>
<summary>🔴 See output</summary>
<p> 
  
[![isaac-arnault-scala-5.png](https://i.postimg.cc/h4M6ZwST/isaac-arnault-scala-5.png)](https://postimg.cc/CdBczcnx)

</p>
</details>
