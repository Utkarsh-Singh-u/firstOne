#include <stdio.h>

int main()
{
    // NAND gate training data
    float x[4][2] = {
        {0, 0},
        {0, 1},
        {1, 0},
        {1, 1}
    };

    // NAND target output
    int target[4] = {1, 1, 1, 0};

    // Initial weights
    float w0 = 0.3;     // Bias weight
    float w1 = 0.0;
    float w2 = 0.0;

    float learning_rate = 0.1;
    float threshold = 0.5;

    int count = 0;

    while (count < 8)
    {
        printf("Number of count is %d\n", count);

        for (int i = 0; i < 4; i++)
        {
            // Weighted sum
            float sum = w0 + x[i][0] * w1 + x[i][1] * w2;

            // Threshold activation function
            int output;

            if (sum >= threshold)
                output = 1;
            else
                output = 0;

            // Error
            int error = target[i] - output;

            printf("Sum is %.6f\n", sum);
            printf("Error is %d\n", error);

            // Perceptron learning rule
            w0 = w0 + learning_rate * error;
            w1 = w1 + learning_rate * error * x[i][0];
            w2 = w2 + learning_rate * error * x[i][1];

            printf("Weight 0 = %.6f Weight 1 = %.6f Weight 2 = %.6f\n",
                   w0, w1, w2);
        }

        count++;
    }

    // Testing
    printf("\nTesting:\n");

    for (int i = 0; i < 4; i++)
    {
        float sum = w0 + x[i][0] * w1 + x[i][1] * w2;

        int output;

        if (sum >= threshold)
            output = 1;
        else
            output = 0;

        printf("Sum is %.6f\n", sum);
        printf("The output for test data %d is: %d\n", i, output);
    }

    return 0;
}