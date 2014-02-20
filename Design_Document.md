Design Document
===============
This document will be a description of our current checker's requirements and interface creations
-------------------------------------------------------------------------------------------------

Requirements up to Assignment 1
-------------------------------

1.     Must set up an 8X8 checkers board
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
6.User should be notified if a piece choice is illegal
6. a piece on a light square
6. exceeding the maximum number
6. spelling/ typing error
6. there is already a piece there
7.
7. User should be notified if there in an inappropriate number of pieces on the board **
	Inappropriate includes:
7. blank board
8. Must allow for further development of the game, very good abstraction of code


Current Design of Software According to Design Document
=======================================================
>Interface of Assignment 1, basic software interface and functions:
>The assignment requires us to write about what the modules have and how it is abstracted, this is essentially it. 


Pieces
======

Pieces() 
>this will hold the necessary components to describe what a game piece will contain

+**getType()** returns whether the piece is a king or a normal piece

+**getLocation()** returns the location of a specified piece, returning X and Y value

+deleted getLocationX() redundant method replaced by getLocation

+deleted getLocationY() redundant method replaced by getLocation

+**setType(String a)** allows the type of the piece to be specified by a string a to (red,black,rking,bking)

+**setLocation(int x, int y)** allows the location of the piece to be specified

Board
=====

Board() 
>this will hold the necessary components and attributes to describe and setup the board

+**UpdateBoard()** update visuals of the board

+**RemovePiece(int x, int y)** removes visual piece and reference in the matrix representation

+**setLocation(int x, int y)** allows the insertion of a piece into the matrix representation

+**clear()** clear the entire board of all pieces

+**getOccupied(int x, int y)** checks to see if a particular square is occupied, along with its current rank and player assigned

+**deleted getOccupiedBy()** redundant method.

+**placePiece(int x, int y)** places the piece? **not sure when this is needed yet**

+**finishBoard()** changes state to playing

+**isBoardClear()** checks if no squares have pieces, returns a boolean