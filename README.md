# EX-8-ADVANCED-ENCRYPTION-STANDARD ALGORITHM
# Aim:
To use Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption.

# ALGORITHM:
1)AES is based on a design principle known as a substitution–permutation.

2)AES does not use a Feistel network like DES, it uses variant of Rijndael.

3)It has a fixed block size of 128 bits, and a key size of 128, 192, or 256 bits.

4)AES operates on a 4 × 4 column-major order array of bytes, termed the state
# PROGRAM:
```
#include <stdio.h>
#include <string.h>

#define KEY 3   // Shift value for substitution

// Function to substitute (encrypt one character)
char substitute(char c)
{
    return c + KEY;
}

// Function to reverse substitute (decrypt one character)
char reverse_substitute(char c)
{
    return c - KEY;
}

// Function to swap characters in pairs
void permute(char text[], int len)
{
    for(int i = 0; i < len - 1; i += 2)
    {
        char temp = text[i];
        text[i] = text[i + 1];
        text[i + 1] = temp;
    }
}

// Reverse permutation (same as permute)
void reverse_permute(char text[], int len)
{
    permute(text, len);
}

int main()
{
    char url[100], encrypted[100], decrypted[100];
    int len;

    printf("Enter URL to encrypt: ");
    scanf("%s", url);

    len = strlen(url);

    // ---------- ENCRYPTION ----------
    for(int i = 0; i < len; i++)
        encrypted[i] = substitute(url[i]);

    encrypted[len] = '\0';

    permute(encrypted, len);

    printf("\nEncrypted URL: %s", encrypted);

    // ---------- DECRYPTION ----------
    strcpy(decrypted, encrypted);

    reverse_permute(decrypted, len);

    for(int i = 0; i < len; i++)
        decrypted[i] = reverse_substitute(decrypted[i]);

    decrypted[len] = '\0';

    printf("\nDecrypted URL: %s\n", decrypted);

    return 0;
}
```

# OUTPUT:

<img width="651" height="499" alt="image" src="https://github.com/user-attachments/assets/c5e3eb85-487c-466f-a71e-0e23f233606a" />


# RESULT:
Hence,the program is executed successfully.


