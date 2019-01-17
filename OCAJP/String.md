# Chapter 4: Selected classes from Java API and arrays

## Table of Contents

* [String](#String)

## String

* Class. Default value is null.
* Immutable => Once created, a string value can't be modified. String methods that return a modified String value returned a new String object with the modified value. Original String value remains the same.

### Ways of Creating String

1. keyword **new**. String objects created this way is never pooled.
2. assignment operator. new String object created only if a String object with same value isn't found in String constant pool.

``` java
String str1 = new String("Paul");
String str2 = new String("Paul");
System.out.println(str1 == str2); //false

StringBuilder sd1 = new StringBuilder("String Builder");
String str5 = new String(sd1);
StringBufffer sd1 = new StringBufffer("String Buffer");
String str6 = new String(sd2);

String str3 = "Harry";
String str4 = "Harry";
System.out.println(str3 == str4); //true

System.out.println("Morning");

//Total of 6 String objects created in this example
```

### Methods

> When chained, the methods are evaluated from left to right

#### charAt()

* Retrieve character at a specified index of String
* *runtime exception* if non-existent index

``` java
String letters = "ABCAB";
System.out.println(letters.charAt(3)); //'A'
```

#### indexOf()

* search for first matching position of char or String and return its index
* return -1 if no match
* By default, search from first char but you can also set starting position

``` java
String letters = "ABCAB";
System.out.println(letters.indexOf('B')); //-1
System.out.println(letters.indexOf("S")); //-1
System.out.println(letters.indexOf("CA")); //2
System.out.println(letters.indexOf('B',2)); //4
```

#### substring()

* return a substring of a String from the position specified to the end of String
* substring method doesn't include character at end position
  * Length of String returned by subString = end - start

``` java
String letters = "ABCAB";
System.out.println(letters.subString(2)); //"CAB"
System.out.println(letters.subString(1,3)); //"BC"
```

#### trim()

* return a new String by removing all leading and trailing *white space*(new lines,spaces or tabs) in a String
* method doesn't remove the space within a String

``` java
String letters = " AB CAB      ";
System.out.println(letters.trim()); //"AB CAB"
```

#### replace()

* return a new String by replacing all occurences of a char/String with another char/String

``` java
String letters = "ABCAB";
System.out.println(letters.replace('B','b')); // "AbCAb"
System.out.println(letters.replace("CA",12)); // "AB12b"
```

#### length()

* return length of String

``` java
System.out.println(letters.replace("Shreya".length)); // 5
```

#### startWith() and beginWidth()

* return a new String by replacing all occurences of a char/String with another char/String

``` java
String letters = "ABCAB";
System.out.println(letters.replace('B','b')); // "AbCAb"
System.out.println(letters.replace("CA",12)); // "AB12b"
```

### String objects and operators

* Concatenation: + and +=

``` java
String aString = 10 + 12 + "OCJA";
System.out.println(aString); // "22OCJA"

//treating numbers as String values
aString = "" + 10 + 12 + "OCJA";
System.out.println(aString); // "1012OCJA"
```

* Equality: == and !=; equals()

==  compares whether the reference variables refer to same objects, and method **equals** compares the String values for equality.  

``` java
String var1 = new String("Java");
String var2 = new String("Java");
System.out.println(var1 == var2); // false
System.out.println(var1.equals(var2)); // true

String var3 = "code";
String var4 = "code";
//var3 and var4 refer to the same String object created and shared in String pool
System.out.println(var3 == var4); // true
System.out.println(var1.equals(var4)); // true
```