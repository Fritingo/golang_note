# 基礎

<br>

## 字符串

**採用UTF-8**
**多行聲明**
ˋˋˋ
s := ˋHello
        Worldˋ
ˋˋˋ
**不可以直接變換**
ˋˋˋ
s := "Hello"
c := []byte(s) //字符串變換需先將 string 轉 byte
c[4] = 'c'
s1 := string(c) //再轉回 string
ˋˋˋ

<br>

## 錯誤

**一般錯誤**
ˋˋˋ
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
ˋˋˋ
**錯誤介面**
ˋˋˋ
type error interface {
    Error() string
}
ˋˋˋ
**嚴重錯誤**
ˋˋˋ
panic(string)//強制中止程式
ˋˋˋ