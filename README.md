
![Markdown Logo](./manual_images/bary.jpg?raw=true)

# Homework 2: Sampling

In this lab, we'll be using barycentric coordinates for color interpolation.

## Logistics

### Building the codebase

Same CMake and OpenGL dependencies as in the previous labs/homework are required to run this codebase, so make sure you have those working.

Start in the folder that GitHub made or that was created when you unzipped the download. Run the following command once to create a build directory, enter it, have CMake generate the appropriate Makefiles for your systen and finally, make the executable, which will be deposited in the build directory.
```
mkdir build && cd build && cmake .. && make
```    

**Don't forget to run ```make``` every time you make changes to your files.**


### Submission
* Your lab and homework solutions are to be submitted on LMS by this upcoming Monday midnight 11:55 pm as usual. 
* You will need to *zip* your **src** folder and submit it on LMS with the naming convention specified there.
* Late submission is allowed with 10% deduction per day until the 6th day as specified on LMS for both components individually.


## Using the GUI

You can run the executable with the command

    make && ./draw ../svg/basic/test1.svg

After finishing Part 3, you will be able to change the viewpoint by dragging your mouse to pan around or scrolling to zoom in and out. Here are all the keyboard shortcuts available (some depend on you implementing various parts of the assignment):

|Key | Action|
|:-----:|------|
|`' '`  | return to original viewpoint|
|`'-'`  | decrease sample rate|
|`'='` | increase sample rate|
|`'Z'` | toggle the pixel inspector|
|`'P'` | switch between texture filtering methods on pixels|
|`'L'` | toggle scanLine|
|`'S'` | save a *png* screenshot in the current directory|
| `'1'-'9'`  | switch between svg files in the loaded directory|

The argument passed to `draw` can either be a single file or a directory containing multiple *svg* files, as in

    make && ./draw ../svg/basic/

If you load a directory with up to 9 files, you can switch between them using the number keys 1-9 on your keyboard.

### Structure

* Part 1: Finding BaryCentric Coordinates
* Part 2: Computing Color
* Part 3: Retrieving Color

### Part 3: Retrieving Color

Go to `DrawRend::rasterize_triangle(...)` in *drawrend.cpp*.

Remember that *tri* parameter you were told to ignore in the previous parts? This is where it comes in handy. Modify the implementation such that if a non-NULL `Triangle *tri` pointer is passed in, it calls the `tri->color(...)` to request the appropriate color (for each sample hit). You just need to think about the correct parameters to pass in it.

The reason a Triangle* pointer is used is to generally reference both ColorTri and TexTri structs that are inherited from it (svg.h), the latter of which you will discover more about soon, as both having their own color sampling functions with the same name color().

To test your implementation, run the following command:

   	make;./draw ../svg/basic/test7.svg

If implemented correctly, instead of a black circle, you will be able to view the colour wheel:

![Markdown Logo](./manual_images/colorwheel.png?raw=true)
