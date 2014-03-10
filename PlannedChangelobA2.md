Assignment 2 Specificiations
============================
Roles
-----

Code : Ryan Mike Don
Testing : Don
Documentation : Erica Terry MD

1. Include choices that enable users to:  
    1. Start a game from original starting positions. 
    1. Start a game from a previously stored state (the state should be saved within a file – and 
you can decide whether you want to allow more than 1 saved game). 
    1. Make moves – you don’t need to be able to play a complete game (yet) – just move 
pieces from one position to another. The moves must be legal moves. You should be 
able to make moves that: simply move a piece to another square; jump the opponent’s 
piece (so that piece is removed from the board); convert a piece to a “king”; move kings 
in both directions (forwards and backwards). You can decide how you want the user to 
indicate moves – graphically or by code (E3-D4 etc), or both. 
    1. Save a game to be resumed later. 
2. The deliverables for the assignment include: 
    2. Extensions to your existing design documents. Make sure you find a way to tell the 
reader (and yourselves) what has changed in your design. A revision history is a good 
idea. 
    2. Extensions to your existing code. Make sure you find a way to tell the reader (and 
yourselves) what has changed in your design. A revision history is a good idea. 
    2. Include a test report document that records how you tested your application.


#### Changelog


+   Saving the file/state, should be hidden, becasue we don't know how it would change
    -   the game savefile format can change and wheather if it is encrypted or not.
	-   saving document should contain which player turn it is on
+   Number of save slots you have because it doesn't have to be just one
+   Adding to the previous documentation
	-   such as legal moves
+   Encapsulation of how pieces are to be moved
+   Valid moves are checked and are hidden from users
	-   hide who's turn it is 
+   Create module list.File io module.
	-   List of things we need to change in old module
+   New method in board that checks if an opposing piece has reached the top of the board and then changes that piece into a king.


#### WHAT TO HIDE (likely to change)

-   how we are saving/loading the state of the game
-   what type of file we're saving to (encrypted or not)
-   number of saved game slots
-   how pieces are moved
-   how we are checking for a valid movement
(from last assignment)


#### WHAT ARE WE ADDING

-   new Class for file I/O (game 1 uses)
    -   save 
    -   load
-   new functions for moving pieces and checking moves (in Board)
    -   movePiece (will contain all the funcations below, cohesion)
	-   checkValidMove
	-   updateMove
	-   isTurnOver
	-   makeKing
-   removePiece in Board
-   new buttons to save game 
-   new button to load game
-   new substates in playing 
    -   player 1
    -   player 2

Link to the Class uses Diagram for View Request for Change
==========================================================
[link to draw.io page]{https://drive.google.com/file/d/0B_OdWfEX6Q8WOW5yM0M3UWc4TEU/edit?usp=sharing}