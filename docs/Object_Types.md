# Game

Info about Game object

====

# Cell

The Cell object should not be constructed directly, as it depends on the context of it's parent Grid object. A cell object can be obtained by calling the `getCell()` method on the Grid object.

The `getCell()` method takes either one, two or three parameters, which can be any of the following combinations:

- Co-ordinates `( x , y )`

    If both parameters are integers, they are taken to be in the form of x, y co-ordinates to the cell. These are zero-based from the top left, so the top left cell could be obtained with `getCell( 0 , 0 )`.
- Neighbour `( cell , translation [ , constrained = FALSE ] )`

    If the first parameter of the method is itself a Cell object, the second parameter MUST be an array with exactly 2 integer values. The array represents a translation from the first cell. Some examples are below:

    Translation array | Result
    ----------------- | ------
    `[ 0 , 1 ]`         | Immediately below
    `[ 1 , 0 ]`         | Immediately to the right
    `[ 1 , 1 ]`         | Below and to the right
    `[ -1 , 0 ]`        | Immediately to the left
    `[ -1 , -1 ]`       | Above and to the left
    `[ -3 , 5 ]`        | 3 to the left, 5 down

    The third (optional) parameter, which defaults to false, determines the handling if the translation target is beyond the edge of the grid. For instance, consider a 4 x 4 grid, from which we will choose the cell `[ 3 , 0 ]` as our starting point:

    . | 0 | 1 | 2 | 3
    --- | --- | --- | --- | ---
    0 |   |   |   | X
    1 |   |   |   |  
    2 |   |   |   |  
    3 |   |   |   |  
    
    If we were to pass the translation array `[ 1 , 1 ]`, we would be attempting to retrieve the cell `[ 4 , 1 ]` - which doesn't exist (one down and one to the right of the selected cell is off the right side of the grid). With the constrained parameter false (or not provided), no cell is returned. A debug level error is thrown and the returned value is `false`. If the contrained parameter provided is truthy, instead we provide the closest we can get to the cell by constraining the co-ordinates to the size of the board. In this case, the cell `[ 3 , 1 ]` is returned (marked with an O below):

    . | 0 | 1 | 2 | 3
    --- | --- | --- | --- | ---
    0 |   |   |   | X
    1 |   |   |   | O
    2 |   |   |   |  
    3 |   |   |   |  

- HTML Element or Selector `( element )`

    If the passed value is a string or DOM element then it is checked to see if it evaluates to a cell in the current grid. In the case of the selector, if multiple cells are matched, then only the first one is used for the return value (this could be unpredictable!).
    
## Object methods

- `methodName( param1 , param2 [ , param3 ] )`
    Method description.

## Object properties

- `x`
    The x co-ordinate of the cell (zero-based, left origin)
- `y`
    The y co-ordinate of the cell (zero-based, top origin)
    
====

# Grid

Info about Grid object

====

# Pathfinding

Info about Pathfinding object

====
