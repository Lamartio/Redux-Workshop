# Open Source
An introduction to open source
---
![Image-Absolute](https://media.giphy.com/media/HP5dest4oOHf2/giphy.gif)
---
# Workshop Redux
---
## What is redux?
* A state management pattern | 
* An immutable in-memory data representation |
* Send a action to create a modified version of that data |
---
## Data example
``` Kotlin
data class Door(val isOpen: Boolean = false)

data class Window(val isBroken: Boolean = false)

data class House(
  val door: Door = Door()
  val window: Window = Door()
)

object ThrowStone // will break a window
```
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

houseMiddleware(ThrowStone, ::println)
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
- Create an object called Store
- Create a property called `house`.
- Create a (private) property reducer and add the created reducer.
- Create a (private) property middleware and add the created middleware.
+++
``` Kotlin
class Store() {

  var house: House = House()
  val reducer : (House, Any) -> Unit = ...
  val middleware : (Any, (Any) -> Unit) -> Unit = ...
  
}
```
+++ Your turn
- Create a function `dispatch` that takes anything as its argument and call the middleware and the reducer and set the result to `house`
- Use the observer pattern to emit the changes of `house`.
+++
``` Kotlin
class Store() {
  var house: House = House()
  val reducer : (House, Any) -> Unit = ...
  val middleware : (Any, (Any) -> Unit) -> Unit = ...
  
  fun dispatch(action: Any) {
    middleware(action, { a -> 
      house = reducer(house, a)
      emit()
    })
  }
  
  fun emit() {
    // Tell everyone that there is a state change
  }
}
```
--- 
# Back to Doakes...
![Image-Absolute](https://media.giphy.com/media/HP5dest4oOHf2/giphy.gif)
---
# Open source
https://github.com/Lamartio/Redux-Workshop
https://gitpitch.com/lamartio/redux-workshop/master
---
# Summary
- This was an example of the core of Redux. |
- Reducers are simple functions that change the state. |
- Middlewares are responsible for side-effects like (asynchronous) network calls |
- Store holds the current state and emits changes through an observable |

