# 基礎

* [1.字符串](#字符串)
* [2.錯誤](#錯誤)
* [3.常數](#常數)
* [4.枚舉](#枚舉)
* [5.Array](#Array)
* [6.Slice](#Slice)
* [7.Map](#Map)
* [8.New](#New)
* [9.If Else](#If_Else)
* [10.Goto](#Goto)
* [11.For](#For)
* [12.Switch](#Switch)
* [13.函數](#函數)
* [14.可變參數函數](#可變參數函數)
* [15.指標](#指標)
* [16.Defer](#Defer)


<br>

## 字符串

* **採用UTF-8**
* **多行聲明**

```go
s := `Hello
        World`
```

* **不可以直接變換**
```go
s := "Hello"
c := []byte(s) //字符串變換需先將 string 轉 byte
c[4] = 'c'
s1 := string(c) //再轉回 string
```

<br>

## 錯誤

* **一般錯誤**
```go
package main                              

import (                                  
        "errors"                          
        "fmt"                             
)                                         

func main() {             //遇到錯誤不會中止程式                
        err := errors.New("Some error")   
        if err != nil {                   
                fmt.Println(err)  //遇到錯誤可以決定如何處理    
        }                                 

        fmt.Println("More message")       
}
```
* **錯誤介面**
```go
type error interface {
    Error() string
}
```
* **嚴重錯誤**
```go
panic(string)//強制中止程式
```

<br>

## 常數
```go
const pi = 3.14
```
<br>

## 枚舉
```go
const(
    a = iota  //0
    b         //1
    test = "A"//A
    c = iota  //3
    d         //4
)
```

<br>

## Array
* **一維**
```go
var arr [n]type
var arr [n]type{}
```
* **多維**
```go
var arr [n][n]type
var arr [n][n]type{{},{}}
```

<br>

## Slice
* **動態數組**
```go
var slice []type
slice := []type{}
slice := make([]type, len, cap)
```
* **長度 容量**
```go
len(slice)
cap(slice)
```
* **新增**
```go
slice = append(slice, n)
```

<br>

## Map
* **類似Python字典**
* **無序的**
* **長度不固定**
```go
var nums map[type]type    //map[key]var
var nums map[type]type{}
nums := make(map[type1]type2)
nums[type1] = type2
```
* **取值用key**
* **刪除用key**
```go
delete(nums,key)
```

<br>

## New
* **初始化泛型**
* **回傳指標(不同於make)**
```go
nums := new(map[type]type)
```

<br>

## If_Else
```go
if x > n{
    //do something
}else if x > n1{
    //do something
}else{
    //do something
}
```
* **允許聲明變數，只存在於 if**
```go
if x := computedValue(); x > n{
    //do someting
}
```

<br>

## Goto
* **跳轉**
```go
Here:
    goto Here //跳轉至Here
}
```

<br>

## For
```go
for index := 0; index < n; index++{//類似C
        //do someting
}
```
* **while**
```go
for index < n{
        //do someting
}
```
* **跳出迴圈**
```go
for index := 10; index > n; index--{
        //do someting
    break
}
```
* **跳過本次迴圈**
```go
for index := 10; index > n; index--{
        //do someting
    continue
}
```
* **用range讀map**
```go
nums := map[string]int{"one": 1, "two": 2}
for k, v := range nums {
	fmt.Println(k)
	fmt.Println(v)
}
```

<br>

## Switch
```go
switch sExpr {
case expr1:
    //some instructions
case expr2:
    //some other instructions
case expr3:
    //some other instructions
default:
    //other code
}
```

<br>

## 函數
```go
func funcName(input1 type1,input2 type2)(output1 type1,output2 type2){
        //do someting
    return value1, value2
}
```

<br>

## 可變參數函數
```go 
func toFullname(names ...stirng) string {//可以接收多個或0個參數
  return strings.Join(names, " ")
}
```
<br>

## 指標
```go
func one(xPtr *int){
    *xPtr = 1
}
func main(){
    x := 5
    one(&x)        //傳入x指標位置
    fmt.Println(x) // x is 1
}
```

<br>

## Defer
* **執行的時間點會在離開目前func時**
```go
func ReadFile(){
    file.Open("file")
    defer file.Close()
}
```
* **後進先出**
```go
for i := 0; i < 5; i++ {
    defer fmt.Printf("%d ", i) //4 3 2 1 0
}
```

