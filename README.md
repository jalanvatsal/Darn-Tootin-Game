# Darn-Tootin-Game
Fall 2023 CS 31
Programming Assignment 7
You're Darn Tootin'!
Time due: 11:00 PM Thursday, December 7

You have arrived in the walled city of Tooton, whose residents, known as Tooters, eat beans, cabbage, and hard-boiled eggs with every meal. Although they are used to the resulting effects, the odor that emanates from the Tooters you encounter makes you woozy. Your only hope to keep from passing out is to successfully preach to the Tooters about converting to a diet of lean meat, lettuce, and rice.

That's the scenario for a new video game under development. Your assignment is to complete the prototype that uses character-based graphics.

If you execute this Windows program or this Mac program or this Linux program, you will see the player (indicated by @) in a rectangular city filled with Tooters (usually indicated by T). At each turn, the user will select an action for the player to take. The player will take the action, and then each Tooter will move one step in a random direction. The attempt to move will make each Tooter break wind. If the Tooter is orthogonally adjacent to the player, the player is affected by the blast of gas. If the player suffers twelve such blasts during the game, the player passes out and the game is over.

This smaller Windows version or Mac version or Linux version of the game may help you see the operation of the game more clearly.

(You can run the Linux version by logging in to cs31.seas.ucla.edu and running the command /usr/local/cs/bin/toot or /usr/local/cs/bin/minitoot. On a Mac, if you click on the downloaded zip file and then double-click on the executable file (e.g., tootmac), your operating system may refuse to open it because it can't confirm who developed the program. In that case, right-click on the executable file instead, select Open With and then Terminal.app. Select the gray Open button on the popup that again says it doesn't know the developer. If your Windows system refuses to run the Windows version because it thinks it has a virus, then if you trust me when I say I built the program myself on the SEASnet Windows server with no virus in the source code, and you trust the SEASnet people to not have installed a devious compiler that inserts a virus into code it compiles, and you know how to disable your antivirus software or otherwise get around the refusal, then you can run the Windows version; otherwise, run the Linux version as described at the start of this paragraph.)

At each turn the player may take one of these actions:

Move one step up, down, left, or right to an empty position (i.e., one not occupied by a Tooter). If the player attempts to move into the wall of the city (e.g., down, when on the bottom row) or to a position occupied by a Tooter, the player does not move.
Preach to the Tooters adjacent to the player orthogonally or diagonally (i.e., to any Tooters next to the player in the eight directions). Each of those Tooters independently has a 2/3 probability of the player converting that Tooter to no longer pollute the air. A Tooter who has been converted should be removed from the game, since it poses no further threat to the player and is thus irrelevant.
The game allows the user to select the player's action by typing u/d/l/r for moving or just hitting enter for preaching. The user may also type q to prematurely quit the game.

When it's the Tooters' turn, each Tooter picks a random direction (up, down, left, or right) with equal probability. The Tooter moves one step in that direction if it can; however, if doing so would cause the Tooter to move into a wall of the city (e.g., down, when on the bottom row) or to the position occupied by the player, it does not move. More than one Tooter may occupy the same position; in that case, instead of T, the display will show a digit character indicating the number of Tooters at that position (where 9 indicates 9 or more). After each Tooter attempts to move (even if it doesn't actually move), if it is now orthogonally adjacent to the player (i.e., next to the player directly above, below, to the left, or to the right, but not diagonally), the player suffers one blast of gas from that Tooter. If this is the twelfth gas blast the player has suffered during the game, the player passes out and the game is over.

Your assignment is to complete this C++ program skeleton to produce a program that implements the described behavior. (We've indicated where you have work to do by comments containing the text TODO; remove those comments as you finish each thing you have to do.) The program skeleton you are to flesh out defines four classes that represent the four kinds of objects this program works with: Game, City, Tooter, and Player. Details of the interface to these classes are in the program skeleton, but here are the essential responsibilities of each class:

Game

To create a Game, you specify a number of rows and columns and the number of Tooters to start with. The Game object creates an appropriately sized City and populates it with the Player and the Tooters.
A game may be played. (Notice that the city is displayed after the Tooters have had their turn to move, but not after the player has had its turn.)
City

When a City object of a particular size is created, it has no Tooters or player. In the City coordinate system, row 1, column 1 is the upper-left-most position that can be occupied by a Tooter or Player. (If a City were created with 7 rows and 8 columns, then the lower-right-most position that could be occupied would be row 7, column 8.)
You may tell a City object to create a Tooter at a particular position.
You may tell a City object to create a Player at a particular position.
You may tell a City object to have all the Tooters in it make their move.
You may tell a City object that the Tooters around the player are being preached to. Tooters that are converted must be removed from the City, since they serve no further purpose in the game.
You may ask a City object if the player is at a particular position.
You may ask a City object its size, how many Tooters are at a particular position, and how many Tooters altogether are in the City.
You may ask a City object whether moving from a particular position in a particular direction is possible (i.e., would not go off the edge of the city), and if so, what the resulting position would be.
You may ask a City object for access to its player.
A City object may be displayed on the screen, showing the locations of the Tooters and player, along with other status information.
Player

A Player is created at some position (using the City coordinate system, where row 1, column 1 is the upper-left-most position, etc.).
You may tell a Player to move in a particular direction or to preach.
You may tell a Player it has suffered a gas blast.
You may ask a Player for its position, age (i.e., how many turns the player has survived without passing out), and health status (i.e., how many more gas blasts the player suffers will cause the player to pass out).
Tooter

A Tooter is created at some position (using the City coordinate system, where row 1, column 1 is the upper-left-most position, etc.).
You may tell a Tooter to move.
You may ask a Tooter object for its position.
The skeleton program you are to complete has all of the class definitions and implementations in one source file, which is awkward. Since we haven't yet learned about separate compilation involving classes, we'll have to live with it.

Complete the implementation in accordance with the description of the game. You are allowed to make whatever changes you want to the private parts of the classes: You may add or remove private data members or private member functions, or change their types. You must not make any deletions, additions, or changes to the public interface of any of these classes — we're depending on them staying the same so that we can test your programs. You can and will, of course, make changes to the implementations of public member functions, since the callers of the function wouldn't have to change any of the code they write to call the function. You must not declare any public data members, nor use any global variables whose values may change during execution (so global constants are OK). You may add additional functions that are not members of any class. The word friend must not appear in your program.

Any member functions you implement must never put an object into an invalid state, one that will cause a problem later on. (For example, bad things could come from placing a Tooter outside the city.) Any function that has a reasonable way of indicating failure through its return value should do so. Constructors pose a special difficulty because they can't return a value. If a constructor can't do its job, we have it write an error message and exit the program with failure by calling exit(1);. (We haven't learned about throwing an exception to signal constructor failure.)

STEPS TO RUN THE GAME:
1) Initialize a Game object in the main routine of toot.cpp following this format: Game(int rows, int cols, int nTooters);
2) Call the .play() method on the Game object that you have just instantiated
3) Save and close toot.cpp
4) Compile toot.cpp file with a compiler of your choice
5) Navigate to the directory where the executable file is located and type in the command ./toot on your terminal to play! 
