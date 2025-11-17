# Non-Duplicated Integrer Array Operations

## Name: Ian Nakano 

## Course: CISC 192 - C++ Programming

## Date: 11/01/2025

---

## Description
This C++ program allows the user to enter **5 unique integers**. 
The program then presents a menu to: 

* Sort the array in **ascending order**
* Sort the array in **descending order**
* Find the **maximum number** in the array

It ensures **no duplicate numbers** are entered.

---

## Instructions 

1. Run the program:
2. Enter 5 unique integers when prompted.
3. Choose an option from the menu: a, b, or c.
4. The program will display the sorted array or the maximum number.

---


```cpp
#include <iostream>
#include <array>

int main() {
    const int N = 5;
    std::array<int, N> numbers{};
    int input;
    bool duplicate;

    std::cout << "Enter " << N << " unique integers:\n";

    // Get unique inputs
    for (int i = 0; i < N; ++i) {
        do {
            duplicate = false;
            std::cout << "Enter number " << i + 1 << ": ";
            std::cin >> input;

            // Check for duplicates
            for (int j = 0; j < i; ++j) {
                if (numbers[j] == input) {
                    std::cout << "Duplicate detected! Please enter a different number.\n";
                    duplicate = true;
                    break;
                }
            }
        } while (duplicate);
        numbers[i] = input;
    }

    // Display menu
    std::cout << "\nMenu:\n";
    std::cout << "a) Sort the array in ascending order\n";
    std::cout << "b) Sort the array in descending order\n";
    std::cout << "c) Find the maximum number\n";
    std::cout << "Enter your choice (a/b/c): ";

    char choice;
    std::cin >> choice;

    // Process choice
    if (choice == 'a') {
        // ascending sort
        for (int i = 0; i < N - 1; ++i) {
            for (int j = i + 1; j < N; ++j) {
                if (numbers[i] > numbers[j]) {
                    int temp = numbers[i];
                    numbers[i] = numbers[j];
                    numbers[j] = temp;
                }
            }
        }
        std::cout << "\nArray sorted in ascending order:\n";
        for (int i = 0; i < N; ++i)
            std::cout << numbers[i] << " ";
        std::cout << "\n";

    } else if (choice == 'b') {
        // descending sort
        for (int i = 0; i < N - 1; ++i) {
            for (int j = i + 1; j < N; ++j) {
                if (numbers[i] < numbers[j]) {
                    int temp = numbers[i];
                    numbers[i] = numbers[j];
                    numbers[j] = temp;
                }
            }
        }
        std::cout << "\nArray sorted in descending order:\n";
        for (int i = 0; i < N; ++i)
            std::cout << numbers[i] << " ";
        std::cout << "\n";

    } else if (choice == 'c') {
        // find maximum
        int maxVal = numbers[0];
        for (int i = 1; i < N; ++i) {
            if (numbers[i] > maxVal) {
                maxVal = numbers[i];
            }
        }
        std::cout << "\nThe maximum number is: " << maxVal << "\n";

    } else {
        std::cout << "\nInvalid choice.\n";
    }

    return 0;
}
