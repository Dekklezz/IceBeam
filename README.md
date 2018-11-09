# IceBeam
A small static class for Keyboard and Mouse automation based on bitmap patterns recognition written in C#.

# Variables created:

*static int **chroma_r**, **chroma_g**, **chroma_b**;*

# Methods created:

## KEYBOARD:

**SendKeystroke({*char c* || *string s* || *int id* },*bool ctrl*, *bool alt*, *bool shift*)**
// Accepts either a character, a string or a index number from the keylist given below.
// Uses 3 booleans to define if we want to push ctrl, alt or shift while sending the keystroke.

**PushKey(*int id*)**
// Presses the key corresponding the index number from the keylist given below

**ReleaseKey(*int id*)**
// Releases the key corresponding the index number from the keylist given below

## MOUSE:

**SendClick(*System.Drawing.Point location*, *int click_type*,*bool ctrl*, *bool alt*, *bool shift*)**
// Sends a mouse click to a certain location at the screen.
// The variable "click_type" takes value '0' for left click, otherwise its right click.
// Booleans have same effect that on "SendKeystroke" function.

**SendDrag(*System.Drawing.Point start_location*, *System.Drawing.Point ending_location*, *int click_type*, *bool ctrl*, *bool alt*, *bool shift*, *bool smooth*)**
// Drags mouse pressing a mousebutton from a starting screen location to an ending screen location
// The variable "click_type" takes value '0' for left click, otherwise its right click.
// The first 3 booleans have same effect that on "SendKeystroke" function.
// The last boolean decides either to drag instantly or to smoothly move your mouse cursor from the starting point to the ending point.

**SetCursor(*System.Drawing.Point location*)**
// Sets the cursor at a certain location at the screen.

## SCREEN

**GetScreenRect()** // **GetScreenRect(*int index*)**
// Returns a System.Drawing.Rectangle containing the starting point and the full size of your desired screen.
// If you dont set an index, it will pick first screen, either it will try finding the screen for the index you gave.

**Screenshot(*System.Drawing.Rectangle rect*)**
// Returns a screenshot in Bitmap object, for the "rect" inside the screen at the time the function was called.

**SetChromaKey(*int r*, *int g*, *int b*)**
// Sets the static variables which will be used for the finding algorythms later on.

**FindAll(*Bitmap small_bmp*, *Bitmap big_bmp*, *int tolerance*)**
// Finds all the small_bmp images contained into the big_bmp.
// Tolerance represents a range value for the color component to change
// Eg: Original RGB pixel (100,27,128)
//     Accepted values: R: 100 - tolerance - 100 + tolerance.
//                      G: 27 - tolerance - 27 + tolerance.
//                      B: 128 - tolerance to 128 + tolerance.
//
// If values are inside that ranges, detection at that pixel will be positive.
// 
// It uses the Properties: "chroma_r, chroma_g, chroma_b" to skip that detection and set the pixel as positive.
//
// Returns a List<System.Drawing.Rectangle> containing all coincidences obtained, with their location informations 
// relative to the big bitmap.


**FindFirst(*Bitmap small_bmp*, *Bitmap big_bmp*, *int tolerance*)**
// Finds the small_bmp image contained into the big_bmp.
// Works the same as the one described above, but this one stops when finding the first coincidence.
// 
// It returns a System.Drawing.Rectangle containing the coincidence obtained, with its location information relative 
// to the big bitmap.
// If it was not found, it returns a System.Drawing.Rectangle.Empty(); struct.

**AreTheyEqual(*Bitmap bmp1*, *Bitmap bmp2*)**
// Returns true if both bitmaps contains the same information, false otherwise.


# Keylist

~~------Under construction------~~

