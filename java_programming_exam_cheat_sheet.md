# Java Programming Exam Cheat Sheet

## 1. For Loops (`for`)
Use a `for` loop when you know the exact number of iterations beforehand.

### Basic Syntax
```java
for (initialization; condition; increment/decrement) {
    // Code to repeat
}
```
* **Example (Counting up):**
  ```java
  for (int i = 0; i < 10; i++) {
      System.out.print(i + " "); // Prints 0 to 9
  }
  ```
* **Example (Counting down):**
  ```java
  for (int i = 10; i > 0; i--) {
      System.out.print(i + " "); // Prints 10 to 1
  }
  ```

### For-Each Loop (Enhanced For Loop)
Best for reading arrays or collections when you don't need the index.
```java
int[] arr = {10, 20, 30, 40};
for (int val : arr) {
    System.out.println(val);
}
```

### Nested For Loops (For Matrices / 2D Arrays)
```java
for (int i = 0; i < rows; i++) {         // Outer loop (rows)
    for (int j = 0; j < cols; j++) {     // Inner loop (columns)
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println(); // New line after each row
}
```

---

## 2. Arrays (1D and 2D)

### 1D Arrays
* **Declaration & Initialization:**
  ```java
  int[] arr = {10, 20, 30, 40, 50}; // Initialized with values
  int[] nums = new int[100];        // Uninitialized array of size 100
  ```
* **Taking Input into an Array (`Scanner`):**
  ```java
  import java.util.Scanner;
  // ...
  Scanner sc = new Scanner(System.in);
  System.out.print("Enter size: ");
  int n = sc.nextInt();
  int[] arr = new int[n];
  
  for (int i = 0; i < n; i++) {
      arr[i] = sc.nextInt();
  }
  ```
* **Common 1D Array Algorithms:**
  * **Finding Maximum / Minimum:**
    ```java
    int maxVal = arr[0];
    int minVal = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > maxVal) maxVal = arr[i];
        if (arr[i] < minVal) minVal = arr[i];
    }
    ```
  * **Calculating Sum and Average:**
    ```java
    double sum = 0;
    for (int num : arr) {
        sum += num;
    }
    double average = sum / arr.length;
    ```
  * **Linear Search:**
    ```java
    int target = 25;
    int index = -1;
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            index = i;
            break;
        }
    }
    ```

### 2D Arrays (Matrices)
* **Declaration & Initialization:**
  ```java
  int[][] matrix = {
      {1, 2, 3},
      {4, 5, 6},
      {7, 8, 9}
  };
  // Or dynamic: int[][] mat = new int[rows][cols];
  ```
* **Inputting/Traversing a 2D Array:**
  ```java
  int rows = 3, cols = 3;
  int[][] mat = new int[rows][cols];
  for (int i = 0; i < rows; i++) {
      for (int j = 0; j < cols; j++) {
          mat[i][j] = sc.nextInt();
      }
  }
  ```

---

## 3. Menu-Driven Programs (`do-while` + `switch-case`)

### Complete Java Template
```java
import java.util.Scanner;

public class MenuExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int choice;
        
        // Declare state variables outside the loop so they persist
        int[] arr = null; 
        
        do {
            // 1. Display Menu
            System.out.println("\n=====================");
            System.out.println("      MAIN MENU      ");
            System.out.println("=====================");
            System.out.println("1. Create/Input Array");
            System.out.println("2. Display Array");
            System.out.println("3. Find Max Element");
            System.out.println("4. Exit");
            System.out.print("Enter your choice (1-4): ");
            
            // 2. Get User Choice
            choice = sc.nextInt();
            
            // 3. Handle Choice using Switch-Case
            switch (choice) {
                case 1:
                    System.out.print("Enter array size: ");
                    int n = sc.nextInt();
                    arr = new int[n];
                    System.out.println("Enter " + n + " elements:");
                    for (int i = 0; i < n; i++) {
                        arr[i] = sc.nextInt();
                    }
                    break;
                    
                case 2:
                    if (arr == null) {
                        System.out.println("[!] Please create an array first (Option 1).");
                    } else {
                        System.out.print("Array elements: ");
                        for (int val : arr) {
                            System.out.print(val + " ");
                        }
                        System.out.println();
                    }
                    break;
                    
                case 3:
                    if (arr == null || arr.length == 0) {
                        System.out.println("[!] Array is empty or not initialized.");
                    } else {
                        int max = arr[0];
                        for (int i = 1; i < arr.length; i++) {
                            if (arr[i] > max) max = arr[i];
                        }
                        System.out.println("Maximum value: " + max);
                    }
                    break;
                    
                case 4:
                    System.out.println("Exiting program. Goodbye!");
                    break;
                    
                default:
                    System.out.println("[!] Invalid choice! Enter between 1 and 4.");
            }
            
        } while (choice != 4);
        
        sc.close();
    }
}
```

---

## ⚡ Java Exam Quick Tips
* **Null Pointer Exception:** If your menu lets users pick options in any order, always check if your array is `null` before trying to loop through it!
* **String Comparisons:** If your menu uses text options instead of numbers, use `choiceStr.equals("yes")` **never** `choiceStr == "yes"`.