# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
## 5. Implementation of one-dimensional array and multidimensional array.
## 6. Implementation of string manipulation.
# Ex.No:11
  Formulate a C program to convert a given decimal number into its binary equivalent and display it.
# Date : 9.2.26
# Aim:
To formulate a C program to convert a decimal number into its binary equivalent and display it.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare variables: num (input number), rem (remainder), binary[] (array to store binary digits), and loop counters i and k.
### Step 4: 
  Read the decimal number from the user.
### Step 5: 
  Initialize i = 0.
### Step 6: 
  Repeat while num > 0:
  Divide num by 2 and store the remainder in binary[i].
  Increment i.
  Update num = num / 2.
### Step 7: 
  Display the binary digits in reverse order (from i-1 down to 0).
### Step 8: 
   Stop
# Program:
```
#include <stdio.h>

int main() {
    int decimal, n;
    int binary[32]; // Array to store binary digits
    int i = 0;

    // Input decimal number
    printf("Enter a decimal number: ");
    scanf("%d", &decimal);

    if(decimal == 0) {
        printf("Binary equivalent: 0\n");
        return 0;
    }

    n = decimal;

    // Convert decimal to binary
    while(n > 0) {
        binary[i] = n % 2; // Store remainder (0 or 1)
        n = n / 2;
        i++;
    }

    // Print binary in reverse order
    printf("Binary equivalent: ");
    for(i = i - 1; i >= 0; i--) {
        printf("%d", binary[i]);
    }
    printf("\n");

    return 0;
}
```
# Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ba4dec22-0bf3-4997-ac5a-264bcaa53ab7" />

# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:12
  Develop a C program to read a matrix and find its saddle point. A saddle point is an element that is the minimum in its row and also the maximum in its column. If such an element exists, display its position and value.
# Date : 9.2.26
# Aim:
  To develop a C program that inputs a matrix, checks each row for its minimum element, verifies whether that element is also the maximum in its corresponding column, and displays the saddle point and its position if it exists.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
 Declare variables i, j, k, m, min, max and a position array pos[2][2].
### Step 4: 
 Read the order of the square matrix m.
### Step 5: 
 Declare an m × m matrix and read its elements.
### Step 6: 
 Display the matrix.
### Step 7: 
   For each row `i` from `0` to `m−1`:
- **Step 7.1:** Set `min` as the first element of the row.  
- **Step 7.2:** Scan the row to find its minimum element and store its position in `pos[0]`.  
- **Step 7.3:** Let `j` be the column of this minimum element.  
- **Step 7.4:** Set `max` as the first element of column `j`.  
- **Step 7.5:** Scan column `j` to find its maximum element and store its position in `pos[1]`.  
### Step 8: 
  Check if the row minimum equals the column maximum:
- If `min == max` **and their positions match**, then the element is a **saddle point**.
- Print the saddle point value and its position.
### Step 9: 
  Stop
# Program:
```
#include <stdio.h>

int main() {
    int rows, cols, i, j, k;
    int found = 0;

    // Read number of rows and columns
    printf("Enter the number of rows and columns: ");
    scanf("%d %d", &rows, &cols);

    int matrix[rows][cols];

    // Read matrix elements
    printf("Enter matrix elements:\n");
    for(i = 0; i < rows; i++) {
        for(j = 0; j < cols; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }

    // Search for saddle point
    for(i = 0; i < rows; i++) {
        // Find minimum element in the row
        int min = matrix[i][0];
        int colIndex = 0;
        for(j = 1; j < cols; j++) {
            if(matrix[i][j] < min) {
                min = matrix[i][j];
                colIndex = j;
            }
        }

        // Check if this minimum is also the maximum in its column
        int isSaddle = 1;
        for(k = 0; k < rows; k++) {
            if(matrix[k][colIndex] > min) {
                isSaddle = 0;
                break;
            }
        }

        if(isSaddle) {
            printf("Saddle point found at row %d, column %d: %d\n", i, colIndex, min);
            found = 1;
            break; // Assuming only one saddle point
        }
    }

    if(!found) {
        printf("No saddle point found in the matrix.\n");
    }

    return 0;
}
```
# Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4b1e52c8-2822-4cb1-8b53-4212cf7738c5" />

# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:13
  Formulate a C program to reverse a string entered by the user and display the reversed string.
# Date : 9.2.26
# Aim:
  To formulate a C program that reads a string from the user, reverses it, and prints the reversed string.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare two character arrays: `s` to store the input string and `d` to store the reversed string.
### Step 4: 
  Read the string from the user using `scanf("%[^\n]s", s);`
### Step 5: 
  Find the length of the string `s` by traversing it until the null character `'\0'` is encountered.
### Step 6: 
  Initialize a counter `j` for the reversed string.
### Step 7: 
  Copy characters from the end of `s` to the beginning of `d` using a loop until all characters are copied in reverse order.
### Step 8: 
  Terminate the reversed string `d` with the null character `'\0'`.
### Step 9: 
  Print the reversed string.
### Step 10: 
  Stop
# Program:
```
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    int len, i;

    // Input string
    printf("Enter a string: ");
    scanf("%s", str);  // Reads string without spaces

    len = strlen(str);

    // Reverse the string
    printf("Reversed string: ");
    for(i = len - 1; i >= 0; i--) {
        printf("%c", str[i]);
    }
    printf("\n");

    return 0;
}
```

# Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b6e5970d-e0f2-464e-a789-b3579109bc87" />

# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.

# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:14
  Formulate a C program to count the frequency of each character in a given string and display the count of every character.
# Date : 9.2.26
# Aim:
  To formulate a C program that accepts a string from the user and calculates the frequency of each character in the string.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare a character array `s[100]` to store the input string, an integer array `visited[256]` initialized to `0`, and variables `i`, `n`, and `count`.
### Step 4: 
  Read the string from the user using `scanf("%[^\n]", s);`
### Step 5: 
  Calculate the length of the string using `strlen(s)` and store it in `n`.
### Step 6: 
 For each character `s[i]` in the string (from `i = 0` to `n - 1`):
 - If `visited[(unsigned char)s[i]] == 0` (character not yet counted):  
  - Initialize `count = 0`.  
  - Loop through the string again and increment `count` for every occurrence of `s[i]`.  
  - Print `s[i]` and its count.  
  - Set `visited[(unsigned char)s[i]] = 1` to mark it as counted.
### Step 7: 
  Repeat Step 6 for all characters.
### Step 8:
  Stop
# Program:
```
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    int freq[256] = {0}; // Array to store frequency of all ASCII characters
    int i;

    // Input string
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin); // Use fgets to allow spaces

    // Remove newline character if present
    str[strcspn(str, "\n")] = '\0';

    // Count frequency of each character
    for(i = 0; str[i] != '\0'; i++) {
        freq[(unsigned char)str[i]]++;
    }

    // Display frequencies
    printf("Character frequencies:\n");
    for(i = 0; i < 256; i++) {
        if(freq[i] != 0) {
            printf("'%c' = %d\n", i, freq[i]);
        }
    }

    return 0;
}
```
# Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7fe03d09-f932-4bc6-8d14-58b78f27ac3f" />

# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:15
  Formulate a C program to remove duplicate words from a given string and display the string with only unique words.
# Date : 9.2.26
# Aim:
  To formulate a C program to remove duplicate words from a given string and display the string with only unique words.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare a character array `str` to store the input string and a 2D array `words` to store individual words.
### Step 4: 
  Read the input string using `scanf("%[^\n]s", str);`
### Step 5: 
 Split the string into words:
 - Traverse the string character by character.  
 - When a space is encountered, terminate the current word with `'\0'` and move to the next row in `words`.  
 - Otherwise, copy the character into the current word.
### Step 6: 
  Compare each word with all other words to detect duplicates:
  - If a duplicate is found, mark it by setting the first character to `'\0'`.
### Step 7: 
  Print all words that are not marked as duplicates.
### Step 8: 
  Stop
# Program:
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

#define MAX 1000

// Function to check if a word already exists
int isDuplicate(char *word, char uniqueWords[][50], int count) {
    for(int i = 0; i < count; i++) {
        if(strcmp(word, uniqueWords[i]) == 0) {
            return 1; // Duplicate found
        }
    }
    return 0; // Not a duplicate
}

int main() {
    char str[MAX];
    char uniqueWords[100][50]; // Array to store unique words
    int count = 0;

    // Input string
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);

    // Remove newline character if present
    str[strcspn(str, "\n")] = '\0';

    // Tokenize string into words
    char *token = strtok(str, " ");

    while(token != NULL) {
        if(!isDuplicate(token, uniqueWords, count)) {
            strcpy(uniqueWords[count], token); // Store unique word
            count++;
        }
        token = strtok(NULL, " ");
    }

    // Display string with unique words
    printf("String after removing duplicates:\n");
    for(int i = 0; i < count; i++) {
        printf("%s", uniqueWords[i]);
        if(i < count - 1) printf(" ");
    }
    printf("\n");

    return 0;
}
```
# Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/435c56a1-411c-4df0-b890-b5d5b0b6f6e4" />

# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.

