## AIM:
To verify the integrity of the data using Hash Functions.
## ALGORITHM:
1.Input a message from the user.<BR>

2.Use a basic custom hash function that applies simple operations like XOR and addition on the characters of the message.<BR>

3.Convert the resulting hash into a hexadecimal format.<BR>

4.Display the computed hash to the user.<BR>

5.Optionally verify the hash by recomputing it and comparing it with a received hash.<BR>

## PROGRAM:
```C
#include <stdio.h>
#include <string.h>

void computeSimpleHash(const char *message, unsigned char *hash) {
    unsigned char temp = 0;

    for (int i = 0; message[i] != '\0'; i++) {
        temp = temp ^ message[i];  
        temp += message[i];        
    }

    *hash = temp;
}

int main() {
    char message[256];      
    unsigned char hash;     
    char receivedHash[3];   

    printf("Enter the message: ");
    scanf("%s", message);

    computeSimpleHash(message, &hash);

    printf("Computed Hash (in hex): %02x\n", hash);

    printf("Enter the received hash (in hex): ");
    scanf("%s", receivedHash);

    unsigned int receivedHashValue;
    sscanf(receivedHash, "%02x", &receivedHashValue);

    if (hash == receivedHashValue) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/9a8afd59-9ed4-4f54-b6f6-a26d797599f2)

## RESULT:
The program to check the integrity of the data using Hash functions was executed successfully.

