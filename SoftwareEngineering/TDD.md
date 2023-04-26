## Terminology
TDD stands for __Test-Driven Development__

## How
TDD需要在内存内运行

### Core Data的注意事项
如果要测试Core Data，就会在永久保存，就会变得很乱。

让Core Data在内存内运行，即关闭App后，会抹掉所有数据的方法

用UIket 开发的开发者, 会有一个CoreDataStack.swift

主要作用是生成persistentContainer 和NSMnagedObjectContext，这个是默认是sqlite的方式

If you wnat to create a persisContainer of memory type:
```swfit
persistantContainer = NSPersistentContainer(name: "MyData")
//the most important two lines
let description = persistentContainer.persistentStoreDescriptions.first
description?.type = NSInMemoryStoreType

persistentContainer.loadPersistentStores{}
```

How to perform testing in swift UI

## Step1 add a targe of `Unit Test Bundle` type to App
How

Path: Click on App -> Editor -> Add Target -> Unit Testing Bundle
Naming Convention: `<file name to test> + <"Tests">`

Give the test file access to the the file being tested
Path: Click on tested file -> Add Target Membership

## Step2 Writing Testing Functions
Creating a testing function
* Naming Convention: `test_[<do somthing>]_returns[<expected output]`
* Example: `func test_convert10_returns1008(){}`

initialize tested object
* Naming Convention: System Under Testing - sut
* Example: `let sut = [<Class>]()` 
* Do Better: use `setUpWithError` and `tearDownWithError` for initialization and deinitialization
  * whatever we put into the setup function is going to run before each  

Defining Input & Output
* Naming Convention: `actual` and `expected`

## Step3 Assert Testing Results
Function to Use: `XCTAssert[<action>]([<parameter>])`




