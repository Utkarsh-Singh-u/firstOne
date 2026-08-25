#include <GL/glut.h>
#include <stdio.h>
#include <stdlib.h>

int x1, y1, x2, y2;

void putPixel(int x, int y)
{
    glBegin(GL_POINTS);
    glVertex2i(x, y);
    glEnd();
}

void bresenham(int x1, int y1, int x2, int y2)
{
    int dx = abs(x2 - x1);
    int dy = abs(y2 - y1);

    int sx = (x2 >= x1) ? 1 : -1;
    int sy = (y2 >= y1) ? 1 : -1;

    int x = x1;
    int y = y1;

    putPixel(x, y);

    // |slope| <= 1
    if (dx >= dy)
    {
        int p = 2 * dy - dx;

        for (int i = 0; i < dx; i++)
        {
            x += sx;

            if (p < 0)
            {
                p += 2 * dy;
            }
            else
            {
                y += sy;
                p += 2 * (dy - dx);
            }

            putPixel(x, y);
        }
    }

    // |slope| > 1
    else
    {
        int p = 2 * dx - dy;

        for (int i = 0; i < dy; i++)
        {
            y += sy;

            if (p < 0)
            {
                p += 2 * dx;
            }
            else
            {
                x += sx;
                p += 2 * (dx - dy);
            }

            putPixel(x, y);
        }
    }
}

void display()
{
    glClear(GL_COLOR_BUFFER_BIT);

    glColor3f(1.0, 1.0, 1.0);

    glPointSize(3.0);

    bresenham(x1, y1, x2, y2);

    glFlush();
}

void init()
{
    glClearColor(0.0, 0.0, 0.0, 1.0);

    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();

    gluOrtho2D(0, 800, 0, 600);
}

int main(int argc, char **argv)
{
    printf("Enter x1 y1: ");
    scanf("%d %d", &x1, &y1);

    printf("Enter x2 y2: ");
    scanf("%d %d", &x2, &y2);

    glutInit(&argc, argv);

    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
    glutInitWindowSize(800, 600);
    glutInitWindowPosition(100, 100);

    glutCreateWindow("Bresenham Line Drawing Algorithm");

    init();

    glutDisplayFunc(display);

    glutMainLoop();

    return 0;
}