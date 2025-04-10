# Ex--5-Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    int i, j, len, rails, count, code[100][1000];
    char str[1000];

    printf("Enter a Secret Message\n");
    fgets(str, sizeof(str), stdin); // Use fgets to prevent buffer overflows
    str[strcspn(str, "\n")] = 0; // Remove trailing newline

    len = strlen(str);

    printf("Enter number of rails\n");
    scanf("%d", &rails);

    // Initialize the code array with 0s
    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            code[i][j] = 0;
        }
    }

    count = 0;
    j = 0;

    while (j < len) {
        if (count % 2 == 0) {
            for (i = 0; i < rails && j < len; i++) {
                code[i][j] = (int)str[j];
                j++;
            }
        } else {
            for (i = rails - 2; i > 0 && j < len; i--) {
                code[i][j] = (int)str[j];
                j++;
            }
        }
        count++;
    }

    // Print the encoded message
    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            if (code[i][j] != 0) {
                printf("%c", (char)code[i][j]);
            }
        }
    }
    printf("\n");

    return 0;
}
```
# OUTPUT
![image](https://github.com/user-attachments/assets/2b0beb0b-4c4a-4338-b3d3-c71ca3fe2ab8)

# RESULT
Hence, Encryption of a message using Rail Fence cipher is implemented and executed successfully.
