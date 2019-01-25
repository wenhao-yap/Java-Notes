# Chapter 5: Flow Control <!-- omit in toc -->

[Back to Home](../Readme.md)

## Tables of Content <!-- omit in toc -->

- [if, if-else statements](#if-if-else-statements)
  - [ternary constructs](#ternary-constructs)
  - [Compilation errors](#compilation-errors)
- [switch statement](#switch-statement)
  - [Comparison with if construct](#comparison-with-if-construct)
- [for loop](#for-loop)
  - [enhanced for loop](#enhanced-for-loop)
    - [Limitations](#limitations)
- [while and do-while](#while-and-do-while)
  - [while vs for](#while-vs-for)
- [Others](#others)
  - [break and continue](#break-and-continue)
  - [Labeled statements](#labeled-statements)

## if, if-else statements

- Can skip *else* code block but not *if*
- if there are no braces, will only execute a single line of code that follows the construct

``` java
if(name.equals("Lion")){
  score = 200;
} else if(name.equals("Cow")){
  score = 100;
}
```

### ternary constructs

``` java
int score = name.equals("Lion") ? 200 : 100;
```

### Compilation errors

``` java
// ternary can't drop its else part
int discount = (bill>2000)?15;
// Not a statement
(5000>2000) ? 15:10;
// can't include code blocks
int discount = (bill>2000)?{bill-150};{bill-100};
//Integer can't be assigned to Long and versa
long bill = 2000;
int discount = (bill>2000)?bill-100:bill-50;
```

## switch statement

- null isn't allowed as case label
- `default` : to execute if no matching case found
- Doesn't accept arguments of type long, float, double,or any object besides String.
- For nonprimitive types, that is String and wrapper types, switch argument must not be null, which would cause NullPointerException to be thrown.
- in absence of **break**, control will fall through remaining code and execute remaining cases if matches

``` java
int marks = 20;
switch(marks){
  case 10: System.out.println(10);
          break;
  case 10: System.out.println(30);
          break;
  default: System.out.println("default");
          break;
}
```

### Comparison with if construct

||if|switch|
|-|-|-|
|evaluation|evaluates all conditions until match found|compare argument with its labels|
|arguments|char, byte, short, int, String, enum, Character, Byte, Integer, Short|boolean|

## for loop

- Initialization,termination condition,update clause are optional.
- Missing termination implies infinite loop
- nested loop executes all iterations for each single iteration of its immediate outer loop

``` java
for(int i=0;i<5;i++){
  System.out.println(i);
}

//this is a valid code
for(;;)
  System.out.println(1);
```

### enhanced for loop

- Use for-each loop to iterate over arrays and collections.
- Don't used it to initialize,modify, or filter them

``` java
for(String val : myList){
  System.out.println(val);
}
```

#### Limitations

- can't be used to initialize an array and modify its elements
- can't be used to remove elements of collection i.e. hides iterator. can't call remove()
- can't be used to iterate over multiple collections or arrays in same loop

## while and do-while

``` java
//code executes once even if initial condition is false
do {
  //code
} while (condition is true);

//code never executes if initial condition is false
while(condition is true){
  //code
}
```

||while|do-while|
|-|-|-|
|condition|check before statements execution|check after statements execution|
|semicolon||require at the end|

### while vs for

- for: used when you know number of iterations
- while: do not know number of iterations and when number of iterations depends on a condition being true

## Others

### break and continue

- `break` : exit or break out of for, for-each, do and do-while, switch
- `continue` : skip remaining steps in current iteration and start with the next iteration

### Labeled statements

- Use label sparingly and only if they seem to increase code readability
- Can add labels to following statements:
  - code block defined using {}
  - looping statements
  - condition constructs
  - expressions
  - assignments
  - return statements
  - try blocks
  - throw statements
  
``` java
String[] programmers = {"Outer","Inner"};
outer:
for(String outer:programmers){
  for(String inner:programmers){
    if(inner.equals("Inner"))
      //exits the outer loop marked with label outer
      break outer;
  }
}
```