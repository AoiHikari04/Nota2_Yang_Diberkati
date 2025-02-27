
# Introduction to GO

**Six Main Point of GO**
- Statically Typed Language
- Strongly Typed Language 
- Compiled Language
- Fast Compile Time
- Built in Concurrency
- Simplicity

---
**Setting up GO Installation**

1. Download Installer from the website
2. install the language
![[Pasted image 20250224163328.png]]
ez dek

---
**Modules And Packages**

Module :
- Is the whole set of files/packages
- Contain the version
- Contain all the dependency

Packages:
- Contain the coding
- Use to actually run the code yeh
---
**Initialising the workspace**

1. in empty directory, create .go files
2. optional, but create module files using command

```
go mod init <githubRepo>
```

3. Now can start Coding

---
# Constant variables and Basic Data Types


**Integer**
```go
var intNum int
var intNum int16 / int32 / int64
var intNum uint // unsigned Number, Only positive
```

**Float**
```go
var floatNum float64 / float32 // need to specify which float
var floatNum float32 = 12345678.9
fmt.println(floatNum) >>> 123456789.000000 // wrong number need float64 to precise
```

**Arithmetic**
- Cant add two different data types together, 
```go
var floatnum32 float32 = 10.2
var intNum32 int32 = 2
var result float32 = floatNum32 + intNum32 xxxx // xboleh cuk
var result float32 = floatNum32 + float32(intNum32) //baru bleh
```

**String**
- Use "" or \`\` untuk String bukan ''
- yare yare nanora
- "" only one line of string
- \`\` can multiple line of string
```go
var myString string = "Hello!! gaes" // only one line
var myString string = `Eiyooo
						opo ko bongak sangat ni` // can cover multiple line

fmt.Println(len("test")) >> //4 tapi ni nilai byte bukan ril
fmt.Println(utf8.RuneCountInString("test")) >> //ril
```

**Bool**
- same stuff as others lol
- Default value is false

**Miscellaneous**
```go
myVar := "Text" // ril shortcut
var1, var2 := 1, 2 //multiple data at the same time
```

**Constant**
- All other properties same as other, just change var to const
- need to initiliase at code time
```go
const myConst String = "ConstValue"
```

---
# Function and Control Structure
- Creating function and returning value
```go 
func printString(InputString string){
	fmt.Println(InputString)
}

func intDivision(numerator int, denumerator int) (int, int, error){
	var err error
	if denominator == 0{
		err = errors.New("Error bang")
		return 0,0,err
	}
	var result int = numerator/denumerator
	var lebihan int = numerator%denumerator
	return result, lebihan, err
}
```
- the corresponding main function
```go
package main

import (
	"errors"
	"fmt"
)

func main(){
	var printValue string = "Hello Gaesek"
	printString(printValue)
	
	var numerator = 11
	var denominator = 0
	var result, lebihan, err = intDivision(numerator, denominator)
	
	// if statement
	if err!=nil{
		fmt.printf(err.Error())
	} else if remainder == 0{
		fmt.printf("The results of the integer division is %v", result) 
	} else {
		fmt.printf("The results of the integer division is %v with remainder %v", result, remainder) 
	}

	// Switch statements ver 1
	switch {
		case err!=nil:
			fmt.Printf(err.Error())
		case remainder == 0:
			fmt.printf("The results of the integer division is %v", result) 
		default:
			fmt.printf("The results of the integer division is %v with remainder %v", result, remainder) 
	}

	// conditional switch statement
	switch remainder{
		case 0:
			fmt.printf("Division was exact")
		case 1,2:
			fmt.printf("Division was close")
		default:
			fmt.printf("Division was not close")
	}
	
	// fmt.printf("The results of the integer division is %v with remainder %v", result, remainder) 

	
	

}

```

---
# Arrays, Slices, Maps, Loops

**\[ ] Arrays**
- Fixed Length
- Same type
- Indexable
- Contiguous in Memory >> sebelah2 dlm memory

```go
var intArr [3]int32 = [3]int32{1,2,3}
intArr := [3]int32{1,2,3} // ril shortcut
intArr := [...]int32{1,,2,3} //kena initiliase siap2
```

**Slices**
- According to the original documentation, slices is just wrappers for arrays
- Array List in a nutshell lol, length will double if not enough lol
```go
var intslice []int32 = []int32{4,5,6}
fmt.printf("the length is %v with capacity of %v", len(intSlice), cap(intSlice))

intSlice = append(intSlice,7)

fmt.printf("the length is %v with capacity of %v", len(intSlice), cap(intSlice))

SliceLength := 3
SliceCapacity := 8
var intSlice2 []int32 = make(int32[], SliceLength, SliceCapacity)

```

**Map**
- Key and value pair, looking up  the value with key
- Will always return a value even if there is no key matched
```go
var myMap map[string]uint8 = make(map[string]uint8)

var myMap2 = map[string]uint8{"Adam":28, "Sarah"33}

var age, inTheMap = myMap2["Jason"]

if inTheMap{
	fmt.printf("The age is %v", age)
}else{
	fmt.Printf("Invalid Name")
}

delete(myMap2, "Adam") //to delete items


```

**Loops**
- only have for loops, but enough to cover all types of loops
- while iterating through maps, the sequence are **not** the same every run
```go

//through maps
for name, age := range myMaps2{
fmt.printf("Name: %v, Age: %v", name, age)
}

// trough array
for i, v := range intArr{
	fmt.printf("Index: %v, Value: %v \n", i, v)
}

for i:=0; i<10;i++ {
	fmt.Println(i)
}

for {
	if i >= 10{
		break
	}
	fmt.Println(i)
	i = i + 1
}

var i int = 0
for i < 10 {
	fmt.Println(i)
	i = i + 1
}

```

# String, Runes and Bytes

**String**
- can be indexed like an array
- Cant be changed after created, if changed, it allocate new memory address for the string, essentially creating a new string
- thus changing the string at memory level is not able
- **Notes:** Use string builder to concatenate a string for a more efficient method
```go
var MyString = "Resume"
var indexed = MyString[0] >> R
```

**Runes**
- Unicode numbers that represent strings
- int32

---
# Struct and Interfaces

**Struct**
- Defining your own types, ie integer, float, boolean
```go

type owner struct{
	name string
}

type gasEngine struct{
	MilesPerGallon uint8
	Gallons uint8
	ownerInfo owner
}

func main(){

	var myEngine gasEngine = gasEngine{MilesPerGallon: 25, Gallons: 5, owner{"Alex"}}

	//Also can do, not reusable
	var myEngine2 = struct{
		mpg uint8
		gallons uint8
	}{25,15}

}
```

**Interfaces**
- An interface that combine structs' function
- if two structs contain the same function, can use interface to combine it and use in other function easily
```go
type gasEngine struct{
	mpg uint8
	gallons uint8

}

type electricEngine struct{
	mpkwh uint
	kilowatt uint8
}

func (e gasEngine) milesLeft() uint8 {
	return e.mpg * e.gallons
}

func (e electricEngine) milesLeft() uint8 {
	return e.mpkwh * e.kilowatt
}

/*
gas Engine and electric engine both have milesLeft function
lets say want to create a function where both structs want to be used, but only want to create one func, interface helped combine this both structs
*/

type engine interface {
	milesLeft() uint8
}

//e only use interface instead of making it for both structs
func canMakeIt(e engine, miles uint8){ 

	if miles <= e.milesLeft(){
		//print you can make it
	} else {
		//print you cant make it
	}

}
```

---
# Pointers

- Stores memory location rather than value
- use * syntax
- The person writing this already what pointer is, lol, get rekt
- uses most in slices -> slices is just pointer
	- if copy slice to another
	- changing the original slice will also change the copied one
	- cuz copied slice also points to the same address of the original slice
- tldr of the video: 
	- pointer is pointing to another place that holds the values
	- * at pointer to devalue the pointer
	- & at variable to show the address
	
```go
//declaring
var p *int32 = new (int32)

//declaring 2
var i int32
var p = &i

```