# Tic Tac Toe Example

React has a good intro tutorial on making a game of Tic Tac Toe. These notes summarize some of the important key points from the tutorial.

## Event Handling in Child and Parent Elements

In the game, the Square function takes in a function as an argument. As a result, the Square, which is the child of the Board element, can redirect its event handler to the parent.

```js
import { useState } from "react";

function Square({ value, onSquareClick }) {
  return (
    // event triggered here
    <button className="square" onClick={onSquareClick}>
      {value}
    </button>
  );
}

export default function Board() {
  const [squares, setSquares] = useState(Array(9).fill(null));

  // the event eventually calls this function
  function handleClick(i) {
    const nextSquares = squares.slice();
    nextSquares[i] = "X";
    setSquares(nextSquares);
  }

  return (
    <>
      <div className="board-row">
        <Square value={squares[0]} onSquareClick={() => handleClick(0)} />
        // ...
      </div>
      // ...
    </>
  );
}
```

## Triggering a Board Re-Render

The `useState` hook returns a state variable and a set state function. Calling the set state function triggers the Board element to re-render.

```js
export default function Board() {
  const [squares, setSquares] = useState(Array(9).fill(null));

  function handleClick(i) {
    const nextSquares = squares.slice();
    nextSquares[i] = 'X';
    // calling setSquares here re-renders the board
    setSquares(nextSquares);
  }

  // ...
}
```

## Preventing an Infinite Loop Using an Arrow Function

The return statement in the Board element produces a grid of Square elements. Each Square accepts a function. If we were to pass in a function call, we would get an infinite loop because each function call would evaluate the function, causing us to move back to the parent, calling the function, etc. Instead, we use an arrow function to abstract the function. Now, we have defined the function without explicitly calling it each time we run the Board element.

```js
export default function Board() {
  const [squares, setSquares] = useState(Array(9).fill(null));

  function handleClick(i) {
    const nextSquares = squares.slice();
    nextSquares[i] = 'X';
    setSquares(nextSquares);
  }

  return (
    <>
      <div className="board-row">
        <Square value={squares[0]} onSquareClick={() => handleClick(0)} />
        // ...
    </>
    // ...
  );
}
```
