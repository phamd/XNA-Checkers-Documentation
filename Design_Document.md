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

+ **setUpBoard(input : string)** sets up board based on input
+ **getPiece(colmn : int, row: int)** checks to see if a particular square is occupied, if there is it is returned
+ **placePiece(colimn : int, row: int)** allows the insertion of a piece onto the board
+ **movePiece(fromCol : int, fromRow : int, toCol : int, toRow : int)** changes a pieces location on the board
+ **clear()** removes all pieces from the board

Implementation
--------------
#### Class Variables

+ **pieceArray** : Private : Array :: Contains all the Piece objects currently on the board in an array.
+ **numWhitePieces** : Private : int :: Holds the number of white pieces on the board as an integer.
+ **numBlackPieces** : Private : int :: Holds the number of black pieces on the board as an integer.

#### Class Functions

+ **setUpBoard(input : string)**     Public : Constructor :: Input string will be read as locations on a physical board and Piece object put in pieceArray accordinngly. numWhitePieces' = numWhitePieces + c and numBlackPieces' = numBlackPieces + d where c and d are between 0 and 12. pieceArray' = pieceArray with c + d more PieceObjects.
+ **getPiece(column : int, row : int)**            Public : PieceReturns :: Returns the Piece object held in the Piece array at the specified location. pieceArray' = PieceArray, numWhitePieces' = numWhitePieces, numBlackPieces' = numBlackPieces.
+ **placePiece(column : int, row : int)** Public : Void :: A new Piece object is placed into pieceArray. Either numWhitePieces' = numWhitePieces + 1 or numBlackPieces' = numWhitePieces + 1. pieceArray' = pieceArray with one more Piece object.
+ **movePiece(fromCol : int, fromRow : int, toCol : int, toRow : int)** Public : Void :: a Piece object is moved to a different location in pieceArray. The size of pieceArray' = size of pieceArray , numWhitePieces' = numWhitePieces, numBlackPieces' = numBlackPieces.
+ **clear()**           Public : Void :: removes all Piece objects from pieceArray. pieceArray' = Array of null objects, numWhitePieces' = 0 or numBlackPieces' = 0.


Pieces
======
Interface
---------
This will hold the necessary components to describe what a game piece will contain, which will be seperate from the game board.
This allows for changes in the game easily and seperate from the board module
Responsibilities: The piece module contains all the data contained within individual pieces, such as the type, and player it belongs to. 

+ **getType()** returns whether the piece is a king or a normal piece
+ **getOwner()**
+ **getLocationX()** returns the location of a specified piece, returning X and Y value
+ **getLocationY()**
+ **getValidMovement(int, int)**
+ **setType(typeState)** allows the type of the piece to be specified by a string a to (red,black,rking,bking)
+ **setLocation(int, int)** allows the location of the piece to be specified

Implementation
--------------
#### Class Variables
+ **column**            Private : Int ::
+ **row**               Private : Int ::
+ **pieceType**         Private : typeState ::
+ **owner**             Private : Player ::
+ **enum : typeState**  Private : 
+ **enum : player**     Private : 

#### Class Functions
+ **getType()**         Public : typeState ::
+ **getOwner()**        Public : player ::
+ **getLocationX()**    Public : int ::
+ **getLocationY()**    Public : int ::
+ **getValidMovement(int, int)**    Public : bool ::
+ **setType(typeState)**    Public : void ::
+ **setLocation(int, int)** Public : void ::

Game1
======
Interface
---------
This module will be the responsible for the initial execution of the game, this class connects and launches critical components together
Game1 will not require an interface as it does not require one, we need a reason.

Implementation
--------------
#### Class Variables
+ **currentstate**      Private : State :: Describes the current state of the program such as what screen is currently being displayed to the user
+ **keyState**          Private : State :: Describes the user input via the keyboard
+ **input**             Private : String :: Is used to collect the commands from the terminal input
+ **board**             Private : Board :: The main board to initlaize for the game
+ **pieceList**         Private : List :: A list of all pieces that are to be placed on the board
+ **mouseStateCurrent** Private : MouseState :: Used to describe the current mouse state such as location = if the user has clicked, and which button left or right
+ **mouseStatePrev**    Private : MouseState :: Holds the previous mouse state
+ **mouseClickedPiece** Private : View_Clickable :: Get the piece that the mouse has clicked on, and will allow for the piece to follow the mouse when dragging

#### Class Functions
+ **Initialize()**  Public : void :: Allows the game to perform any initialization it needs to before starting to run. 
                 *  This is where it can query for any required services and load any non-graphic
                 *  related content.  Calling base.Initialize will enumerate through any components
         and initialize them as well.
+ **LoadContent()** Public : void ::  LoadContent will be called once per game and is the place to load all required content to create the game,
                  * loads all textures to create the gui on the game
+ **UnloadContent()**   Public : void :: UnloadContent will be called once per game and is the place to unload all content.
+ **Update(GameTime)**  Public : void ::  Allows the game to run logic such as updating the world, checking for collisions, gathering input, and playing audio.
+ **Draw(GameTime)**    Public : void :: The game draws different things depending on $currentState. The function clears the screen the redraws the area
                   *    that needs to be updated again.
+ **TakeInput()**   Public : void :: This function will ask the user for a string to parse as the board setup. There are no arguments, the input string will be null before entering the function

ViewClickable
=============
Implementation
--------------
Software Decision Behaviour Hiding, as this class will be used to update the mouse movements of the game 
Graphics implementation
Hardware Behaviour

#### Class Variables
+ **position**  Private : Vector2 ::
+ **size**      Private : Vector2 ::
+ **scale**     Private : float ::

#### Class Functions
+ **Intersect()**       Public : bool ::
+ **draw()**            Public : void ::
+ **getPosition()**     Public : Vector2 ::
+ **setPosition()**     Public : void ::


Self Defined Types
==================
ENUM
----
Suggested Changes

+ **typeState** (Normal, King, Null)
+ **player** (Black, White, Null)

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