# 3D-graphics
========


Functionality
--------

This project creates a window which will display a 3D object on screen defined by vertices and the edges of the faces of the object. User can also use mouse 
to interact with the object, so it helps to visualize the wireframe of 3D object

The code is very simple to use,
```
python3 show_3d_object.py object.txt
```
It uses an input *.txt file, passing as an argument when running the .py file, the object.txt file contains nodes and edges infomation, 
one sample example like following,
```
6,8
1,1.0,0.0,0.0
2,0.0,-1.0,0.0
3,0.0,0.0,1.0
4,-2.0,0.0,0.0
5,0.0,2.0,0.0
6,0.0,0.0,-2.0
1,2,3
1,2,6
1,3,5
1,5,6
2,3,4
2,4,6
3,4,5
4,5,6
```

The first line contains two integers. The first integer is the number of vertices that define the 3D object, and the second number is the number of faces that define the 3D object.
Starting at the second line each line will define one vertex of the 3D object and will consist of an integer followed by three real numbers. The integer is the ID of the vertex and 
the three real numbers define the (x,y,z) coordinates of the vertex. The number of lines in this section will be equal to the first integer in the file.

To run this program, it also needs the some supportive ```*.py``` files in ```lib```folder at the same address as main python script.
```
graphics.py
input.py
matrixOperation.py
colorRender.py
```

Functionality
--------

### Main python script ```show_3d_object.py```
- The class ```loadObject``` inside the script loads the object.txt into program, and parses the comma-separated text file. It stores nodes positions in a numpy (N X 4) array, edges in 
a list, and surfaces which represented by three nodes position in a list as well. After getting all the object infomation, it will pass those information and create an instance of 
class Bese in ```graphics.py```.

### Display module ```graphics.py```
- This part of program is going to process object information and display object on the screen. It contains three main functionalities,
  1. initialize a display screen to show the object with some parameters, such as screen size
  2. a main loop keeps running to update object information and display to screen, this part also has the API to user interface ```input.py```, it can show object 
  based on the user mouse input
  3. a module deals with nodes position information, it calculates the new position of each node and projections which are the images on the screen, it has the API to 
  '''matrixOperation.py``` and ```colorRender.py```.

### mathmetical calculation module ```matrixOperation.py```
- This module can handle 5 kinds of matrix operations
  1. matrix translation
  2. matrix scaling
  3. matrix rotation along x axis
  4. matrix rotation along y axis
  5. matrix rotation along z axis
  
### user interface module ```input.py```
- This module tracks the user's mouse clicking and movement, the infomation will be sent to ```graphics.py``` for rotating the object.

### color render module ```colorRender.py```
This module is optional, it uses only for the purpose of coloring the surfaces of the object. Another main python script 
  ```
  show_3d_object_color.py
  ``` 
will be used to activate the module.
Run the similar command line, 
  ```
  python3 show_3d_object_color.py object.txt
  ``` 
to view colored object.


Installation
------------
It doesn't need to install anythin special, but does require python3 installed with numpy and pygame packages.
To view transparent object, run command line
```
python3 show_3d_object.py object.txt
```
.
To view colored version, run command line

```
python3 show_3d_object_color.py object.txt
```
.
