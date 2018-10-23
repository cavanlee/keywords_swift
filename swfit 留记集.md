```swift
@discardableResult
func discardTest() -> Bool {
        return true
    }
```

swift中所定义的函数如果有返回值的话,调用的时候必须有一个接收方,否则编译器会报一个警告```Result of call to 'discardTest()' is unused```,在方法前加上 ```@discardableResult```，此时不接收这个函数的返回值就不会有警告了。

另外，也可以用一个通配符接收方法返回值,可以达到同样的目的。

```swift
_ = discardTest()
```

