# 基礎

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

##枚舉
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
