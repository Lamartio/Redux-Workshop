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
## Components
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
## Components
- State 
- Action 
- Reducer = (state, action) -> state
- Middleware |
+++
## Middleware
The handler for asynchronous actions. 
