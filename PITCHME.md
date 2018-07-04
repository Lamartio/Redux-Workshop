# Open Source
+++
![Image-Absolute](https://media.giphy.com/media/HP5dest4oOHf2/giphy.gif)
+++
# Workshop Redux
---
## What is redux?
* A state management pattern | 
* An immutable in-memory data representation |
* Send a action to create a modified version of that data |
---?gist=Lamartio/bd20de7402e35d09bbc0653cb3730397&lang=Kotlin&title=Source: Example (Kotlin)
---
## Components (1/3)
- State |
- Action |
- Reducer = (state, action) -> state |
+++
## Your turn!
- Pick your favorite language and editor
- Create a reducer for the House
- Run the reducer with the House state and a ThrowStone action and print out the resulting house.
+++
``` Kotlin
fun houseReducer(house: House, action: ThrowStone) {
  val window = house.window.copy(isBroken = true)
  val house = house.copy(window = window)

  return house
}
```
---
## Components (2/3)
- State 
- Action 
- Reducer = (state, action) -> state
- Middleware = The handler for asynchronous actions |
+++
``` Kotlin
// synchronous function
fun test(number: Int) : String { 
  return number.toString() 
}
// println(test(123))

// asynchronous function
fun test(number: Int, callback: (String) -> Unit) {
  callback(number.toString())
}
// test(123, { result -> println(result })
```
+++
## Your turn
- Create a function called houseMiddleware that takes a ThrowStone action and a callback called `next` that will take anything.
- The function must call `next` three times: Throw, Throwing, Throwed.
- Run it and print it's result.
+++
``` Kotlin
object Throw
object Throwing
object Throwed

fun houseMiddleware(action: ThrowStone, next: (Any) -> Unit) {
  next(Throw)
  next(Throwing)
  next(Throwed)
}
```
--- 
## Components (3/3)
- State 
- Action 
- Reducer = (state, action) -> state
- Middleware = The handler for asynchronous actions
- Store = holds the state and emits changes |
+++
# Your turn
- Create an object that is a observable and has a `House` as a property.
- Add a (private) property reducer and add the created reducer.
- Add a (private) property middleware and add the created middleware
- Add a function `dispatch` that takes anything as its argument.

--- 

# Almost there

Back to Doakes...
---
![Image-Absolute](https://media.giphy.com/media/HP5dest4oOHf2/giphy.gif)
---
# Open source
