# Complete 48 Programming Interview Problems for Bangladeshi Software Companies

## 📋 Table of Contents

- [Array Problems (10)](#array-problems)
- [String Problems (10)](#string-problems) 
- [Linked List Problems (6)](#linked-list-problems)
- [Mathematical Problems (10)](#mathematical-problems)
- [Sorting and Searching (6)](#sorting-and-searching)
- [Basic Programming (6)](#basic-programming)

---

## Array Problems (Complete 1-10)
### 1. Find Maximum Element in Array

**Problem:** Find the maximum element in an array.

**C++ Solution:**
```cpp
#include <iostream>
#include <climits>
using namespace std;

int findMax(int arr[], int n) {
    int max = INT_MIN;
    for(int i = 0; i < n; i++) {
        if(arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

int main() {
    int arr[] = {1, 8, 3, 9, 4};
    int n = 5;
    cout << "Maximum element: " << findMax(arr, n) << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <limits.h>

int findMax(int arr[], int n) {
    int max = INT_MIN;
    for(int i = 0; i < n; i++) {
        if(arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

int main() {
    int arr[] = {1, 8, 3, 9, 4};
    int n = 5;
    printf("Maximum element: %d\n", findMax(arr, n));
    return 0;
}
```

**Explanation:** We iterate through the array once, keeping track of the maximum value seen so far. Time complexity: O(n), Space complexity: O(1).

---

### 2. Reverse an Array

**Problem:** Reverse the elements of an array in-place.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

void reverseArray(int arr[], int n) {
    int start = 0, end = n - 1;
    while(start < end) {
        // Swap elements
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int n = 5;
    cout << "Original: ";
    printArray(arr, n);
    reverseArray(arr, n);
    cout << "Reversed: ";
    printArray(arr, n);
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void reverseArray(int arr[], int n) {
    int start = 0, end = n - 1;
    while(start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int n = 5;
    printf("Original: ");
    printArray(arr, n);
    reverseArray(arr, n);
    printf("Reversed: ");
    printArray(arr, n);
    return 0;
}
```

**Explanation:** Use two pointers approach - start from beginning and end, swap elements and move pointers toward center. Time complexity: O(n), Space complexity: O(1).

---

### 3. Two Sum Problem

**Problem:** Find two numbers in an array that add up to a specific target.

**C++ Solution:**
```cpp
#include <iostream>
#include <unordered_map>
#include <vector>
using namespace std;

vector<int> twoSum(vector<int>& nums, int target) {
    unordered_map<int, int> numMap;
    
    for(int i = 0; i < nums.size(); i++) {
        int complement = target - nums[i];
        
        if(numMap.find(complement) != numMap.end()) {
            return {numMap[complement], i};
        }
        
        numMap[nums[i]] = i;
    }
    
    return {}; // No solution found
}

int main() {
    vector<int> nums = {2, 7, 11, 15};
    int target = 9;
    
    vector<int> result = twoSum(nums, target);
    if(!result.empty()) {
        cout << "Indices: " << result[0] << ", " << result[1] << endl;
    }
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

// Brute force approach for C
int* twoSum(int* nums, int numsSize, int target) {
    static int result[2];
    
    for(int i = 0; i < numsSize - 1; i++) {
        for(int j = i + 1; j < numsSize; j++) {
            if(nums[i] + nums[j] == target) {
                result[0] = i;
                result[1] = j;
                return result;
            }
        }
    }
    return NULL;
}

int main() {
    int nums[] = {2, 7, 11, 15};
    int target = 9;
    int size = 4;
    
    int* result = twoSum(nums, size, target);
    if(result != NULL) {
        printf("Indices: %d, %d\n", result[0], result[1]);
    }
    return 0;
}
```

**Explanation:** C++ uses hash map for O(n) solution. C uses brute force O(n²) approach. The hash map stores numbers we've seen and their indices.

---

### 4. Find Second Largest Element

**Problem:** Find the second largest element in an array.

**C++ Solution:**
```cpp
#include <iostream>
#include <climits>
using namespace std;

int findSecondLargest(int arr[], int n) {
    if(n < 2) return -1;
    
    int largest = INT_MIN, second = INT_MIN;
    
    for(int i = 0; i < n; i++) {
        if(arr[i] > largest) {
            second = largest;
            largest = arr[i];
        }
        else if(arr[i] > second && arr[i] != largest) {
            second = arr[i];
        }
    }
    
    return (second == INT_MIN) ? -1 : second;
}

int main() {
    int arr[] = {12, 35, 1, 10, 34, 1};
    int n = 6;
    int result = findSecondLargest(arr, n);
    
    if(result != -1) {
        cout << "Second largest: " << result << endl;
    } else {
        cout << "Second largest not found" << endl;
    }
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <limits.h>

int findSecondLargest(int arr[], int n) {
    if(n < 2) return -1;
    
    int largest = INT_MIN, second = INT_MIN;
    
    for(int i = 0; i < n; i++) {
        if(arr[i] > largest) {
            second = largest;
            largest = arr[i];
        }
        else if(arr[i] > second && arr[i] != largest) {
            second = arr[i];
        }
    }
    
    return (second == INT_MIN) ? -1 : second;
}

int main() {
    int arr[] = {12, 35, 1, 10, 34, 1};
    int n = 6;
    int result = findSecondLargest(arr, n);
    
    if(result != -1) {
        printf("Second largest: %d\n", result);
    } else {
        printf("Second largest not found\n");
    }
    return 0;
}
```

**Explanation:** Single pass through array maintaining largest and second largest values. Handle edge cases like duplicate largest values. Time complexity: O(n).

---

### 5. Remove Duplicates from Sorted Array

**Problem:** Remove duplicates from a sorted array in-place.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

int removeDuplicates(int arr[], int n) {
    if(n == 0) return 0;
    
    int j = 0; // Index for unique elements
    
    for(int i = 1; i < n; i++) {
        if(arr[i] != arr[j]) {
            j++;
            arr[j] = arr[i];
        }
    }
    
    return j + 1; // Length of array with unique elements
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {1, 1, 2, 2, 2, 3, 4, 4, 5};
    int n = 9;
    
    cout << "Original: ";
    printArray(arr, n);
    
    int newLength = removeDuplicates(arr, n);
    cout << "After removing duplicates: ";
    printArray(arr, newLength);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int removeDuplicates(int arr[], int n) {
    if(n == 0) return 0;
    
    int j = 0;
    
    for(int i = 1; i < n; i++) {
        if(arr[i] != arr[j]) {
            j++;
            arr[j] = arr[i];
        }
    }
    
    return j + 1;
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {1, 1, 2, 2, 2, 3, 4, 4, 5};
    int n = 9;
    
    printf("Original: ");
    printArray(arr, n);
    
    int newLength = removeDuplicates(arr, n);
    printf("After removing duplicates: ");
    printArray(arr, newLength);
    
    return 0;
}
```

**Explanation:** Use two pointers - one to track unique elements position, another to scan array. Since array is sorted, duplicates are adjacent. Time complexity: O(n).

---

### 6. Find Missing Number

**Problem:** Find the missing number in an array containing n-1 numbers taken from range 1 to n.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

int findMissingNumber(int arr[], int n) {
    // Method 1: Using sum formula
    int expectedSum = (n + 1) * (n + 2) / 2;
    int actualSum = 0;
    
    for(int i = 0; i < n; i++) {
        actualSum += arr[i];
    }
    
    return expectedSum - actualSum;
}

// Method 2: Using XOR
int findMissingNumberXOR(int arr[], int n) {
    int xor1 = 0, xor2 = 0;
    
    for(int i = 0; i < n; i++) {
        xor1 ^= arr[i];
    }
    
    for(int i = 1; i <= n + 1; i++) {
        xor2 ^= i;
    }
    
    return xor1 ^ xor2;
}

int main() {
    int arr[] = {1, 2, 4, 5, 6};
    int n = 5;
    cout << "Missing number: " << findMissingNumber(arr, n) << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int findMissingNumber(int arr[], int n) {
    int expectedSum = (n + 1) * (n + 2) / 2;
    int actualSum = 0;
    
    for(int i = 0; i < n; i++) {
        actualSum += arr[i];
    }
    
    return expectedSum - actualSum;
}

int main() {
    int arr[] = {1, 2, 4, 5, 6};
    int n = 5;
    printf("Missing number: %d\n", findMissingNumber(arr, n));
    return 0;
}
```

### 7. Stock Buy and Sell

**Problem:** Find the maximum profit by buying and selling a stock once.

**C++ Solution:**
```cpp
#include <iostream>
#include <climits>
using namespace std;

int maxProfit(int prices[], int n) {
    if(n <= 1) return 0;
    
    int minPrice = INT_MAX;
    int maxProfit = 0;
    
    for(int i = 0; i < n; i++) {
        if(prices[i] < minPrice) {
            minPrice = prices[i];
        }
        else if(prices[i] - minPrice > maxProfit) {
            maxProfit = prices[i] - minPrice;
        }
    }
    
    return maxProfit;
}

int main() {
    int prices[] = {7, 1, 5, 3, 6, 4};
    int n = 6;
    cout << "Maximum profit: " << maxProfit(prices, n) << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <limits.h>

int maxProfit(int prices[], int n) {
    if(n <= 1) return 0;
    
    int minPrice = INT_MAX;
    int maxProfit = 0;
    
    for(int i = 0; i < n; i++) {
        if(prices[i] < minPrice) {
            minPrice = prices[i];
        }
        else if(prices[i] - minPrice > maxProfit) {
            maxProfit = prices[i] - minPrice;
        }
    }
    
    return maxProfit;
}

int main() {
    int prices[] = {7, 1, 5, 3, 6, 4};
    int n = 6;
    printf("Maximum profit: %d\n", maxProfit(prices, n));
    return 0;
}
```

### 8. Rotate Array

**Problem:** Rotate an array to the right by k steps.

**C++ Solution:**
```cpp
#include <iostream>
#include <algorithm>
using namespace std;

void rotateArray(int arr[], int n, int k) {
    k = k % n; // Handle k > n
    
    // Reverse entire array
    reverse(arr, arr + n);
    
    // Reverse first k elements
    reverse(arr, arr + k);
    
    // Reverse remaining elements
    reverse(arr + k, arr + n);
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int n = 7;
    int k = 3;
    
    cout << "Original: ";
    printArray(arr, n);
    
    rotateArray(arr, n, k);
    
    cout << "After rotation: ";
    printArray(arr, n);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void reverse(int arr[], int start, int end) {
    while(start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

void rotateArray(int arr[], int n, int k) {
    k = k % n;
    
    reverse(arr, 0, n - 1);
    reverse(arr, 0, k - 1);
    reverse(arr, k, n - 1);
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int n = 7, k = 3;
    
    printf("Original: ");
    printArray(arr, n);
    
    rotateArray(arr, n, k);
    
    printf("After rotation: ");
    printArray(arr, n);
    
    return 0;
}
```

### 9. Merge Two Sorted Arrays

**Problem:** Merge two sorted arrays into one sorted array.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

void mergeSortedArrays(int arr1[], int n1, int arr2[], int n2, int result[]) {
    int i = 0, j = 0, k = 0;
    
    while(i < n1 && j < n2) {
        if(arr1[i] <= arr2[j]) {
            result[k++] = arr1[i++];
        } else {
            result[k++] = arr2[j++];
        }
    }
    
    // Copy remaining elements
    while(i < n1) {
        result[k++] = arr1[i++];
    }
    
    while(j < n2) {
        result[k++] = arr2[j++];
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr1[] = {1, 3, 5, 7};
    int arr2[] = {2, 4, 6, 8, 9};
    int n1 = 4, n2 = 5;
    int result[9];
    
    mergeSortedArrays(arr1, n1, arr2, n2, result);
    
    cout << "Merged array: ";
    printArray(result, n1 + n2);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void mergeSortedArrays(int arr1[], int n1, int arr2[], int n2, int result[]) {
    int i = 0, j = 0, k = 0;
    
    while(i < n1 && j < n2) {
        if(arr1[i] <= arr2[j]) {
            result[k++] = arr1[i++];
        } else {
            result[k++] = arr2[j++];
        }
    }
    
    while(i < n1) {
        result[k++] = arr1[i++];
    }
    
    while(j < n2) {
        result[k++] = arr2[j++];
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr1[] = {1, 3, 5, 7};
    int arr2[] = {2, 4, 6, 8, 9};
    int n1 = 4, n2 = 5;
    int result[9];
    
    mergeSortedArrays(arr1, n1, arr2, n2, result);
    
    printf("Merged array: ");
    printArray(result, n1 + n2);
    
    return 0;
}
```

### 10. Leader Elements in Array

**Problem:** Find all leader elements in an array. An element is leader if it is greater than all elements to its right.

**C++ Solution:**
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> findLeaders(int arr[], int n) {
    vector<int> leaders;
    int maxRight = arr[n-1];
    leaders.push_back(maxRight);
    
    for(int i = n-2; i >= 0; i--) {
        if(arr[i] > maxRight) {
            maxRight = arr[i];
            leaders.push_back(maxRight);
        }
    }
    
    reverse(leaders.begin(), leaders.end());
    return leaders;
}

int main() {
    int arr[] = {16, 17, 4, 3, 5, 2};
    int n = 6;
    
    vector<int> leaders = findLeaders(arr, n);
    
    cout << "Leaders: ";
    for(int leader : leaders) {
        cout << leader << " ";
    }
    cout << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void findLeaders(int arr[], int n) {
    int leaders[n];
    int count = 0;
    int maxRight = arr[n-1];
    leaders[count++] = maxRight;
    
    for(int i = n-2; i >= 0; i--) {
        if(arr[i] > maxRight) {
            maxRight = arr[i];
            leaders[count++] = maxRight;
        }
    }
    
    printf("Leaders: ");
    for(int i = count-1; i >= 0; i--) {
        printf("%d ", leaders[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {16, 17, 4, 3, 5, 2};
    int n = 6;
    findLeaders(arr, n);
    return 0;
}
```

---

## String Problems (Complete 1-10)

### 1. Reverse a String

**Problem:** Reverse a string in-place.

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

// Method 1: Using two pointers
string reverseString1(string str) {
    int start = 0, end = str.length() - 1;
    
    while(start < end) {
        swap(str[start], str[end]);
        start++;
        end--;
    }
    
    return str;
}

// Method 2: Using built-in function
string reverseString2(string str) {
    reverse(str.begin(), str.end());
    return str;
}

int main() {
    string str = "Hello World";
    cout << "Original: " << str << endl;
    cout << "Reversed: " << reverseString1(str) << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>

void reverseString(char str[]) {
    int start = 0;
    int end = strlen(str) - 1;
    
    while(start < end) {
        char temp = str[start];
        str[start] = str[end];
        str[end] = temp;
        start++;
        end--;
    }
}

int main() {
    char str[] = "Hello World";
    printf("Original: %s\n", str);
    reverseString(str);
    printf("Reversed: %s\n", str);
    return 0;
}
```

**Explanation:** Two pointers approach - swap characters from both ends moving toward center. Time complexity: O(n), Space complexity: O(1).

---

### 2. Check if String is Palindrome

**Problem:** Check if a string is a palindrome (reads same forwards and backwards).

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

bool isPalindrome(string str) {
    // Convert to lowercase and remove spaces
    transform(str.begin(), str.end(), str.begin(), ::tolower);
    str.erase(remove(str.begin(), str.end(), ' '), str.end());
    
    int start = 0, end = str.length() - 1;
    
    while(start < end) {
        if(str[start] != str[end]) {
            return false;
        }
        start++;
        end--;
    }
    
    return true;
}

int main() {
    string str = "A man a plan a canal Panama";
    cout << "\"" << str << "\" is " 
         << (isPalindrome(str) ? "a palindrome" : "not a palindrome") << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int isPalindrome(char str[]) {
    int start = 0;
    int end = strlen(str) - 1;
    
    while(start < end) {
        // Skip non-alphanumeric characters
        while(start < end && !isalnum(str[start])) start++;
        while(start < end && !isalnum(str[end])) end--;
        
        if(tolower(str[start]) != tolower(str[end])) {
            return 0; // Not palindrome
        }
        
        start++;
        end--;
    }
    
    return 1; // Is palindrome
}

int main() {
    char str[] = "A man, a plan, a canal: Panama";
    printf("\"%s\" is %s\n", str, 
           isPalindrome(str) ? "a palindrome" : "not a palindrome");
    return 0;
}
```

**Explanation:** Compare characters from both ends, ignoring case and non-alphanumeric characters. Time complexity: O(n).

---

### 3. Count Vowels and Consonants

**Problem:** Count the number of vowels and consonants in a string.

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
using namespace std;

void countVowelsConsonants(string str) {
    int vowels = 0, consonants = 0;
    
    for(char c : str) {
        if(isalpha(c)) {
            char lower = tolower(c);
            if(lower == 'a' || lower == 'e' || lower == 'i' || 
               lower == 'o' || lower == 'u') {
                vowels++;
            } else {
                consonants++;
            }
        }
    }
    
    cout << "Vowels: " << vowels << endl;
    cout << "Consonants: " << consonants << endl;
}

int main() {
    string str = "Hello World";
    cout << "String: " << str << endl;
    countVowelsConsonants(str);
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void countVowelsConsonants(char str[]) {
    int vowels = 0, consonants = 0;
    
    for(int i = 0; str[i] != '\0'; i++) {
        if(isalpha(str[i])) {
            char c = tolower(str[i]);
            if(c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
                vowels++;
            } else {
                consonants++;
            }
        }
    }
    
    printf("Vowels: %d\n", vowels);
    printf("Consonants: %d\n", consonants);
}

int main() {
    char str[] = "Hello World";
    printf("String: %s\n", str);
    countVowelsConsonants(str);
    return 0;
}
```

### 4. Remove Duplicates from String

**Problem:** Remove duplicate characters from a string while maintaining order.

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <unordered_set>
using namespace std;

string removeDuplicates(string str) {
    unordered_set<char> seen;
    string result = "";
    
    for(char c : str) {
        if(seen.find(c) == seen.end()) {
            seen.insert(c);
            result += c;
        }
    }
    
    return result;
}

int main() {
    string str = "programming";
    cout << "Original: " << str << endl;
    cout << "After removing duplicates: " << removeDuplicates(str) << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>

void removeDuplicates(char str[]) {
    int index = 0;
    int visited[256] = {0}; // ASCII characters
    
    for(int i = 0; str[i] != '\0'; i++) {
        if(!visited[(int)str[i]]) {
            str[index++] = str[i];
            visited[(int)str[i]] = 1;
        }
    }
    
    str[index] = '\0';
}

int main() {
    char str[] = "programming";
    printf("Original: %s\n", str);
    removeDuplicates(str);
    printf("After removing duplicates: %s\n", str);
    return 0;
}
```

### 5. Find First Non-Repeating Character

**Problem:** Find the first non-repeating character in a string.

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <unordered_map>
using namespace std;

char firstNonRepeating(string str) {
    unordered_map<char, int> count;
    
    // Count frequency of each character
    for(char c : str) {
        count[c]++;
    }
    
    // Find first character with count 1
    for(char c : str) {
        if(count[c] == 1) {
            return c;
        }
    }
    
    return '\0'; // No non-repeating character found
}

int main() {
    string str = "leetcode";
    char result = firstNonRepeating(str);
    
    if(result != '\0') {
        cout << "First non-repeating character: " << result << endl;
    } else {
        cout << "No non-repeating character found" << endl;
    }
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>

char firstNonRepeating(char str[]) {
    int count[256] = {0};
    
    // Count frequency
    for(int i = 0; str[i] != '\0'; i++) {
        count[(int)str[i]]++;
    }
    
    // Find first non-repeating
    for(int i = 0; str[i] != '\0'; i++) {
        if(count[(int)str[i]] == 1) {
            return str[i];
        }
    }
    
    return '\0';
}

int main() {
    char str[] = "leetcode";
    char result = firstNonRepeating(str);
    
    if(result != '\0') {
        printf("First non-repeating character: %c\n", result);
    } else {
        printf("No non-repeating character found\n");
    }
    
    return 0;
}
```

### 6. Check Anagram

**Problem:** Check if two strings are anagrams of each other.

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

bool isAnagram(string str1, string str2) {
    if(str1.length() != str2.length()) {
        return false;
    }
    
    sort(str1.begin(), str1.end());
    sort(str2.begin(), str2.end());
    
    return str1 == str2;
}

// Alternative method using character count
bool isAnagramCount(string str1, string str2) {
    if(str1.length() != str2.length()) return false;
    
    int count[256] = {0};
    
    for(int i = 0; i < str1.length(); i++) {
        count[str1[i]]++;
        count[str2[i]]--;
    }
    
    for(int i = 0; i < 256; i++) {
        if(count[i] != 0) return false;
    }
    
    return true;
}

int main() {
    string str1 = "listen";
    string str2 = "silent";
    
    cout << "\"" << str1 << "\" and \"" << str2 << "\" are " 
         << (isAnagram(str1, str2) ? "anagrams" : "not anagrams") << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int compare(const void *a, const void *b) {
    return (*(char*)a - *(char*)b);
}

int isAnagram(char str1[], char str2[]) {
    int len1 = strlen(str1);
    int len2 = strlen(str2);
    
    if(len1 != len2) return 0;
    
    qsort(str1, len1, sizeof(char), compare);
    qsort(str2, len2, sizeof(char), compare);
    
    return strcmp(str1, str2) == 0;
}

int main() {
    char str1[] = "listen";
    char str2[] = "silent";
    
    printf("\"%s\" and \"%s\" are %s\n", str1, str2, 
           isAnagram(str1, str2) ? "anagrams" : "not anagrams");
    
    return 0;
}
```

### 7. String to Integer (atoi)

**Problem:** Implement string to integer conversion function.

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <climits>
using namespace std;

int myAtoi(string s) {
    int i = 0, sign = 1;
    long result = 0;
    
    // Skip whitespace
    while(i < s.length() && s[i] == ' ') i++;
    
    // Handle sign
    if(i < s.length() && (s[i] == '+' || s[i] == '-')) {
        sign = (s[i] == '-') ? -1 : 1;
        i++;
    }
    
    // Process digits
    while(i < s.length() && isdigit(s[i])) {
        result = result * 10 + (s[i] - '0');
        
        // Check overflow
        if(result * sign > INT_MAX) return INT_MAX;
        if(result * sign < INT_MIN) return INT_MIN;
        
        i++;
    }
    
    return result * sign;
}

int main() {
    string str = "  -42";
    cout << "String: \"" << str << "\"" << endl;
    cout << "Integer: " << myAtoi(str) << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>
#include <limits.h>
#include <ctype.h>

int myAtoi(char *s) {
    int i = 0, sign = 1;
    long result = 0;
    
    while(s[i] == ' ') i++;
    
    if(s[i] == '+' || s[i] == '-') {
        sign = (s[i] == '-') ? -1 : 1;
        i++;
    }
    
    while(s[i] && isdigit(s[i])) {
        result = result * 10 + (s[i] - '0');
        
        if(result * sign > INT_MAX) return INT_MAX;
        if(result * sign < INT_MIN) return INT_MIN;
        
        i++;
    }
    
    return result * sign;
}

int main() {
    char str[] = "  -42";
    printf("String: \"%s\"\n", str);
    printf("Integer: %d\n", myAtoi(str));
    return 0;
}
```

### 8. Longest Common Prefix

**Problem:** Find the longest common prefix string among an array of strings.

**C++ Solution:**
```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

string longestCommonPrefix(vector<string>& strs) {
    if(strs.empty()) return "";
    
    string prefix = strs[0];
    
    for(int i = 1; i < strs.size(); i++) {
        while(strs[i].find(prefix) != 0) {
            prefix = prefix.substr(0, prefix.length() - 1);
            if(prefix.empty()) return "";
        }
    }
    
    return prefix;
}

int main() {
    vector<string> strs = {"flower", "flow", "flight"};
    
    cout << "Strings: ";
    for(string s : strs) {
        cout << "\"" << s << "\" ";
    }
    cout << endl;
    
    cout << "Longest common prefix: \"" << longestCommonPrefix(strs) << "\"" << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>

void longestCommonPrefix(char strs[][50], int n, char result[]) {
    if(n == 0) {
        result[0] = '\0';
        return;
    }
    
    int minLen = strlen(strs[0]);
    for(int i = 1; i < n; i++) {
        int len = strlen(strs[i]);
        if(len < minLen) minLen = len;
    }
    
    int index = 0;
    for(int i = 0; i < minLen; i++) {
        char current = strs[0][i];
        for(int j = 1; j < n; j++) {
            if(strs[j][i] != current) {
                result[index] = '\0';
                return;
            }
        }
        result[index++] = current;
    }
    
    result[index] = '\0';
}

int main() {
    char strs[][50] = {"flower", "flow", "flight"};
    int n = 3;
    char result[50];
    
    longestCommonPrefix(strs, n, result);
    
    printf("Longest common prefix: \"%s\"\n", result);
    
    return 0;
}
```

### 9. Valid Parentheses

**Problem:** Check if a string containing parentheses is valid.

**C++ Solution:**
```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;

bool isValid(string s) {
    stack<char> st;
    
    for(char c : s) {
        if(c == '(' || c == '[' || c == '{') {
            st.push(c);
        }
        else {
            if(st.empty()) return false;
            
            char top = st.top();
            st.pop();
            
            if((c == ')' && top != '(') ||
               (c == ']' && top != '[') ||
               (c == '}' && top != '{')) {
                return false;
            }
        }
    }
    
    return st.empty();
}

int main() {
    string s = "()[]{}";
    cout << "String: " << s << endl;
    cout << "Valid: " << (isValid(s) ? "Yes" : "No") << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>

int isValid(char *s) {
    char stack[10000];
    int top = -1;
    
    for(int i = 0; s[i] != '\0'; i++) {
        char c = s[i];
        
        if(c == '(' || c == '[' || c == '{') {
            stack[++top] = c;
        }
        else {
            if(top == -1) return 0;
            
            char topChar = stack[top--];
            
            if((c == ')' && topChar != '(') ||
               (c == ']' && topChar != '[') ||
               (c == '}' && topChar != '{')) {
                return 0;
            }
        }
    }
    
    return top == -1;
}

int main() {
    char s[] = "()[]{}";
    printf("String: %s\n", s);
    printf("Valid: %s\n", isValid(s) ? "Yes" : "No");
    return 0;
}
```

### 10. Reverse Words in String

**Problem:** Reverse the order of words in a string.

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <algorithm>
using namespace std;

string reverseWords(string s) {
    stringstream ss(s);
    string word;
    vector<string> words;
    
    while(ss >> word) {
        words.push_back(word);
    }
    
    reverse(words.begin(), words.end());
    
    string result = "";
    for(int i = 0; i < words.size(); i++) {
        if(i > 0) result += " ";
        result += words[i];
    }
    
    return result;
}

int main() {
    string s = "  hello   world  ";
    cout << "Original: \"" << s << "\"" << endl;
    cout << "Reversed: \"" << reverseWords(s) << "\"" << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <string.h>

void reverse(char str[], int start, int end) {
    while(start < end) {
        char temp = str[start];
        str[start] = str[end];
        str[end] = temp;
        start++;
        end--;
    }
}

void reverseWords(char str[]) {
    int len = strlen(str);
    
    // Reverse entire string
    reverse(str, 0, len - 1);
    
    // Reverse each word
    int start = 0;
    for(int i = 0; i <= len; i++) {
        if(str[i] == ' ' || str[i] == '\0') {
            reverse(str, start, i - 1);
            start = i + 1;
        }
    }
}

int main() {
    char str[] = "hello world";
    printf("Original: \"%s\"\n", str);
    reverseWords(str);
    printf("Reversed: \"%s\"\n", str);
    return 0;
}
```

---

## Linked List Problems (Complete 1-6)

### 1. Reverse Linked List

**Problem:** Reverse a singly linked list.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

class LinkedList {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* current = head;
        
        while(current != nullptr) {
            ListNode* nextTemp = current->next;
            current->next = prev;
            prev = current;
            current = nextTemp;
        }
        
        return prev;
    }
    
    void printList(ListNode* head) {
        ListNode* temp = head;
        while(temp != nullptr) {
            cout << temp->val << " ";
            temp = temp->next;
        }
        cout << endl;
    }
    
    ListNode* createList(int arr[], int n) {
        if(n == 0) return nullptr;
        
        ListNode* head = new ListNode(arr[0]);
        ListNode* current = head;
        
        for(int i = 1; i < n; i++) {
            current->next = new ListNode(arr[i]);
            current = current->next;
        }
        
        return head;
    }
};

int main() {
    LinkedList ll;
    int arr[] = {1, 2, 3, 4, 5};
    ListNode* head = ll.createList(arr, 5);
    
    cout << "Original: ";
    ll.printList(head);
    
    head = ll.reverseList(head);
    
    cout << "Reversed: ";
    ll.printList(head);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <stdlib.h>

struct ListNode {
    int val;
    struct ListNode* next;
};

struct ListNode* createNode(int val) {
    struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
    node->val = val;
    node->next = NULL;
    return node;
}

struct ListNode* reverseList(struct ListNode* head) {
    struct ListNode* prev = NULL;
    struct ListNode* current = head;
    
    while(current != NULL) {
        struct ListNode* nextTemp = current->next;
        current->next = prev;
        prev = current;
        current = nextTemp;
    }
    
    return prev;
}

void printList(struct ListNode* head) {
    struct ListNode* temp = head;
    while(temp != NULL) {
        printf("%d ", temp->val);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct ListNode* head = createNode(1);
    head->next = createNode(2);
    head->next->next = createNode(3);
    head->next->next->next = createNode(4);
    head->next->next->next->next = createNode(5);
    
    printf("Original: ");
    printList(head);
    
    head = reverseList(head);
    
    printf("Reversed: ");
    printList(head);
    
    return 0;
}
```

### 2. Find Middle Element

**Problem:** Find the middle element of a linked list.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

ListNode* findMiddle(ListNode* head) {
    if(head == nullptr) return nullptr;
    
    ListNode* slow = head;
    ListNode* fast = head;
    
    while(fast != nullptr && fast->next != nullptr) {
        slow = slow->next;
        fast = fast->next->next;
    }
    
    return slow;
}

ListNode* createList(int arr[], int n) {
    if(n == 0) return nullptr;
    
    ListNode* head = new ListNode(arr[0]);
    ListNode* current = head;
    
    for(int i = 1; i < n; i++) {
        current->next = new ListNode(arr[i]);
        current = current->next;
    }
    
    return head;
}

void printList(ListNode* head) {
    ListNode* temp = head;
    while(temp != nullptr) {
        cout << temp->val << " ";
        temp = temp->next;
    }
    cout << endl;
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    ListNode* head = createList(arr, 5);
    
    cout << "List: ";
    printList(head);
    
    ListNode* middle = findMiddle(head);
    if(middle != nullptr) {
        cout << "Middle element: " << middle->val << endl;
    }
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <stdlib.h>

struct ListNode {
    int val;
    struct ListNode* next;
};

struct ListNode* createNode(int val) {
    struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
    node->val = val;
    node->next = NULL;
    return node;
}

struct ListNode* findMiddle(struct ListNode* head) {
    if(head == NULL) return NULL;
    
    struct ListNode* slow = head;
    struct ListNode* fast = head;
    
    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
    }
    
    return slow;
}

void printList(struct ListNode* head) {
    struct ListNode* temp = head;
    while(temp != NULL) {
        printf("%d ", temp->val);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct ListNode* head = createNode(1);
    head->next = createNode(2);
    head->next->next = createNode(3);
    head->next->next->next = createNode(4);
    head->next->next->next->next = createNode(5);
    
    printf("List: ");
    printList(head);
    
    struct ListNode* middle = findMiddle(head);
    if(middle != NULL) {
        printf("Middle element: %d\n", middle->val);
    }
    
    return 0;
}
```

### 3. Detect Cycle in Linked List

**Problem:** Detect if a linked list has a cycle.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

bool hasCycle(ListNode* head) {
    if(head == nullptr || head->next == nullptr) return false;
    
    ListNode* slow = head;
    ListNode* fast = head->next;
    
    while(slow != fast) {
        if(fast == nullptr || fast->next == nullptr) {
            return false;
        }
        slow = slow->next;
        fast = fast->next->next;
    }
    
    return true;
}

int main() {
    ListNode* head = new ListNode(3);
    head->next = new ListNode(2);
    head->next->next = new ListNode(0);
    head->next->next->next = new ListNode(-4);
    head->next->next->next->next = head->next; // Create cycle
    
    cout << "Has cycle: " << (hasCycle(head) ? "Yes" : "No") << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <stdlib.h>

struct ListNode {
    int val;
    struct ListNode* next;
};

struct ListNode* createNode(int val) {
    struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
    node->val = val;
    node->next = NULL;
    return node;
}

int hasCycle(struct ListNode* head) {
    if(head == NULL || head->next == NULL) return 0;
    
    struct ListNode* slow = head;
    struct ListNode* fast = head->next;
    
    while(slow != fast) {
        if(fast == NULL || fast->next == NULL) {
            return 0;
        }
        slow = slow->next;
        fast = fast->next->next;
    }
    
    return 1;
}

int main() {
    struct ListNode* head = createNode(3);
    head->next = createNode(2);
    head->next->next = createNode(0);
    head->next->next->next = createNode(-4);
    head->next->next->next->next = head->next; // Create cycle
    
    printf("Has cycle: %s\n", hasCycle(head) ? "Yes" : "No");
    
    return 0;
}
```

### 4. Delete Node

**Problem:** Delete a node from linked list given only access to that node.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

void deleteNode(ListNode* node) {
    if(node == nullptr || node->next == nullptr) return;
    
    // Copy the next node's value to current node
    node->val = node->next->val;
    
    // Delete the next node
    ListNode* nodeToDelete = node->next;
    node->next = node->next->next;
    delete nodeToDelete;
}

void printList(ListNode* head) {
    ListNode* temp = head;
    while(temp != nullptr) {
        cout << temp->val << " ";
        temp = temp->next;
    }
    cout << endl;
}

int main() {
    ListNode* head = new ListNode(4);
    head->next = new ListNode(5);
    head->next->next = new ListNode(1);
    head->next->next->next = new ListNode(9);
    
    cout << "Original: ";
    printList(head);
    
    // Delete node with value 5 (second node)
    deleteNode(head->next);
    
    cout << "After deletion: ";
    printList(head);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <stdlib.h>

struct ListNode {
    int val;
    struct ListNode* next;
};

struct ListNode* createNode(int val) {
    struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
    node->val = val;
    node->next = NULL;
    return node;
}

void deleteNode(struct ListNode* node) {
    if(node == NULL || node->next == NULL) return;
    
    node->val = node->next->val;
    
    struct ListNode* nodeToDelete = node->next;
    node->next = node->next->next;
    free(nodeToDelete);
}

void printList(struct ListNode* head) {
    struct ListNode* temp = head;
    while(temp != NULL) {
        printf("%d ", temp->val);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct ListNode* head = createNode(4);
    head->next = createNode(5);
    head->next->next = createNode(1);
    head->next->next->next = createNode(9);
    
    printf("Original: ");
    printList(head);
    
    deleteNode(head->next);
    
    printf("After deletion: ");
    printList(head);
    
    return 0;
}
```

### 5. Merge Two Sorted Lists

**Problem:** Merge two sorted linked lists into one sorted list.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    ListNode dummy(0);
    ListNode* tail = &dummy;
    
    while(l1 && l2) {
        if(l1->val <= l2->val) {
            tail->next = l1;
            l1 = l1->next;
        } else {
            tail->next = l2;
            l2 = l2->next;
        }
        tail = tail->next;
    }
    
    tail->next = l1 ? l1 : l2;
    
    return dummy.next;
}

ListNode* createList(int arr[], int n) {
    if(n == 0) return nullptr;
    
    ListNode* head = new ListNode(arr[0]);
    ListNode* current = head;
    
    for(int i = 1; i < n; i++) {
        current->next = new ListNode(arr[i]);
        current = current->next;
    }
    
    return head;
}

void printList(ListNode* head) {
    ListNode* temp = head;
    while(temp != nullptr) {
        cout << temp->val << " ";
        temp = temp->next;
    }
    cout << endl;
}

int main() {
    int arr1[] = {1, 2, 4};
    int arr2[] = {1, 3, 4};
    
    ListNode* l1 = createList(arr1, 3);
    ListNode* l2 = createList(arr2, 3);
    
    cout << "List 1: ";
    printList(l1);
    cout << "List 2: ";
    printList(l2);
    
    ListNode* merged = mergeTwoLists(l1, l2);
    
    cout << "Merged: ";
    printList(merged);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <stdlib.h>

struct ListNode {
    int val;
    struct ListNode* next;
};

struct ListNode* createNode(int val) {
    struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
    node->val = val;
    node->next = NULL;
    return node;
}

struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode dummy;
    dummy.next = NULL;
    struct ListNode* tail = &dummy;
    
    while(l1 && l2) {
        if(l1->val <= l2->val) {
            tail->next = l1;
            l1 = l1->next;
        } else {
            tail->next = l2;
            l2 = l2->next;
        }
        tail = tail->next;
    }
    
    tail->next = l1 ? l1 : l2;
    
    return dummy.next;
}

void printList(struct ListNode* head) {
    struct ListNode* temp = head;
    while(temp != NULL) {
        printf("%d ", temp->val);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct ListNode* l1 = createNode(1);
    l1->next = createNode(2);
    l1->next->next = createNode(4);
    
    struct ListNode* l2 = createNode(1);
    l2->next = createNode(3);
    l2->next->next = createNode(4);
    
    printf("List 1: ");
    printList(l1);
    printf("List 2: ");
    printList(l2);
    
    struct ListNode* merged = mergeTwoLists(l1, l2);
    
    printf("Merged: ");
    printList(merged);
    
    return 0;
}
```

### 6. Remove Nth Node from End

**Problem:** Remove the nth node from the end of a linked list.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

ListNode* removeNthFromEnd(ListNode* head, int n) {
    ListNode dummy(0);
    dummy.next = head;
    
    ListNode* first = &dummy;
    ListNode* second = &dummy;
    
    // Move first pointer n+1 steps ahead
    for(int i = 0; i <= n; i++) {
        first = first->next;
    }
    
    // Move both pointers until first reaches end
    while(first != nullptr) {
        first = first->next;
        second = second->next;
    }
    
    // Remove the nth node
    ListNode* nodeToDelete = second->next;
    second->next = second->next->next;
    delete nodeToDelete;
    
    return dummy.next;
}

ListNode* createList(int arr[], int n) {
    if(n == 0) return nullptr;
    
    ListNode* head = new ListNode(arr[0]);
    ListNode* current = head;
    
    for(int i = 1; i < n; i++) {
        current->next = new ListNode(arr[i]);
        current = current->next;
    }
    
    return head;
}

void printList(ListNode* head) {
    ListNode* temp = head;
    while(temp != nullptr) {
        cout << temp->val << " ";
        temp = temp->next;
    }
    cout << endl;
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    ListNode* head = createList(arr, 5);
    
    cout << "Original: ";
    printList(head);
    
    head = removeNthFromEnd(head, 2);
    
    cout << "After removing 2nd from end: ";
    printList(head);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <stdlib.h>

struct ListNode {
    int val;
    struct ListNode* next;
};

struct ListNode* createNode(int val) {
    struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
    node->val = val;
    node->next = NULL;
    return node;
}

struct ListNode* removeNthFromEnd(struct ListNode* head, int n) {
    struct ListNode dummy;
    dummy.next = head;
    
    struct ListNode* first = &dummy;
    struct ListNode* second = &dummy;
    
    for(int i = 0; i <= n; i++) {
        first = first->next;
    }
    
    while(first != NULL) {
        first = first->next;
        second = second->next;
    }
    
    struct ListNode* nodeToDelete = second->next;
    second->next = second->next->next;
    free(nodeToDelete);
    
    return dummy.next;
}

void printList(struct ListNode* head) {
    struct ListNode* temp = head;
    while(temp != NULL) {
        printf("%d ", temp->val);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct ListNode* head = createNode(1);
    head->next = createNode(2);
    head->next->next = createNode(3);
    head->next->next->next = createNode(4);
    head->next->next->next->next = createNode(5);
    
    printf("Original: ");
    printList(head);
    
    head = removeNthFromEnd(head, 2);
    
    printf("After removing 2nd from end: ");
    printList(head);
    
    return 0;
}
```

---

## Mathematical Problems (Complete 1-10)

### 1. Check Prime Number

**Problem:** Check if a given number is prime.

**C++ Solution:**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isPrime(int n) {
    if(n <= 1) return false;
    if(n <= 3) return true;
    if(n % 2 == 0 || n % 3 == 0) return false;
    
    // Check divisors from 5 to sqrt(n)
    for(int i = 5; i * i <= n; i += 6) {
        if(n % i == 0 || n % (i + 2) == 0) {
            return false;
        }
    }
    
    return true;
}

int main() {
    int num = 29;
    cout << num << " is " << (isPrime(num) ? "prime" : "not prime") << endl;
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <math.h>

int isPrime(int n) {
    if(n <= 1) return 0;
    if(n <= 3) return 1;
    if(n % 2 == 0 || n % 3 == 0) return 0;
    
    for(int i = 5; i * i <= n; i += 6) {
        if(n % i == 0 || n % (i + 2) == 0) {
            return 0;
        }
    }
    
    return 1;
}

int main() {
    int num = 29;
    printf("%d is %s\n", num, isPrime(num) ? "prime" : "not prime");
    return 0;
}
```

**Explanation:** Optimized algorithm checking divisors up to √n, skipping even numbers after 2. Time complexity: O(√n).

---

### 2. Fibonacci Series

**Problem:** Generate Fibonacci series up to n terms.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

// Iterative approach
void fibonacciIterative(int n) {
    if(n <= 0) return;
    
    int a = 0, b = 1;
    
    if(n >= 1) cout << a << " ";
    if(n >= 2) cout << b << " ";
    
    for(int i = 3; i <= n; i++) {
        int c = a + b;
        cout << c << " ";
        a = b;
        b = c;
    }
    cout << endl;
}

// Recursive approach
int fibonacciRecursive(int n) {
    if(n <= 1) return n;
    return fibonacciRecursive(n-1) + fibonacciRecursive(n-2);
}

int main() {
    int n = 10;
    cout << "Fibonacci series (iterative): ";
    fibonacciIterative(n);
    
    cout << "Fibonacci series (recursive): ";
    for(int i = 0; i < n; i++) {
        cout << fibonacciRecursive(i) << " ";
    }
    cout << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void fibonacciIterative(int n) {
    if(n <= 0) return;
    
    int a = 0, b = 1;
    
    if(n >= 1) printf("%d ", a);
    if(n >= 2) printf("%d ", b);
    
    for(int i = 3; i <= n; i++) {
        int c = a + b;
        printf("%d ", c);
        a = b;
        b = c;
    }
    printf("\n");
}

int fibonacciRecursive(int n) {
    if(n <= 1) return n;
    return fibonacciRecursive(n-1) + fibonacciRecursive(n-2);
}

int main() {
    int n = 10;
    printf("Fibonacci series: ");
    fibonacciIterative(n);
    return 0;
}
```

**Explanation:** Iterative approach is O(n) time and O(1) space. Recursive approach is O(2^n) time due to repeated calculations.

---

### 3. Factorial Calculation

**Problem:** Calculate factorial of a number using iterative and recursive methods.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

// Iterative approach
long long factorialIterative(int n) {
    if(n < 0) return -1; // Invalid input
    
    long long result = 1;
    for(int i = 1; i <= n; i++) {
        result *= i;
    }
    return result;
}

// Recursive approach
long long factorialRecursive(int n) {
    if(n < 0) return -1;
    if(n == 0 || n == 1) return 1;
    return n * factorialRecursive(n - 1);
}

int main() {
    int n = 5;
    
    cout << "Factorial of " << n << " (iterative): " 
         << factorialIterative(n) << endl;
    cout << "Factorial of " << n << " (recursive): " 
         << factorialRecursive(n) << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

long long factorialIterative(int n) {
    if(n < 0) return -1;
    
    long long result = 1;
    for(int i = 1; i <= n; i++) {
        result *= i;
    }
    return result;
}

long long factorialRecursive(int n) {
    if(n < 0) return -1;
    if(n == 0 || n == 1) return 1;
    return n * factorialRecursive(n - 1);
}

int main() {
    int n = 5;
    
    printf("Factorial of %d (iterative): %lld\n", n, factorialIterative(n));
    printf("Factorial of %d (recursive): %lld\n", n, factorialRecursive(n));
    
    return 0;
}
```

### 4. Fibonacci Series (Already covered above)

### 5. Armstrong Number

**Problem:** Check if a number is an Armstrong number (sum of cubes of digits equals the number).

**C++ Solution:**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isArmstrong(int n) {
    int original = n;
    int sum = 0;
    int digits = 0;
    
    // Count digits
    int temp = n;
    while(temp > 0) {
        digits++;
        temp /= 10;
    }
    
    // Calculate sum of powers
    temp = n;
    while(temp > 0) {
        int digit = temp % 10;
        sum += pow(digit, digits);
        temp /= 10;
    }
    
    return sum == original;
}

void printArmstrongNumbers(int limit) {
    cout << "Armstrong numbers up to " << limit << ": ";
    for(int i = 1; i <= limit; i++) {
        if(isArmstrong(i)) {
            cout << i << " ";
        }
    }
    cout << endl;
}

int main() {
    int num = 153;
    cout << num << " is " << (isArmstrong(num) ? "an Armstrong number" : "not an Armstrong number") << endl;
    
    printArmstrongNumbers(1000);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <math.h>

int isArmstrong(int n) {
    int original = n;
    int sum = 0;
    int digits = 0;
    
    int temp = n;
    while(temp > 0) {
        digits++;
        temp /= 10;
    }
    
    temp = n;
    while(temp > 0) {
        int digit = temp % 10;
        sum += pow(digit, digits);
        temp /= 10;
    }
    
    return sum == original;
}

int main() {
    int num = 153;
    printf("%d is %s\n", num, isArmstrong(num) ? "an Armstrong number" : "not an Armstrong number");
    
    printf("Armstrong numbers up to 1000: ");
    for(int i = 1; i <= 1000; i++) {
        if(isArmstrong(i)) {
            printf("%d ", i);
        }
    }
    printf("\n");
    
    return 0;
}
```

### 6. Perfect Number Check

**Problem:** Check if a number is perfect (sum of proper divisors equals the number).

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

bool isPerfect(int n) {
    if(n <= 1) return false;
    
    int sum = 1; // 1 is always a proper divisor
    
    for(int i = 2; i * i <= n; i++) {
        if(n % i == 0) {
            sum += i;
            if(i * i != n) { // Avoid adding square root twice
                sum += n / i;
            }
        }
    }
    
    return sum == n;
}

void findPerfectNumbers(int limit) {
    cout << "Perfect numbers up to " << limit << ": ";
    for(int i = 1; i <= limit; i++) {
        if(isPerfect(i)) {
            cout << i << " ";
        }
    }
    cout << endl;
}

int main() {
    int num = 28;
    cout << num << " is " << (isPerfect(num) ? "a perfect number" : "not a perfect number") << endl;
    
    findPerfectNumbers(10000);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int isPerfect(int n) {
    if(n <= 1) return 0;
    
    int sum = 1;
    
    for(int i = 2; i * i <= n; i++) {
        if(n % i == 0) {
            sum += i;
            if(i * i != n) {
                sum += n / i;
            }
        }
    }
    
    return sum == n;
}

int main() {
    int num = 28;
    printf("%d is %s\n", num, isPerfect(num) ? "a perfect number" : "not a perfect number");
    
    printf("Perfect numbers up to 10000: ");
    for(int i = 1; i <= 10000; i++) {
        if(isPerfect(i)) {
            printf("%d ", i);
        }
    }
    printf("\n");
    
    return 0;
}
```

### 7. Count Digits

**Problem:** Count the number of digits in a number.

**C++ Solution:**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int countDigits(int n) {
    if(n == 0) return 1;
    
    n = abs(n); // Handle negative numbers
    int count = 0;
    
    while(n > 0) {
        count++;
        n /= 10;
    }
    
    return count;
}

// Alternative method using logarithm
int countDigitsLog(int n) {
    if(n == 0) return 1;
    
    n = abs(n);
    return floor(log10(n)) + 1;
}

int main() {
    int num = 12345;
    cout << "Number of digits in " << num << ": " << countDigits(num) << endl;
    cout << "Using log method: " << countDigitsLog(num) << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <math.h>
#include <stdlib.h>

int countDigits(int n) {
    if(n == 0) return 1;
    
    n = abs(n);
    int count = 0;
    
    while(n > 0) {
        count++;
        n /= 10;
    }
    
    return count;
}

int countDigitsLog(int n) {
    if(n == 0) return 1;
    
    n = abs(n);
    return floor(log10(n)) + 1;
}

int main() {
    int num = 12345;
    printf("Number of digits in %d: %d\n", num, countDigits(num));
    printf("Using log method: %d\n", countDigitsLog(num));
    
    return 0;
}
```

### 8. Reverse Number

**Problem:** Reverse the digits of a number.

**C++ Solution:**
```cpp
#include <iostream>
#include <climits>
using namespace std;

int reverseNumber(int n) {
    int reversed = 0;
    bool isNegative = n < 0;
    n = abs(n);
    
    while(n > 0) {
        // Check for overflow
        if(reversed > INT_MAX / 10) {
            return 0; // Overflow
        }
        
        reversed = reversed * 10 + n % 10;
        n /= 10;
    }
    
    return isNegative ? -reversed : reversed;
}

int main() {
    int num = 12345;
    cout << "Original: " << num << endl;
    cout << "Reversed: " << reverseNumber(num) << endl;
    
    num = -123;
    cout << "Original: " << num << endl;
    cout << "Reversed: " << reverseNumber(num) << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <limits.h>
#include <stdlib.h>

int reverseNumber(int n) {
    int reversed = 0;
    int isNegative = n < 0;
    n = abs(n);
    
    while(n > 0) {
        if(reversed > INT_MAX / 10) {
            return 0;
        }
        
        reversed = reversed * 10 + n % 10;
        n /= 10;
    }
    
    return isNegative ? -reversed : reversed;
}

int main() {
    int num = 12345;
    printf("Original: %d\n", num);
    printf("Reversed: %d\n", reverseNumber(num));
    
    num = -123;
    printf("Original: %d\n", num);
    printf("Reversed: %d\n", reverseNumber(num));
    
    return 0;
}
```

### 9. Power Calculation

**Problem:** Calculate power of a number (x^y).

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

// Iterative approach
long long powerIterative(int base, int exp) {
    if(exp < 0) return 0; // Handle negative exponents
    
    long long result = 1;
    for(int i = 0; i < exp; i++) {
        result *= base;
    }
    return result;
}

// Optimized approach using exponentiation by squaring
long long powerOptimized(int base, int exp) {
    if(exp == 0) return 1;
    if(exp < 0) return 0;
    
    long long result = 1;
    long long currentPower = base;
    
    while(exp > 0) {
        if(exp % 2 == 1) {
            result *= currentPower;
        }
        currentPower *= currentPower;
        exp /= 2;
    }
    
    return result;
}

// Recursive approach
long long powerRecursive(int base, int exp) {
    if(exp == 0) return 1;
    if(exp < 0) return 0;
    if(exp == 1) return base;
    
    if(exp % 2 == 0) {
        long long temp = powerRecursive(base, exp / 2);
        return temp * temp;
    } else {
        return base * powerRecursive(base, exp - 1);
    }
}

int main() {
    int base = 2, exp = 10;
    
    cout << base << "^" << exp << " = " << powerIterative(base, exp) << " (iterative)" << endl;
    cout << base << "^" << exp << " = " << powerOptimized(base, exp) << " (optimized)" << endl;
    cout << base << "^" << exp << " = " << powerRecursive(base, exp) << " (recursive)" << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

long long powerIterative(int base, int exp) {
    if(exp < 0) return 0;
    
    long long result = 1;
    for(int i = 0; i < exp; i++) {
        result *= base;
    }
    return result;
}

long long powerOptimized(int base, int exp) {
    if(exp == 0) return 1;
    if(exp < 0) return 0;
    
    long long result = 1;
    long long currentPower = base;
    
    while(exp > 0) {
        if(exp % 2 == 1) {
            result *= currentPower;
        }
        currentPower *= currentPower;
        exp /= 2;
    }
    
    return result;
}

long long powerRecursive(int base, int exp) {
    if(exp == 0) return 1;
    if(exp < 0) return 0;
    if(exp == 1) return base;
    
    if(exp % 2 == 0) {
        long long temp = powerRecursive(base, exp / 2);
        return temp * temp;
    } else {
        return base * powerRecursive(base, exp - 1);
    }
}

int main() {
    int base = 2, exp = 10;
    
    printf("%d^%d = %lld (iterative)\n", base, exp, powerIterative(base, exp));
    printf("%d^%d = %lld (optimized)\n", base, exp, powerOptimized(base, exp));
    printf("%d^%d = %lld (recursive)\n", base, exp, powerRecursive(base, exp));
    
    return 0;
}
```

### 10. Check Perfect Square

**Problem:** Check if a number is a perfect square.

**C++ Solution:**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isPerfectSquare(int n) {
    if(n < 0) return false;
    
    int root = sqrt(n);
    return root * root == n;
}

// Binary search approach
bool isPerfectSquareBinary(int n) {
    if(n < 0) return false;
    if(n <= 1) return true;
    
    long long left = 1, right = n / 2;
    
    while(left <= right) {
        long long mid = left + (right - left) / 2;
        long long square = mid * mid;
        
        if(square == n) return true;
        else if(square < n) left = mid + 1;
        else right = mid - 1;
    }
    
    return false;
}

int main() {
    int num = 16;
    cout << num << " is " << (isPerfectSquare(num) ? "a perfect square" : "not a perfect square") << endl;
    
    cout << "Perfect squares up to 100: ";
    for(int i = 1; i <= 100; i++) {
        if(isPerfectSquare(i)) {
            cout << i << " ";
        }
    }
    cout << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <math.h>

int isPerfectSquare(int n) {
    if(n < 0) return 0;
    
    int root = sqrt(n);
    return root * root == n;
}

int isPerfectSquareBinary(int n) {
    if(n < 0) return 0;
    if(n <= 1) return 1;
    
    long long left = 1, right = n / 2;
    
    while(left <= right) {
        long long mid = left + (right - left) / 2;
        long long square = mid * mid;
        
        if(square == n) return 1;
        else if(square < n) left = mid + 1;
        else right = mid - 1;
    }
    
    return 0;
}

int main() {
    int num = 16;
    printf("%d is %s\n", num, isPerfectSquare(num) ? "a perfect square" : "not a perfect square");
    
    printf("Perfect squares up to 100: ");
    for(int i = 1; i <= 100; i++) {
        if(isPerfectSquare(i)) {
            printf("%d ", i);
        }
    }
    printf("\n");
    
    return 0;
}
```

---

## Sorting and Searching (Complete 1-6)

### 1. Binary Search

**Problem:** Implement binary search algorithm.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2; // Avoid overflow
        
        if(arr[mid] == target) {
            return mid;
        }
        else if(arr[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }
    
    return -1; // Not found
}

// Recursive version
int binarySearchRecursive(int arr[], int left, int right, int target) {
    if(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) return mid;
        if(arr[mid] > target) return binarySearchRecursive(arr, left, mid-1, target);
        return binarySearchRecursive(arr, mid+1, right, target);
    }
    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40, 50, 80};
    int n = 7;
    int target = 10;
    
    int result = binarySearch(arr, n, target);
    if(result != -1) {
        cout << "Element found at index: " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) {
            return mid;
        }
        else if(arr[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }
    
    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40, 50, 80};
    int n = 7;
    int target = 10;
    
    int result = binarySearch(arr, n, target);
    if(result != -1) {
        printf("Element found at index: %d\n", result);
    } else {
        printf("Element not found\n");
    }
    
    return 0;
}
```

**Explanation:** Divide and conquer algorithm that works on sorted arrays. Time complexity: O(log n), Space complexity: O(1) for iterative.

---

### 2. Bubble Sort

**Problem:** Implement bubble sort algorithm.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        bool swapped = false;
        
        for(int j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                // Swap elements
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;
            }
        }
        
        // If no swapping occurred, array is sorted
        if(!swapped) break;
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = 7;
    
    cout << "Original array: ";
    printArray(arr, n);
    
    bubbleSort(arr, n);
    
    cout << "Sorted array: ";
    printArray(arr, n);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void bubbleSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        int swapped = 0;
        
        for(int j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = 1;
            }
        }
        
        if(!swapped) break;
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = 7;
    
    printf("Original array: ");
    printArray(arr, n);
    
    bubbleSort(arr, n);
    
    printf("Sorted array: ");
    printArray(arr, n);
    
    return 0;
}
```

**Explanation:** Simple sorting algorithm that repeatedly steps through the list, compares adjacent elements and swaps them if in wrong order. Time complexity: O(n²).

---

### 3. Selection Sort

**Problem:** Implement selection sort algorithm.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        int minIndex = i;
        
        // Find minimum element in remaining array
        for(int j = i + 1; j < n; j++) {
            if(arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        
        // Swap minimum element with first element
        if(minIndex != i) {
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = 5;
    
    cout << "Original array: ";
    printArray(arr, n);
    
    selectionSort(arr, n);
    
    cout << "Sorted array: ";
    printArray(arr, n);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void selectionSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        int minIndex = i;
        
        for(int j = i + 1; j < n; j++) {
            if(arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        
        if(minIndex != i) {
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = 5;
    
    printf("Original array: ");
    printArray(arr, n);
    
    selectionSort(arr, n);
    
    printf("Sorted array: ");
    printArray(arr, n);
    
    return 0;
}
```

### 4. Insertion Sort

**Problem:** Implement insertion sort algorithm.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        
        // Move elements greater than key one position ahead
        while(j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        
        arr[j + 1] = key;
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = 5;
    
    cout << "Original array: ";
    printArray(arr, n);
    
    insertionSort(arr, n);
    
    cout << "Sorted array: ";
    printArray(arr, n);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void insertionSort(int arr[], int n) {
    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        
        while(j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        
        arr[j + 1] = key;
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = 5;
    
    printf("Original array: ");
    printArray(arr, n);
    
    insertionSort(arr, n);
    
    printf("Sorted array: ");
    printArray(arr, n);
    
    return 0;
}
```

### 5. Find Element in Rotated Array

**Problem:** Find an element in a rotated sorted array.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

int searchRotated(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) {
            return mid;
        }
        
        // Check which half is sorted
        if(arr[left] <= arr[mid]) {
            // Left half is sorted
            if(target >= arr[left] && target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        } else {
            // Right half is sorted
            if(target > arr[mid] && target <= arr[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    return -1; // Not found
}

int main() {
    int arr[] = {4, 5, 6, 7, 0, 1, 2};
    int n = 7;
    int target = 0;
    
    int result = searchRotated(arr, n, target);
    
    if(result != -1) {
        cout << "Element " << target << " found at index " << result << endl;
    } else {
        cout << "Element " << target << " not found" << endl;
    }
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int searchRotated(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) {
            return mid;
        }
        
        if(arr[left] <= arr[mid]) {
            if(target >= arr[left] && target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        } else {
            if(target > arr[mid] && target <= arr[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    return -1;
}

int main() {
    int arr[] = {4, 5, 6, 7, 0, 1, 2};
    int n = 7;
    int target = 0;
    
    int result = searchRotated(arr, n, target);
    
    if(result != -1) {
        printf("Element %d found at index %d\n", target, result);
    } else {
        printf("Element %d not found\n", target);
    }
    
    return 0;
}
```

### 6. Find Square Root

**Problem:** Find the square root of a number using binary search.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

int squareRoot(int n) {
    if(n == 0 || n == 1) return n;
    
    int left = 1, right = n / 2;
    int result = 0;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(mid == n / mid) {
            return mid;
        } else if(mid < n / mid) {
            result = mid;
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

// Alternative approach using long long to avoid overflow
int squareRootSafe(int n) {
    if(n == 0 || n == 1) return n;
    
    long long left = 1, right = n / 2;
    int result = 0;
    
    while(left <= right) {
        long long mid = left + (right - left) / 2;
        long long square = mid * mid;
        
        if(square == n) {
            return mid;
        } else if(square < n) {
            result = mid;
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

int main() {
    int n = 8;
    cout << "Square root of " << n << " is " << squareRoot(n) << endl;
    
    n = 16;
    cout << "Square root of " << n << " is " << squareRoot(n) << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int squareRoot(int n) {
    if(n == 0 || n == 1) return n;
    
    long long left = 1, right = n / 2;
    int result = 0;
    
    while(left <= right) {
        long long mid = left + (right - left) / 2;
        long long square = mid * mid;
        
        if(square == n) {
            return mid;
        } else if(square < n) {
            result = mid;
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

int main() {
    int n = 8;
    printf("Square root of %d is %d\n", n, squareRoot(n));
    
    n = 16;
    printf("Square root of %d is %d\n", n, squareRoot(n));
    
    return 0;
}
```

---

## Basic Programming (Complete 1-6)

### 1. Swap Two Numbers

**Problem:** Swap two numbers without using a temporary variable.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

// Method 1: Using arithmetic operations
void swapArithmetic(int &a, int &b) {
    if(a != b) { // Handle case when a and b are same
        a = a + b;
        b = a - b;
        a = a - b;
    }
}

// Method 2: Using XOR
void swapXOR(int &a, int &b) {
    if(a != b) {
        a = a ^ b;
        b = a ^ b;
        a = a ^ b;
    }
}

// Method 3: Using temporary variable (most common)
void swapTemp(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x = 10, y = 20;
    
    cout << "Before swap: x = " << x << ", y = " << y << endl;
    swapTemp(x, y);
    cout << "After swap: x = " << x << ", y = " << y << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void swapArithmetic(int *a, int *b) {
    if(*a != *b) {
        *a = *a + *b;
        *b = *a - *b;
        *a = *a - *b;
    }
}

void swapXOR(int *a, int *b) {
    if(*a != *b) {
        *a = *a ^ *b;
        *b = *a ^ *b;
        *a = *a ^ *b;
    }
}

void swapTemp(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 10, y = 20;
    
    printf("Before swap: x = %d, y = %d\n", x, y);
    swapTemp(&x, &y);
    printf("After swap: x = %d, y = %d\n", x, y);
    
    return 0;
}
```

**Explanation:** Multiple methods exist. Temporary variable is most reliable. Arithmetic method can cause overflow. XOR method works but avoid when numbers might be same.

---

### 2. Check Odd/Even

**Problem:** Check if a number is odd or even.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

// Method 1: Using modulo operator
bool isEven(int n) {
    return n % 2 == 0;
}

// Method 2: Using bitwise AND
bool isEvenBitwise(int n) {
    return (n & 1) == 0;
}

void checkOddEven(int n) {
    if(isEven(n)) {
        cout << n << " is even" << endl;
    } else {
        cout << n << " is odd" << endl;
    }
}

int main() {
    int numbers[] = {2, 7, 10, 15, 20};
    int size = 5;
    
    for(int i = 0; i < size; i++) {
        checkOddEven(numbers[i]);
    }
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int isEven(int n) {
    return n % 2 == 0;
}

int isEvenBitwise(int n) {
    return (n & 1) == 0;
}

void checkOddEven(int n) {
    if(isEven(n)) {
        printf("%d is even\n", n);
    } else {
        printf("%d is odd\n", n);
    }
}

int main() {
    int numbers[] = {2, 7, 10, 15, 20};
    int size = 5;
    
    for(int i = 0; i < size; i++) {
        checkOddEven(numbers[i]);
    }
    
    return 0;
}
```

### 3. Find Largest of 3 Numbers

**Problem:** Find the largest among three numbers.

**C++ Solution:**
```cpp
#include <iostream>
#include <algorithm>
using namespace std;

// Method 1: Using if-else
int findMax3(int a, int b, int c) {
    if(a >= b && a >= c) {
        return a;
    } else if(b >= a && b >= c) {
        return b;
    } else {
        return c;
    }
}

// Method 2: Using ternary operator
int findMax3Ternary(int a, int b, int c) {
    return (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c);
}

// Method 3: Using built-in max function
int findMax3Builtin(int a, int b, int c) {
    return max({a, b, c});
}

int main() {
    int a = 10, b = 25, c = 15;
    
    cout << "Numbers: " << a << ", " << b << ", " << c << endl;
    cout << "Largest (if-else): " << findMax3(a, b, c) << endl;
    cout << "Largest (ternary): " << findMax3Ternary(a, b, c) << endl;
    cout << "Largest (builtin): " << findMax3Builtin(a, b, c) << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

int findMax3(int a, int b, int c) {
    if(a >= b && a >= c) {
        return a;
    } else if(b >= a && b >= c) {
        return b;
    } else {
        return c;
    }
}

int findMax3Ternary(int a, int b, int c) {
    return (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c);
}

int main() {
    int a = 10, b = 25, c = 15;
    
    printf("Numbers: %d, %d, %d\n", a, b, c);
    printf("Largest (if-else): %d\n", findMax3(a, b, c));
    printf("Largest (ternary): %d\n", findMax3Ternary(a, b, c));
    
    return 0;
}
```

### 4. Sum of Digits

**Problem:** Calculate the sum of digits of a number.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

int sumOfDigits(int n) {
    n = abs(n); // Handle negative numbers
    int sum = 0;
    
    while(n > 0) {
        sum += n % 10;
        n /= 10;
    }
    
    return sum;
}

// Recursive approach
int sumOfDigitsRecursive(int n) {
    n = abs(n);
    if(n == 0) return 0;
    return n % 10 + sumOfDigitsRecursive(n / 10);
}

int main() {
    int num = 12345;
    cout << "Number: " << num << endl;
    cout << "Sum of digits (iterative): " << sumOfDigits(num) << endl;
    cout << "Sum of digits (recursive): " << sumOfDigitsRecursive(num) << endl;
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>
#include <stdlib.h>

int sumOfDigits(int n) {
    n = abs(n);
    int sum = 0;
    
    while(n > 0) {
        sum += n % 10;
        n /= 10;
    }
    
    return sum;
}

int sumOfDigitsRecursive(int n) {
    n = abs(n);
    if(n == 0) return 0;
    return n % 10 + sumOfDigitsRecursive(n / 10);
}

int main() {
    int num = 12345;
    printf("Number: %d\n", num);
    printf("Sum of digits (iterative): %d\n", sumOfDigits(num));
    printf("Sum of digits (recursive): %d\n", sumOfDigitsRecursive(num));
    
    return 0;
}
```

### 5. Pattern Printing

**Problem:** Print various patterns like stars, numbers, etc.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

// Pattern 1: Right triangle of stars
void printStarTriangle(int n) {
    cout << "Star Triangle:" << endl;
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= i; j++) {
            cout << "* ";
        }
        cout << endl;
    }
    cout << endl;
}

// Pattern 2: Number triangle
void printNumberTriangle(int n) {
    cout << "Number Triangle:" << endl;
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= i; j++) {
            cout << j << " ";
        }
        cout << endl;
    }
    cout << endl;
}

// Pattern 3: Pyramid
void printPyramid(int n) {
    cout << "Pyramid:" << endl;
    for(int i = 1; i <= n; i++) {
        // Print spaces
        for(int j = 1; j <= n - i; j++) {
            cout << " ";
        }
        // Print stars
        for(int j = 1; j <= 2 * i - 1; j++) {
            cout << "*";
        }
        cout << endl;
    }
    cout << endl;
}

// Pattern 4: Diamond
void printDiamond(int n) {
    cout << "Diamond:" << endl;
    // Upper half
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= n - i; j++) {
            cout << " ";
        }
        for(int j = 1; j <= 2 * i - 1; j++) {
            cout << "*";
        }
        cout << endl;
    }
    // Lower half
    for(int i = n - 1; i >= 1; i--) {
        for(int j = 1; j <= n - i; j++) {
            cout << " ";
        }
        for(int j = 1; j <= 2 * i - 1; j++) {
            cout << "*";
        }
        cout << endl;
    }
    cout << endl;
}

int main() {
    int n = 5;
    
    printStarTriangle(n);
    printNumberTriangle(n);
    printPyramid(n);
    printDiamond(n);
    
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

void printStarTriangle(int n) {
    printf("Star Triangle:\n");
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }
    printf("\n");
}

void printNumberTriangle(int n) {
    printf("Number Triangle:\n");
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= i; j++) {
            printf("%d ", j);
        }
        printf("\n");
    }
    printf("\n");
}

void printPyramid(int n) {
    printf("Pyramid:\n");
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= n - i; j++) {
            printf(" ");
        }
        for(int j = 1; j <= 2 * i - 1; j++) {
            printf("*");
        }
        printf("\n");
    }
    printf("\n");
}

void printDiamond(int n) {
    printf("Diamond:\n");
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= n - i; j++) {
            printf(" ");
        }
        for(int j = 1; j <= 2 * i - 1; j++) {
            printf("*");
        }
        printf("\n");
    }
    for(int i = n - 1; i >= 1; i--) {
        for(int j = 1; j <= n - i; j++) {
            printf(" ");
        }
        for(int j = 1; j <= 2 * i - 1; j++) {
            printf("*");
        }
        printf("\n");
    }
    printf("\n");
}

int main() {
    int n = 5;
    
    printStarTriangle(n);
    printNumberTriangle(n);
    printPyramid(n);
    printDiamond(n);
    
    return 0;
}
```

### 6. Calculator Implementation

**Problem:** Implement a basic calculator with four operations.

**C++ Solution:**
```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    double add(double a, double b) {
        return a + b;
    }
    
    double subtract(double a, double b) {
        return a - b;
    }
    
    double multiply(double a, double b) {
        return a * b;
    }
    
    double divide(double a, double b) {
        if(b == 0) {
            cout << "Error: Division by zero!" << endl;
            return 0;
        }
        return a / b;
    }
    
    void displayMenu() {
        cout << "\n=== Calculator Menu ===" << endl;
        cout << "1. Addition (+)" << endl;
        cout << "2. Subtraction (-)" << endl;
        cout << "3. Multiplication (*)" << endl;
        cout << "4. Division (/)" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice: ";
    }
    
    void run() {
        int choice;
        double num1, num2, result;
        
        do {
            displayMenu();
            cin >> choice;
            
            if(choice >= 1 && choice <= 4) {
                cout << "Enter first number: ";
                cin >> num1;
                cout << "Enter second number: ";
                cin >> num2;
                
                switch(choice) {
                    case 1:
                        result = add(num1, num2);
                        cout << num1 << " + " << num2 << " = " << result << endl;
                        break;
                    case 2:
                        result = subtract(num1, num2);
                        cout << num1 << " - " << num2 << " = " << result << endl;
                        break;
                    case 3:
                        result = multiply(num1, num2);
                        cout << num1 << " * " << num2 << " = " << result << endl;
                        break;
                    case 4:
                        result = divide(num1, num2);
                        if(num2 != 0) {
                            cout << num1 << " / " << num2 << " = " << result << endl;
                        }
                        break;
                }
            } else if(choice == 5) {
                cout << "Thank you for using the calculator!" << endl;
            } else {
                cout << "Invalid choice! Please try again." << endl;
            }
            
        } while(choice != 5);
    }
};

int main() {
    Calculator calc;
    calc.run();
    return 0;
}
```

**C Solution:**
```c
#include <stdio.h>

double add(double a, double b) {
    return a + b;
}

double subtract(double a, double b) {
    return a - b;
}

double multiply(double a, double b) {
    return a * b;
}

double divide(double a, double b) {
    if(b == 0) {
        printf("Error: Division by zero!\n");
        return 0;
    }
    return a / b;
}

void displayMenu() {
    printf("\n=== Calculator Menu ===\n");
    printf("1. Addition (+)\n");
    printf("2. Subtraction (-)\n");
    printf("3. Multiplication (*)\n");
    printf("4. Division (/)\n");
    printf("5. Exit\n");
    printf("Enter your choice: ");
}

int main() {
    int choice;
    double num1, num2, result;
    
    do {
        displayMenu();
        scanf("%d", &choice);
        
        if(choice >= 1 && choice <= 4) {
            printf("Enter first number: ");
            scanf("%lf", &num1);
            printf("Enter second number: ");
            scanf("%lf", &num2);
            
            switch(choice) {
                case 1:
                    result = add(num1, num2);
                    printf("%.2f + %.2f = %.2f\n", num1, num2, result);
                    break;
                case 2:
                    result = subtract(num1, num2);
                    printf("%.2f - %.2f = %.2f\n", num1, num2, result);
                    break;
                case 3:
                    result = multiply(num1, num2);
                    printf("%.2f * %.2f = %.2f\n", num1, num2, result);
                    break;
                case 4:
                    result = divide(num1, num2);
                    if(num2 != 0) {
                        printf("%.2f / %.2f = %.2f\n", num1, num2, result);
                    }
                    break;
            }
        } else if(choice == 5) {
            printf("Thank you for using the calculator!\n");
        } else {
            printf("Invalid choice! Please try again.\n");
        }
        
    } while(choice != 5);
    
    return 0;
}
```

---

## 🎯 Final Tips for Success

### Practice Strategy:
1. **Day 1-3**: Focus on Arrays and Strings (most common)
2. **Day 4-6**: Master Mathematical problems
3. **Day 7-9**: Learn Linked Lists and Sorting
4. **Day 10-14**: Mixed practice and mock interviews

### Interview Day Tips:
1. **Read the problem carefully** - don't rush
2. **Ask clarifying questions** about edge cases
3. **Explain your approach** before coding
4. **Start with brute force**, then optimize
5. **Test your code** with sample inputs
6. **Handle edge cases** like empty arrays, null pointers

### Common Pitfalls to Avoid:
- **Array bounds** - always check indices
- **Integer overflow** - use long long when needed
- **Memory management** - free allocated memory in C
- **Null pointer checks** - especially for linked lists
- **Loop conditions** - avoid off-by-one errors

**Good luck with your interviews! Practice these problems daily and you'll definitely improve your problem-solving skills.** 🚀

---

*Remember: Consistency is key. Practice 2-3 problems every day and review your mistakes!*