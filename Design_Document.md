Design Document
===============
This document will be a description of our current checker's requirements and interface creations


Requirements up to Assignment 1
-------------------------------

1.  Must set up an 8X8 checkers board
2.
    2. Squares will be either light or dark
    2. The bottom right square must be light
3. 	User must be able to choose the standard set up
4. Board Rules
    4. User must be able to specify starting position of each piece
    4. Notation for specifying piece location must use standard form (A7 = B)
    4. User should be able to specify type (normal or king)
    4. If they specified every pieces starting position, user must be able to indicate if the set up is complete 
    4. User should be able to clear the board
5. Maximum of 12 white and 12 black pieces can be placed on the board
6. Illegal moves notification:
    6. User should be notified if a piece choice is illegal
    6. a piece on a light square
    6. exceeding the maximum number
    6. spelling/ typing error
    6. there is already a piece there
7. User should be notified if there in an inappropriate number of pieces on the board
	Inappropriate includes:
    7. blank board
8. Must allow for further development of the game, very good abstraction of code

States
------
- Menu
- Set-up
- Playing

Encapsulation Structure
-----------------------
Program -> Game1 -> Board -> Piece 


Current Design of Software According to Design Document
=======================================================
Interface of Assignment 1, basic software interface and functions:
The assignment requires us to write about what the modules have and how it is abstracted, this is essentially it. 

Board
=====
Interface
---------
This will hold the necessary components and attributes to describe and setup the board
Secret: This module encapsulates the Piece module.
Responsibilities: The board module tracks where all the pieces are located. It contains methods to check where pieces are and to add pieces to the board. 
The Board Class will hold an array of Piece objects. It contains methods to check where pieces are and to add pieces to the board. 

+ **UpdateBoard()** update visuals of the board
+ **RemovePiece(int, int)** removes visual piece and reference in the matrix representation
+ **setLocation(int, int)** allows the insertion of a piece into the matrix representation
+ **clear()** clear the entire board of all pieces
+ **getOccupied(int, int)** checks to see if a particular square is occupied, along with its current rank and player assigned
+ **deleted getOccupiedBy()** redundant method.
+ **placePiece(int, int)** places the piece
+ **finishBoard()** changes state to playing
+ **isBoardClear()** checks if no squares have pieces, returns a boolean

Implementation
--------------
######Class Variables

+ **pieceArray** : Private : Array :: 

######Class Functions

+ **Board()**           Public : Constructor :: Creates the "default" set up of the board. It uses one for loop to move through the columns and one to move through the rows. It uses if statements to determine which type of piece to place there. The Piece objects are placed into the pieceArray in their correct positions.
+ **Board(String)**     Public : Constructor :: Takes a String as input that will be interpreted at the Piece locations. It uses a for loop to go throught every Piece and case statements to determine what place and type were entered. The function will check if there are too many pieces or it was an invalid input as described in requirements. Otherwise the current piece is placed in the correct position in the array.
+ **setLocation(int, int, Piece)**  Public : Void :: Allows the insertion of a piece into the Array of Piece objects.
+ **clear()**           Public : Void :: Uses two for loops to clear the Array of all Pieces previosly placed.
+ **getOccupied(int, int)**         Public : Bool :: Returns whether or not a certiain position in the array has a Piece object of is Null.
+ **getOccupiedBy(int, int)**       Public : typeStateUses :: an if statement to determine if a position in the array is occupied by a Piece, if so it returns the Type of that Piece.
+ **getPiece(int, int)**            Public : PieceReturns :: what Piece is at a specific position int the Array.

Pieces
======
Interface
---------
This will hold the necessary components to describe what a game piece will contain, which will be seperate from the game board.
This allows for changes in the game easily and seperate from the board module
Responsibilities: The piece module contains all the data contained within individual pieces, such as the type, and player it belongs to. 

+ **getType()** returns whether the piece is a king or a normal piece
+ **getLocation()** returns the location of a specified piece, returning X and Y value
+ **setType(String)** allows the type of the piece to be specified by a string a to (red,black,rking,bking)
+ **setLocation(int, int)** allows the location of the piece to be specified

Implementation
--------------
######Class Variables


######Class Functions

Game1
======
Interface
---------
This module will be the responsible for the initial execution of the game, this class connects and launches critical components together
Game1 will not require an interface as it does not require one, we need a reason.

Implementation
--------------
######Class Variables
+ **currentstate**      Private : State ::
+ **keyState**          Private : State ::
+ **input**             Private : String :: 
+ **board**             Private : Board ::
+ **pieceList**         Private : List ::
+ **mouseStateCurrent** Private : MouseState ::
+ **mouseStatePrev**    Private : MouseState ::
+ **mouseClickedPiece** Private : View_Clickable ::

######Class Functions
+ **Game1()**       Public : 
+ **Initialize()**  Public :
+ **LoadContent()** Public : 
+ **UnloadContent()**   Public :
+ **Update(GameTime)**  Public :
+ **Draw(GameTime)**    Public :
+ **TakeInput()**   Public :

ViewClickable
=============
Implementation
--------------
>Software Decision Behaviour Hiding, as this class will be used to update the mouse movements of the game 
>Graphics implementation
>Hardware Behaviour

######Class Variables
+ **position** 
+ **size**
+ **scale**

######Class Functions

+ **View_Clickable()**
+ **Intersect()**
+ **draw()**
+ **getPosition()**
+ **setPosition()**


Self Defined Types
==================
ENUM
=====
Suggested Changes
===

Pieces
====
Types
======
+ typeState |  is an enum with values stating if the piece is normal or a king
+ player | states if the piece is owned by black or white

Access Programs (aka methods)
======
+ public Piece(pieceType : typeState, owner : player) -- constructor, doesnt belong in design document i think
+ getType() : typeState -- get piece type
+ getOwner() : player -- get owner of piece
+ setType(pieceType : typeState) : void -- changes type of piece

Board
==========
+ clear() : void -- removes all pieces off the board
+ getPiece(col : int, row : int) -- checks if there is a piece there, if there is, we return it.
+ movePiece(fromCol : int, fromRow : int, toCol : int, toRow : int) -- moves piece
    + we use isValidMovement within movePiece  
+ isValidMovement(fromCol : int, fromRow : int, toCol : int, toRow : int)