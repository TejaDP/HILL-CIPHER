# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>

int main()
{
    int key[2][2], inv[2][2];
    int text[2], cipher[2], plain[2];
    int det, i;

    printf("Enter 2x2 key matrix:\n");

    for(i = 0; i < 2; i++)
        for(int j = 0; j < 2; j++)
            scanf("%d", &key[i][j]);

    printf("Enter 2 numbers for plaintext: ");
    scanf("%d %d", &text[0], &text[1]);

    /* Encryption */

    cipher[0] = (key[0][0] * text[0] +
                 key[0][1] * text[1]) % 26;

    cipher[1] = (key[1][0] * text[0] +
                 key[1][1] * text[1]) % 26;

    printf("Encrypted: %d %d\n", cipher[0], cipher[1]);

    /* Find determinant */

    det = key[0][0] * key[1][1] -
          key[0][1] * key[1][0];

    det = (det % 26 + 26) % 26;

    /* Inverse key matrix */

    for(i = 0; i < 26; i++)
    {
        if((det * i) % 26 == 1)
        {
            int inverse = i;

            inv[0][0] = key[1][1] * inverse % 26;
            inv[0][1] = -key[0][1] * inverse % 26;
            inv[1][0] = -key[1][0] * inverse % 26;
            inv[1][1] = key[0][0] * inverse % 26;

            break;
        }
    }

    /* Make values positive */

    for(i = 0; i < 2; i++)
        for(int j = 0; j < 2; j++)
            inv[i][j] = (inv[i][j] + 26) % 26;

    /* Decryption */

    plain[0] = (inv[0][0] * cipher[0] +
                inv[0][1] * cipher[1]) % 26;

    plain[1] = (inv[1][0] * cipher[0] +
                inv[1][1] * cipher[1]) % 26;

    printf("Decrypted: %d %d\n", plain[0], plain[1]);

    return 0;
}
```

## OUTPUT
<img width="1256" height="523" alt="image" src="https://github.com/user-attachments/assets/b42e2fc3-870b-45ec-a2cd-6c2f6a75437f" />

## RESULT
the program implemented successfully.
