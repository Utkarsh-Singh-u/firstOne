#include <stdio.h>
#include <graphics.h>
#include <stdlib.h>

void drawLine(int x1, int y1, int x2, int y2)
{
    int dx = abs(x2 - x1);
    int dy = abs(y2 - y1);

    int sx = (x2 >= x1) ? 1 : -1;
    int sy = (y2 >= y1) ? 1 : -1;

    int x = x1;
    int y = y1;

    putpixel(x, y, WHITE);

    // Case 1: |slope| <= 1
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

            putpixel(x, y, WHITE);
        }
    }

    // Case 2: |slope| > 1
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

            putpixel(x, y, WHITE);
        }
    }
}

int main()
{
    int gd = DETECT, gm;
    int x1, y1, x2, y2;

    initgraph(&gd, &gm, "");

    printf("Enter starting point (x1 y1): ");
    scanf("%d %d", &x1, &y1);

    printf("Enter ending point (x2 y2): ");
    scanf("%d %d", &x2, &y2);

    drawLine(x1, y1, x2, y2);

    getch();
    closegraph();

    return 0;
}