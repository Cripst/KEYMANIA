# KEYMANIA
 This interactive Arduino-based game is inspired by the popular Piano Tiles and combines musical rhythm with player reflexes, creating an engaging and dynamic experience. Players must press the corresponding buttons at the right moment, syncing with a sequence of ‘notes’ or blocks scrolling on a screen. Each correct press continues the musical rhythm, while mistakes are penalized, adding a challenging element.

 The game is designed to test reaction speed and hand-eye coordination, with increasing difficulty as the rhythm becomes faster. The design includes LED display modules or an LCD screen for visualizing the notes, buttons for interaction, and sensors for detecting touches. Sounds are generated in real-time, providing players with auditory feedback and enhancing immersion.

 This project is ideal for music and technology enthusiasts, offering a creative way to combine programming, electronics, and entertainment. Through the flexibility provided by the Arduino platform, the game can be customized with different melodies, difficulty levels, and visual effects to offer a unique experience to each player.

# General Description of the Game
An interactive Arduino-based game inspired by Piano Tiles, combining musical rhythm with fast player reflexes.

# Game Mechanics
The player must press the buttons in rhythm with a sequence of blocks or notes scrolling on a screen, perfectly timing their presses to accumulate points.

# Purpose and Challenges of the Game
Testing reaction speed and hand-eye coordination, with progressively increasing difficulty as the rhythm becomes faster and more complex.

# Hardware design
![image](https://github.com/user-attachments/assets/22d1ef9a-ca75-48c9-a719-64b6985976a5)

# Implementare
![image](https://github.com/user-attachments/assets/363a3ff3-9f26-455a-b8ab-6a8f8720d398)
# Components

| Amount | Part tipe    | Properties                    | Datasheet                                                                                         | Image |
|--------|--------------|-------------------------------|---------------------------------------------------------------------------------------------------|-------|
| 1      | Arduino Nano | Arduino UNO R3 (SKU: A000066) | https://docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf                                |![image](https://github.com/user-attachments/assets/97a8d66c-a17d-43f6-934d-98620967512f)
| 4      | Push button  | GPIO                          | https://components101.com/switches/push-button                                                    |     ![image](https://github.com/user-attachments/assets/04ed3dba-cdb0-4d4a-8420-29e51b0a2d86)
| 1      | Display lcd  | 128x128 LCS (SPI 1.44 inch)   | https://www.kingtechdisplay.com/uploads/file/1.44-inch-spi-interface-128-128-samll-lcd-module.pdf |![image](https://github.com/user-attachments/assets/fdb70236-dacf-4b1b-b0db-44ce79a8f18c) |


# Technical Elements and Components Used

https://github.com/user-attachments/assets/d179356d-3aaa-4102-8241-c99039d2dd0e


The game uses an LCD screen or LED matrix to display the notes, physical buttons for interaction, and sensors for detecting correct presses.

# Components:

- LCD screen for gameplay 
- 4 push buttons - for input
- 7 segment display for score

# Auditory and Visual Feedback
Real-time sounds and visual effects contribute to an engaging game experience, offering instant feedback to the player for each action.

# Customization and Extensibility
The Arduino platform allows for adding new songs, variable difficulty levels, and personalized effects, offering a unique experience for each user.

# Target Audience and Benefits
Ideal for music and technology enthusiasts, the game provides a fun way to improve reflexes, coordination, and rhythm sense.

# General Description
# Hardware Design

The PINs used are the digital pins 13-7 because they have the functionality that were needed.

Conected the pins for the display (digital display 13-10). The display uses the SPI is using the ISP protocol to communicate with the board. For power I used the 3.3V power output (no need for PWM). 

The buttons are connected to the arduino via the digital pins 9-6. They also use a 1k pull-up resistor.

A 9V battery is used to power the arduino through the barrel jack.

# Software Design

The current software implementation includes a functional Arduino-based game similar to Piano Tiles, featuring:

Tile Display: A 1.4-inch ST7735 SPI LCD screen displays falling tiles across four lanes.
User Interaction: Four buttons connected to pins D4–D7 allow users to interact by "hitting" the tiles as they fall.
Game Mechanics:
Users lose the game if they miss a tile, press a button too early, or let a tile fall off the screen.
A scoring system calculates points dynamically based on the time elapsed and number of tiles hit.
Audio Feedback: A speaker connected to pin D3 plays musical notes corresponding to the lanes when tiles are hit.
LCD Score Display: A 1602 LCD module connected via digital pins D0–D2 and analog pins A0–A5 displays the current score in real time.
Menus:
Start Menu: Users can select to start the game or view high scores.
Difficulty Menu: Provides three difficulty levels (Easy, Medium, Hard), which adjust the tile falling speed.
High Scores Menu: Displays the top five high scores stored during gameplay.
The game has been thoroughly tested to ensure accurate interaction, proper visual feedback, and real-time updates on both displays.

Motivation for Library Choices
Adafruit_GFX and Adafruit_ST7735:

These libraries are well-documented, reliable, and provide comprehensive functions for rendering graphics on the ST7735 display.
Their ability to draw shapes, text, and handle colors made them ideal for creating the tile graphics and menus.
LiquidCrystal:

This library offers straightforward methods to control the 1602 LCD screen.
It eliminates the need for external components like potentiometers by allowing contrast control through software.
Arduino Tone:

The built-in tone() function was used for audio feedback due to its simplicity in generating PWM signals for sound.
It integrates seamlessly with the microcontroller’s resources, avoiding additional complexity.
These libraries were chosen for their ease of use, efficiency, and compatibility with the project’s hardware and performance constraints.

Novelty Element of the Project
The project stands out by combining multiple real-time feedback mechanisms:

Interactive Gameplay: Users receive simultaneous visual (tiles), auditory (notes), and tactile (button press) feedback.
Multi-Display Integration: Incorporates both a graphical LCD for game rendering and a character LCD for live score tracking.
Dynamic Scoring System: The scoring system adapts to the gameplay duration and performance, adding a layer of complexity.
Custom Menus: Includes dynamic menus for game start, difficulty selection, and high-score viewing, ensuring user-friendly navigation.
Compact Hardware Design: Efficient use of available pins and resources (e.g., replacing a potentiometer with software-controlled contrast) demonstrates ingenuity in hardware utilization.
Project Architecture and Functional Interaction
1. Project Skeleton:
Main Components:

loop(): Coordinates between menus and game logic.
updateStartMenu(): Handles the start menu.
updateHighScoresMenu(): Displays and manages the high scores.
updateDifficultyMenu(): Enables difficulty selection.
handleGameLogic(): Runs the game loop, updating tiles and managing hits/misses.
Subroutines:

drawTile(): Renders tiles on the ST7735 screen.
playNoteForLane(): Plays a note when a tile is hit.
calculateScore(): Computes the final score at the end of a game.
updateScoreDisplay(): Updates the real-time score on the 1602 LCD.
2. Interaction Between Functionalities:
Menus and Game Logic:
The user navigates from the start menu to the difficulty menu, which launches the game based on user selection.
Tile Management and Input Handling:
Falling tiles are dynamically generated and checked against button inputs for valid hits or misses.
Score Display:
While the ST7735 handles visual gameplay, the 1602 LCD continuously tracks and updates the score, ensuring dual-display functionality.
Audio Feedback:
The tone corresponding to the lane is played whenever a tile is successfully hit.
3. Validation:
Unit Testing:
Each function (e.g., drawTile(), calculateScore(), updateScoreDisplay()) was tested independently to ensure expected outputs.
Integrated Testing:
The entire system was tested with varying difficulty levels, button presses, and edge cases (e.g., multiple misses, simultaneous button presses).
User Testing:
Gameplay was evaluated by users for responsiveness, clarity of visuals, and overall engagement.
This documentation provides a comprehensive view of the current implementation, design decisions, and unique features of the project.
# Results
# Conclusions
# Journal
