# HILL CIPHER — EX. NO: 3

## AIM

To write a C program to implement the Hill Cipher substitution technique for encryption.

## DESCRIPTION

The Hill Cipher is a polygraphic substitution cipher that uses matrix multiplication to encrypt a message. Each letter is represented by a number from 0 to 25, where A = 0, B = 1, ..., Z = 25. The plaintext is divided into blocks of three letters and multiplied by a \\(3 \times 3\\) key matrix modulo 26 to obtain the ciphertext.

## ALGORITHM

1. Read the plaintext and key matrix from the user.
2. Convert the plaintext letters into numbers from 0 to 25.
3. Divide the plaintext into groups of three letters. Add padding if necessary.
4. Arrange the key values in a \\(3 \times 3\\) matrix.
5. Multiply each plaintext block by the key matrix modulo 26.
6. Convert the resulting numbers into letters to obtain the ciphertext.
7. Display the encrypted message.

## PROGRAM

```

#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main()
{
    char plaintext[100], ciphertext[100];
    int key[3][3];
    int i, j, k, sum;
    int len, block[3];

    printf("Enter plaintext (uppercase letters): ");
    scanf("%99s", plaintext);

    len = strlen(plaintext);

    for (i = 0; i < len; i++)
        plaintext[i] = toupper(plaintext[i]);

    /* Pad plaintext with X if required */
    while (len % 3 != 0)
        plaintext[len++] = 'X';

    plaintext[len] = '\0';

    printf("Enter 3x3 key matrix:\n");
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
            scanf("%d", &key[i][j]);

    for (i = 0; i < len; i += 3)
    {
        for (j = 0; j < 3; j++)
            block[j] = plaintext[i + j] - 'A';

        for (j = 0; j < 3; j++)
        {
            sum = 0;

            for (k = 0; k < 3; k++)
                sum += key[j][k] * block[k];

            ciphertext[i + j] = (sum % 26) + 'A';
        }
    }

    ciphertext[len] = '\0';

    printf("Ciphertext: %s\n", ciphertext);

    return 0;
}

```

## OUTPUT
<img width="778" height="463" alt="image" src="https://github.com/user-attachments/assets/b8b258f6-dd06-4225-b00c-be75486e9015" />



## RESULT

Thus, the C program to implement the Hill Cipher substitution technique was written and executed successfully, and the ciphertext was obtained.

Note: This program implements encryption only. For decryption, the key matrix must have an inverse modulo 26.
