# EX 4 : ELLIPSE DRAWING ALGORITHM

**AIM :**


To  implement the Bresenham’s  algorithm for ellipse using a c coding.


**EQUIPMENT REQUIRED:**


●	Hardware: Personal Computer (PC)


●	Software: C Compiler

**ALGORITHM :**

Step 1 : Start.
  
Step 2 : Initialize the graphics header files and functions.
   
Step 3 : Declare the required variables and functions.
 
Step 4 : Get the co-ordinates and radius of the ellipse.

Step 5 : Draw the ellipse using the algorithm.

Step  6 : Display the output.
 
Step 7 : stop.


**Program :**

```
Developed By: Simon Malachi S
Register no: 212224040318
```
```
#include <graphics.h>
#include <stdio.h>
#include <math.h>
#include <conio.h>

// Function prototype
void plotpoints(int xcenter, int ycenter, int x, int y);

int main() {
    int gd = DETECT, gm;
    int xcenter, ycenter, rx, ry;
    int x, y;
    float rx2, ry2, p1, p2;
    float dx, dy;

    initgraph(&gd, &gm, "C:\\Turboc3\\BGI");

    printf("Enter the radius values (rx ry): ");
    scanf("%d%d", &rx, &ry);

    printf("Enter the center coordinates (xcenter ycenter): ");
    scanf("%d%d", &xcenter, &ycenter);

    x = 0;
    y = ry;

    rx2 = rx * rx;
    ry2 = ry * ry;

    dx = 2 * ry2 * x;
    dy = 2 * rx2 * y;

    // Region 1
    p1 = ry2 - (rx2 * ry) + (0.25 * rx2);
    while (dx < dy) {
        plotpoints(xcenter, ycenter, x, y);
        x++;
        dx = 2 * ry2 * x;

        if (p1 < 0) {
            p1 = p1 + dx + ry2;
        } else {
            y--;
            dy = 2 * rx2 * y;
            p1 = p1 + dx - dy + ry2;
        }

        delay(10);
    }

    // Region 2
    p2 = (ry2 * (x + 0.5) * (x + 0.5)) + (rx2 * (y - 1) * (y - 1)) - (rx2 * ry2);
    while (y >= 0) {
        plotpoints(xcenter, ycenter, x, y);
        y--;
        dy = 2 * rx2 * y;

        if (p2 > 0) {
            p2 = p2 - dy + rx2;
        } else {
            x++;
            dx = 2 * ry2 * x;
            p2 = p2 + dx - dy + rx2;
        }

        delay(10);
    }

    getch();
    closegraph();
    return 0;
}
void plotpoints(int xcenter, int ycenter, int x, int y) {
    putpixel(xcenter + x, ycenter + y, WHITE);
    putpixel(xcenter - x, ycenter + y, WHITE);
    putpixel(xcenter + x, ycenter - y, WHITE);
    putpixel(xcenter - x, ycenter - y, WHITE);
}

```


**Output :**

![image](https://github.com/user-attachments/assets/b623d75a-7abd-49e6-ba30-b077ab45b4ae)


![Screenshot 2025-05-07 110219](https://github.com/user-attachments/assets/aad8b2f0-2f63-4880-80b8-06a0cc7684d2)




**Result :**

Thus the Bresenham’s  algorithm for ellipse using a c coding is implemented successfully .
