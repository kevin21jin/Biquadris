# Biquadris

## Overview

The video game Biquadris is a Latinization of the game Tetris, expanded for two player competition. It consists of two boards, each 11 columns wide and 15 rows high. Blocks consisting of four cells  appear at the top of each board, and you must drop them onto their respective boards so as not to leave any gaps. Once an entire row has been filled, it disappears, and the blocks above move down by one unit.

## About

- Language: C++

- Design Patterns: Object-Oriented Programming, Encapsulation, Abstract classes, RAII Idiom

## Rules

- Cell: Every cell is only constructed when a board is constructed, and it remains in its original position until the program terminates. If a cell’s type is modified and the cell is not set to “blind”, it will draw a new square in the corresponding colour in the Xwindow to update the graphical display. If a cell is set to “blind”, it will become a black square in the graphical display. If a cell is not “blind”, it appears in the colour corresponding to its type.

- Block: When the board generates a block, a new block is constructed at the top left of the board. However, if there isn’t enough space, the block will be set to “doesn’t exist” and the board will observe this to determine whether the game should be terminated. The movement and rotation of a block is accomplished by changing the cells that it points to and setting the cells’ types accordingly. When performing a horizontal or vertical move, the function returns a boolean to indicate whether the move is valid or not. This information is useful for the board when a “heavy” block is moved.

- Board: Board contains a vector of vectors that contains totally 11x15 cell pointers, which constitutes the game board. Also, it contains a vector of block pointers. Therefore, the board knows the movement and status of all blocks. Board directly or indirectly handles most of the player's operations. It updates the game board (vector of vectors of cell pointers) in it by traversing, clearing out the full rows and calculating the new score. The board implements the methods of generating new blocks; moving, dropping and rotating blocks by calling the methods of the block. Also, there are three boolean variables in Board to help track the special effects (Blind, Heavy and Force) on the current board, the methods in Board will react differently based on these booleans.

- Level: A block generator can either generate blocks according to a sequence contained in a file or randomly according to the specified rules. The board uses the block generator stored in it to retrieve what type of block should be generated next.

