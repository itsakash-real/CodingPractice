# IBM Associate System Engineer - Coding Question Bank (100 Questions)

## Category 1: Basic Logic & Mathematics (15 questions)

### Q1: Check if a Number is Prime
**Problem:** Determine if a given number N is prime.

**Input Format:** Single integer N

**Output Format:** Print "YES" if prime, "NO" otherwise

**Example:**
```
Input: 17
Output: YES

Input: 15
Output: NO
```

**Constraints:** 1 ≤ N ≤ 10^6

**Explanation:** A prime number has exactly two divisors: 1 and itself. Check divisibility from 2 to √N.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    if (n <= 1) {
        cout << "NO" << endl;
        return 0;
    }
    
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            cout << "NO" << endl;
            return 0;
        }
    }
    
    cout << "YES" << endl;
    return 0;
}
```
**Time Complexity:** O(√N)  
**Space Complexity:** O(1)

---

### Q2: Count Digits in a Number
**Problem:** Count the number of digits in a given integer N.

**Input Format:** Single integer N

**Output Format:** Print count of digits

**Example:**
```
Input: 12345
Output: 5

Input: 0
Output: 1
```

**Constraints:** -10^9 ≤ N ≤ 10^9

**Explanation:** Convert to absolute value and repeatedly divide by 10 until number becomes 0.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long n;
    cin >> n;
    
    if (n == 0) {
        cout << 1 << endl;
        return 0;
    }
    
    n = abs(n);
    int count = 0;
    
    while (n > 0) {
        count++;
        n /= 10;
    }
    
    cout << count << endl;
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(1)

---

### Q3: Reverse a Number
**Problem:** Reverse the digits of an integer N.

**Input Format:** Single integer N

**Output Format:** Print reversed number

**Example:**
```
Input: 12345
Output: 54321

Input: -123
Output: -321
```

**Constraints:** -10^9 ≤ N ≤ 10^9

**Explanation:** Extract last digit repeatedly and build reversed number.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long n;
    cin >> n;
    
    long long rev = 0;
    bool negative = n < 0;
    n = abs(n);
    
    while (n > 0) {
        rev = rev * 10 + n % 10;
        n /= 10;
    }
    
    if (negative) rev = -rev;
    
    cout << rev << endl;
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(1)

---

### Q4: GCD of Two Numbers
**Problem:** Find the Greatest Common Divisor of two numbers A and B.

**Input Format:** Two integers A and B

**Output Format:** Print GCD

**Example:**
```
Input: 24 36
Output: 12

Input: 17 19
Output: 1
```

**Constraints:** 1 ≤ A, B ≤ 10^9

**Explanation:** Use Euclidean algorithm: GCD(a, b) = GCD(b, a % b)

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long a, b;
    cin >> a >> b;
    
    while (b != 0) {
        long long temp = b;
        b = a % b;
        a = temp;
    }
    
    cout << a << endl;
    return 0;
}
```
**Time Complexity:** O(log(min(A, B)))  
**Space Complexity:** O(1)

---

### Q5: LCM of Two Numbers
**Problem:** Find the Least Common Multiple of two numbers A and B.

**Input Format:** Two integers A and B

**Output Format:** Print LCM

**Example:**
```
Input: 12 18
Output: 36

Input: 5 7
Output: 35
```

**Constraints:** 1 ≤ A, B ≤ 10^6

**Explanation:** LCM(a, b) = (a * b) / GCD(a, b)

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

long long gcd(long long a, long long b) {
    while (b != 0) {
        long long temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int main() {
    long long a, b;
    cin >> a >> b;
    
    long long lcm = (a * b) / gcd(a, b);
    
    cout << lcm << endl;
    return 0;
}
```
**Time Complexity:** O(log(min(A, B)))  
**Space Complexity:** O(1)

---

### Q6: Factorial of N
**Problem:** Calculate factorial of a number N.

**Input Format:** Single integer N

**Output Format:** Print factorial of N

**Example:**
```
Input: 5
Output: 120

Input: 0
Output: 1
```

**Constraints:** 0 ≤ N ≤ 20

**Explanation:** Factorial N! = 1 * 2 * 3 * ... * N

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    long long fact = 1;
    
    for (int i = 2; i <= n; i++) {
        fact *= i;
    }
    
    cout << fact << endl;
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(1)

---

### Q7: Check Armstrong Number
**Problem:** Check if a number is an Armstrong number (sum of cubes of digits equals the number).

**Input Format:** Single integer N

**Output Format:** Print "YES" if Armstrong, "NO" otherwise

**Example:**
```
Input: 153
Output: YES (1³ + 5³ + 3³ = 153)

Input: 123
Output: NO
```

**Constraints:** 1 ≤ N ≤ 10^6

**Explanation:** Extract each digit, cube it, and sum all cubes.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    int original = n;
    int sum = 0;
    
    while (n > 0) {
        int digit = n % 10;
        sum += digit * digit * digit;
        n /= 10;
    }
    
    if (sum == original) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(1)

---

### Q8: Sum of Digits
**Problem:** Find the sum of all digits of a number N.

**Input Format:** Single integer N

**Output Format:** Print sum of digits

**Example:**
```
Input: 12345
Output: 15

Input: 999
Output: 27
```

**Constraints:** 0 ≤ N ≤ 10^9

**Explanation:** Extract each digit and add to sum.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long n;
    cin >> n;
    
    int sum = 0;
    
    while (n > 0) {
        sum += n % 10;
        n /= 10;
    }
    
    cout << sum << endl;
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(1)

---

### Q9: Check Palindrome Number
**Problem:** Check if a number reads the same forwards and backwards.

**Input Format:** Single integer N

**Output Format:** Print "YES" if palindrome, "NO" otherwise

**Example:**
```
Input: 12321
Output: YES

Input: 12345
Output: NO
```

**Constraints:** 0 ≤ N ≤ 10^9

**Explanation:** Reverse the number and compare with original.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long n;
    cin >> n;
    
    long long original = n;
    long long rev = 0;
    
    while (n > 0) {
        rev = rev * 10 + n % 10;
        n /= 10;
    }
    
    if (rev == original) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(1)

---

### Q10: Fibonacci Number at Position N
**Problem:** Find the Nth Fibonacci number (0-indexed).

**Input Format:** Single integer N

**Output Format:** Print Nth Fibonacci number

**Example:**
```
Input: 6
Output: 8 (0, 1, 1, 2, 3, 5, 8)

Input: 10
Output: 55
```

**Constraints:** 0 ≤ N ≤ 40

**Explanation:** Use iterative approach to avoid stack overflow.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    if (n == 0) {
        cout << 0 << endl;
        return 0;
    }
    if (n == 1) {
        cout << 1 << endl;
        return 0;
    }
    
    long long a = 0, b = 1;
    
    for (int i = 2; i <= n; i++) {
        long long c = a + b;
        a = b;
        b = c;
    }
    
    cout << b << endl;
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(1)

---

### Q11: Power of a Number
**Problem:** Calculate A raised to power B (A^B).

**Input Format:** Two integers A and B

**Output Format:** Print A^B

**Example:**
```
Input: 2 10
Output: 1024

Input: 5 3
Output: 125
```

**Constraints:** 1 ≤ A ≤ 10, 0 ≤ B ≤ 20

**Explanation:** Use iterative multiplication or fast exponentiation.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long a, b;
    cin >> a >> b;
    
    long long result = 1;
    
    for (int i = 0; i < b; i++) {
        result *= a;
    }
    
    cout << result << endl;
    return 0;
}
```
**Time Complexity:** O(B)  
**Space Complexity:** O(1)

---

### Q12: Sum of First N Natural Numbers
**Problem:** Calculate sum of first N natural numbers.

**Input Format:** Single integer N

**Output Format:** Print sum

**Example:**
```
Input: 5
Output: 15 (1+2+3+4+5)

Input: 100
Output: 5050
```

**Constraints:** 1 ≤ N ≤ 10^6

**Explanation:** Use formula: N * (N + 1) / 2

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long n;
    cin >> n;
    
    long long sum = n * (n + 1) / 2;
    
    cout << sum << endl;
    return 0;
}
```
**Time Complexity:** O(1)  
**Space Complexity:** O(1)

---

### Q13: Count Prime Numbers up to N
**Problem:** Count how many prime numbers exist from 1 to N.

**Input Format:** Single integer N

**Output Format:** Print count of primes

**Example:**
```
Input: 10
Output: 4 (2, 3, 5, 7)

Input: 20
Output: 8
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use Sieve of Eratosthenes for efficient counting.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    if (n < 2) {
        cout << 0 << endl;
        return 0;
    }
    
    vector<bool> prime(n + 1, true);
    prime[0] = prime[1] = false;
    
    for (int i = 2; i * i <= n; i++) {
        if (prime[i]) {
            for (int j = i * i; j <= n; j += i) {
                prime[j] = false;
            }
        }
    }
    
    int count = 0;
    for (int i = 2; i <= n; i++) {
        if (prime[i]) count++;
    }
    
    cout << count << endl;
    return 0;
}
```
**Time Complexity:** O(N log log N)  
**Space Complexity:** O(N)

---

### Q14: Print All Divisors of N
**Problem:** Print all divisors of a number N in ascending order.

**Input Format:** Single integer N

**Output Format:** Print divisors space-separated

**Example:**
```
Input: 12
Output: 1 2 3 4 6 12

Input: 7
Output: 1 7
```

**Constraints:** 1 ≤ N ≤ 10^6

**Explanation:** Check from 1 to √N, add both i and N/i as divisors.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    set<int> divisors;
    
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            divisors.insert(i);
            divisors.insert(n / i);
        }
    }
    
    for (int d : divisors) {
        cout << d << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(√N)  
**Space Complexity:** O(number of divisors)

---

### Q15: Check Perfect Number
**Problem:** Check if N equals the sum of its proper divisors (excluding N itself).

**Input Format:** Single integer N

**Output Format:** Print "YES" if perfect, "NO" otherwise

**Example:**
```
Input: 28
Output: YES (1+2+4+7+14 = 28)

Input: 12
Output: NO
```

**Constraints:** 1 ≤ N ≤ 10^6

**Explanation:** Find all divisors except N, sum them, and compare.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    if (n <= 1) {
        cout << "NO" << endl;
        return 0;
    }
    
    int sum = 1;
    
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            sum += i;
            if (i != n / i) {
                sum += n / i;
            }
        }
    }
    
    if (sum == n) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(√N)  
**Space Complexity:** O(1)

---

## Category 2: Arrays (20 questions)

### Q16: Find Maximum Element in Array
**Problem:** Find the maximum element in an array.

**Input Format:**
- First line: N (size of array)
- Second line: N space-separated integers

**Output Format:** Print maximum element

**Example:**
```
Input:
5
3 7 2 9 4
Output: 9
```

**Constraints:** 1 ≤ N ≤ 10^5, -10^9 ≤ arr[i] ≤ 10^9

**Explanation:** Iterate through array maintaining maximum value seen.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int maxElem = arr[0];
    for (int i = 1; i < n; i++) {
        maxElem = max(maxElem, arr[i]);
    }
    
    cout << maxElem << endl;
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q17: Reverse an Array
**Problem:** Reverse the given array.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print reversed array

**Example:**
```
Input:
5
1 2 3 4 5
Output: 5 4 3 2 1
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use two pointers from start and end, swap and move inward.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int left = 0, right = n - 1;
    while (left < right) {
        swap(arr[left], arr[right]);
        left++;
        right--;
    }
    
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q18: Find Second Largest Element
**Problem:** Find the second largest distinct element in array.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print second largest or -1 if doesn't exist

**Example:**
```
Input:
5
3 7 2 9 4
Output: 7

Input:
3
5 5 5
Output: -1
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Track largest and second largest in single pass.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int first = INT_MIN, second = INT_MIN;
    
    for (int i = 0; i < n; i++) {
        if (arr[i] > first) {
            second = first;
            first = arr[i];
        } else if (arr[i] > second && arr[i] != first) {
            second = arr[i];
        }
    }
    
    if (second == INT_MIN) {
        cout << -1 << endl;
    } else {
        cout << second << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q19: Rotate Array by K Positions
**Problem:** Rotate array to the right by K positions.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print rotated array

**Example:**
```
Input:
5 2
1 2 3 4 5
Output: 4 5 1 2 3
```

**Constraints:** 1 ≤ N ≤ 10^5, 0 ≤ K ≤ 10^9

**Explanation:** Use reverse technique: reverse whole, then first K, then remaining.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    k = k % n;
    
    reverse(arr.begin(), arr.end());
    reverse(arr.begin(), arr.begin() + k);
    reverse(arr.begin() + k, arr.end());
    
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q20: Check if Array is Sorted
**Problem:** Check if array is sorted in non-decreasing order.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
5
1 2 3 4 5
Output: YES

Input:
4
1 3 2 4
Output: NO
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Compare each element with next element.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    bool sorted = true;
    for (int i = 0; i < n - 1; i++) {
        if (arr[i] > arr[i + 1]) {
            sorted = false;
            break;
        }
    }
    
    if (sorted) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q21: Remove Duplicates from Sorted Array
**Problem:** Remove duplicates from a sorted array in-place and return new length.

**Input Format:**
- First line: N
- Second line: N sorted integers

**Output Format:** Print new length and modified array

**Example:**
```
Input:
6
1 1 2 2 3 4
Output: 
4
1 2 3 4
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use two pointers: one for position, one for iteration.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    if (n == 0) {
        cout << 0 << endl;
        return 0;
    }
    
    int j = 0;
    for (int i = 1; i < n; i++) {
        if (arr[i] != arr[j]) {
            j++;
            arr[j] = arr[i];
        }
    }
    
    cout << j + 1 << endl;
    for (int i = 0; i <= j; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q22: Move Zeros to End
**Problem:** Move all zeros to the end while maintaining relative order of non-zero elements.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print modified array

**Example:**
```
Input:
6
0 1 0 3 12 0
Output: 1 3 12 0 0 0
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use two pointers to place non-zero elements at front.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int j = 0;
    for (int i = 0; i < n; i++) {
        if (arr[i] != 0) {
            arr[j] = arr[i];
            j++;
        }
    }
    
    while (j < n) {
        arr[j] = 0;
        j++;
    }
    
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q23: Find Missing Number
**Problem:** Array contains N-1 distinct numbers from 1 to N. Find the missing number.

**Input Format:**
- First line: N
- Second line: N-1 integers

**Output Format:** Print missing number

**Example:**
```
Input:
5
1 2 4 5
Output: 3
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Sum of 1 to N minus sum of array gives missing number.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    long long totalSum = (long long)n * (n + 1) / 2;
    long long arraySum = 0;
    
    for (int i = 0; i < n - 1; i++) {
        int x;
        cin >> x;
        arraySum += x;
    }
    
    cout << totalSum - arraySum << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(1)

---

### Q24: Find Pair with Given Sum
**Problem:** Check if there exists a pair in array with sum equal to K.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
5 9
1 4 5 7 2
Output: YES (4 + 5 = 9)
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use hash set to check if complement exists.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_set<int> seen;
    bool found = false;
    
    for (int i = 0; i < n; i++) {
        if (seen.count(k - arr[i])) {
            found = true;
            break;
        }
        seen.insert(arr[i]);
    }
    
    if (found) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q25: Kadane's Algorithm - Maximum Subarray Sum
**Problem:** Find maximum sum of contiguous subarray.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print maximum sum

**Example:**
```
Input:
6
-2 1 -3 4 -1 2
Output: 5 (subarray [4, -1, 2])
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Track current sum, reset if negative, track global max.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    long long maxSum = arr[0];
    long long currentSum = arr[0];
    
    for (int i = 1; i < n; i++) {
        currentSum = max((long long)arr[i], currentSum + arr[i]);
        maxSum = max(maxSum, currentSum);
    }
    
    cout << maxSum << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q26: Stock Buy and Sell - Single Transaction
**Problem:** Find maximum profit from buying and selling stock once.

**Input Format:**
- First line: N
- Second line: N prices

**Output Format:** Print maximum profit

**Example:**
```
Input:
6
7 1 5 3 6 4
Output: 5 (buy at 1, sell at 6)
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Track minimum price seen so far, calculate profit at each step.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> prices(n);
    for (int i = 0; i < n; i++) {
        cin >> prices[i];
    }
    
    int minPrice = prices[0];
    int maxProfit = 0;
    
    for (int i = 1; i < n; i++) {
        maxProfit = max(maxProfit, prices[i] - minPrice);
        minPrice = min(minPrice, prices[i]);
    }
    
    cout << maxProfit << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q27: Leaders in Array
**Problem:** Find all leaders in array. An element is a leader if it's greater than all elements to its right.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print leaders from left to right

**Example:**
```
Input:
6
16 17 4 3 5 2
Output: 17 5 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Traverse from right, track maximum seen so far.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    vector<int> leaders;
    int maxRight = arr[n - 1];
    leaders.push_back(maxRight);
    
    for (int i = n - 2; i >= 0; i--) {
        if (arr[i] > maxRight) {
            leaders.push_back(arr[i]);
            maxRight = arr[i];
        }
    }
    
    reverse(leaders.begin(), leaders.end());
    
    for (int leader : leaders) {
        cout << leader << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q28: Equilibrium Index
**Problem:** Find an index where sum of left elements equals sum of right elements.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print equilibrium index (0-based) or -1

**Example:**
```
Input:
7
-7 1 5 2 -4 3 0
Output: 3 (sum of left = -7+1+5 = -1, sum of right = -4+3+0 = -1)
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Calculate total sum, then iterate maintaining left sum.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    long long totalSum = 0;
    for (int i = 0; i < n; i++) {
        totalSum += arr[i];
    }
    
    long long leftSum = 0;
    for (int i = 0; i < n; i++) {
        totalSum -= arr[i];
        if (leftSum == totalSum) {
            cout << i << endl;
            return 0;
        }
        leftSum += arr[i];
    }
    
    cout << -1 << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q29: Find Majority Element
**Problem:** Find element that appears more than N/2 times.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print majority element or -1

**Example:**
```
Input:
7
2 2 1 1 1 2 2
Output: 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use Boyer-Moore Voting Algorithm.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int candidate = arr[0];
    int count = 1;
    
    for (int i = 1; i < n; i++) {
        if (arr[i] == candidate) {
            count++;
        } else {
            count--;
            if (count == 0) {
                candidate = arr[i];
                count = 1;
            }
        }
    }
    
    count = 0;
    for (int i = 0; i < n; i++) {
        if (arr[i] == candidate) count++;
    }
    
    if (count > n / 2) {
        cout << candidate << endl;
    } else {
        cout << -1 << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q30: Merge Two Sorted Arrays
**Problem:** Merge two sorted arrays into one sorted array.

**Input Format:**
- First line: N, M
- Second line: N sorted integers
- Third line: M sorted integers

**Output Format:** Print merged sorted array

**Example:**
```
Input:
3 4
1 3 5
2 4 6 8
Output: 1 2 3 4 5 6 8
```

**Constraints:** 1 ≤ N, M ≤ 10^5

**Explanation:** Use two pointers technique.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<int> arr1(n), arr2(m);
    for (int i = 0; i < n; i++) cin >> arr1[i];
    for (int i = 0; i < m; i++) cin >> arr2[i];
    
    vector<int> result;
    int i = 0, j = 0;
    
    while (i < n && j < m) {
        if (arr1[i] <= arr2[j]) {
            result.push_back(arr1[i]);
            i++;
        } else {
            result.push_back(arr2[j]);
            j++;
        }
    }
    
    while (i < n) {
        result.push_back(arr1[i]);
        i++;
    }
    
    while (j < m) {
        result.push_back(arr2[j]);
        j++;
    }
    
    for (int x : result) {
        cout << x << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N + M)  
**Space Complexity:** O(N + M)

---

### Q31: Find Duplicate in Array
**Problem:** Array contains N+1 integers from 1 to N. Find the duplicate.

**Input Format:**
- First line: N
- Second line: N+1 integers

**Output Format:** Print duplicate number

**Example:**
```
Input:
4
1 3 4 2 2
Output: 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use XOR or sum formula approach.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n + 1);
    for (int i = 0; i < n + 1; i++) {
        cin >> arr[i];
    }
    
    long long arraySum = 0;
    for (int i = 0; i < n + 1; i++) {
        arraySum += arr[i];
    }
    
    long long expectedSum = (long long)n * (n + 1) / 2;
    
    cout << arraySum - expectedSum << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q32: Rearrange Positive and Negative Numbers
**Problem:** Rearrange array so positive and negative numbers alternate (start with positive).

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print rearranged array

**Example:**
```
Input:
6
1 -2 3 -4 5 -6
Output: 1 -2 3 -4 5 -6
```

**Constraints:** 1 ≤ N ≤ 10^5, equal positives and negatives

**Explanation:** Separate positive and negative, then merge alternately.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    vector<int> pos, neg;
    for (int i = 0; i < n; i++) {
        if (arr[i] >= 0) {
            pos.push_back(arr[i]);
        } else {
            neg.push_back(arr[i]);
        }
    }
    
    int i = 0, j = 0, k = 0;
    while (i < pos.size() && j < neg.size()) {
        arr[k++] = pos[i++];
        arr[k++] = neg[j++];
    }
    
    for (int x : arr) {
        cout << x << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q33: Subarray with Given Sum
**Problem:** Find if there exists a contiguous subarray with sum K.

**Input Format:**
- First line: N, K
- Second line: N positive integers

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
5 12
1 2 3 7 5
Output: YES (2 + 3 + 7 = 12)
```

**Constraints:** 1 ≤ N ≤ 10^5, positive integers only

**Explanation:** Use sliding window with two pointers.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int left = 0, sum = 0;
    
    for (int right = 0; right < n; right++) {
        sum += arr[right];
        
        while (sum > k && left <= right) {
            sum -= arr[left];
            left++;
        }
        
        if (sum == k) {
            cout << "YES" << endl;
            return 0;
        }
    }
    
    cout << "NO" << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q34: Count Inversions
**Problem:** Count pairs (i, j) where i < j and arr[i] > arr[j].

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print count of inversions

**Example:**
```
Input:
5
2 4 1 3 5
Output: 3 (pairs: (2,1), (4,1), (4,3))
```

**Constraints:** 1 ≤ N ≤ 10^3

**Explanation:** Use nested loops for simple approach.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int count = 0;
    
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[i] > arr[j]) {
                count++;
            }
        }
    }
    
    cout << count << endl;
    
    return 0;
}
```
**Time Complexity:** O(N²)  
**Space Complexity:** O(N)

---

### Q35: Product of Array Except Self
**Problem:** For each index i, calculate product of all elements except arr[i].

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print N products

**Example:**
```
Input:
4
1 2 3 4
Output: 24 12 8 6
```

**Constraints:** 1 ≤ N ≤ 10^5, no division allowed

**Explanation:** Use prefix and suffix product arrays.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    vector<long long> result(n, 1);
    
    long long prefix = 1;
    for (int i = 0; i < n; i++) {
        result[i] = prefix;
        prefix *= arr[i];
    }
    
    long long suffix = 1;
    for (int i = n - 1; i >= 0; i--) {
        result[i] *= suffix;
        suffix *= arr[i];
    }
    
    for (int i = 0; i < n; i++) {
        cout << result[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

## Category 3: Strings (15 questions)

### Q36: Reverse a String
**Problem:** Reverse the given string.

**Input Format:** Single line string

**Output Format:** Print reversed string

**Example:**
```
Input: hello
Output: olleh
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Use two pointers or built-in reverse.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    reverse(s.begin(), s.end());
    
    cout << s << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q37: Check Palindrome String
**Problem:** Check if string is palindrome.

**Input Format:** Single line string

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input: racecar
Output: YES

Input: hello
Output: NO
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Compare characters from both ends moving inward.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    int left = 0, right = s.length() - 1;
    bool isPalindrome = true;
    
    while (left < right) {
        if (s[left] != s[right]) {
            isPalindrome = false;
            break;
        }
        left++;
        right--;
    }
    
    if (isPalindrome) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q38: Count Vowels and Consonants
**Problem:** Count vowels and consonants in a string.

**Input Format:** Single line string (lowercase only)

**Output Format:** Print vowel count and consonant count

**Example:**
```
Input: hello
Output: 2 3
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Check each character if vowel or consonant.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    int vowels = 0, consonants = 0;
    
    for (char c : s) {
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
            vowels++;
        } else if (c >= 'a' && c <= 'z') {
            consonants++;
        }
    }
    
    cout << vowels << " " << consonants << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q39: Check Anagram
**Problem:** Check if two strings are anagrams.

**Input Format:** Two strings on separate lines

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
listen
silent
Output: YES
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Sort both strings and compare or use frequency count.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s1, s2;
    cin >> s1 >> s2;
    
    if (s1.length() != s2.length()) {
        cout << "NO" << endl;
        return 0;
    }
    
    sort(s1.begin(), s1.end());
    sort(s2.begin(), s2.end());
    
    if (s1 == s2) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N log N)  
**Space Complexity:** O(N)

---

### Q40: First Non-Repeating Character
**Problem:** Find the first non-repeating character in string.

**Input Format:** Single line string

**Output Format:** Print first non-repeating character or -1

**Example:**
```
Input: aabccde
Output: b

Input: aabbcc
Output: -1
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Use frequency map and find first with count 1.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    unordered_map<char, int> freq;
    
    for (char c : s) {
        freq[c]++;
    }
    
    for (char c : s) {
        if (freq[c] == 1) {
            cout << c << endl;
            return 0;
        }
    }
    
    cout << -1 << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q41: Remove Duplicates from String
**Problem:** Remove duplicate characters from string maintaining first occurrence.

**Input Format:** Single line string

**Output Format:** Print string without duplicates

**Example:**
```
Input: programming
Output: progamin
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Use set to track seen characters.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    unordered_set<char> seen;
    string result = "";
    
    for (char c : s) {
        if (seen.find(c) == seen.end()) {
            result += c;
            seen.insert(c);
        }
    }
    
    cout << result << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q42: Longest Substring Without Repeating Characters
**Problem:** Find length of longest substring without repeating characters.

**Input Format:** Single line string

**Output Format:** Print maximum length

**Example:**
```
Input: abcabcbb
Output: 3 (abc)

Input: bbbbb
Output: 1
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Use sliding window with hash set.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    unordered_set<char> chars;
    int left = 0, maxLen = 0;
    
    for (int right = 0; right < s.length(); right++) {
        while (chars.count(s[right])) {
            chars.erase(s[left]);
            left++;
        }
        chars.insert(s[right]);
        maxLen = max(maxLen, right - left + 1);
    }
    
    cout << maxLen << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(min(N, charset size))

---

### Q43: String Rotation Check
**Problem:** Check if string s2 is rotation of string s1.

**Input Format:** Two strings on separate lines

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
abcde
cdeab
Output: YES
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Check if s2 exists in s1+s1.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s1, s2;
    cin >> s1 >> s2;
    
    if (s1.length() != s2.length()) {
        cout << "NO" << endl;
        return 0;
    }
    
    string concatenated = s1 + s1;
    
    if (concatenated.find(s2) != string::npos) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q44: Count Words in String
**Problem:** Count number of words in a string separated by spaces.

**Input Format:** Single line string with spaces

**Output Format:** Print word count

**Example:**
```
Input: Hello World Programming
Output: 3
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Split by spaces and count.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string line;
    getline(cin, line);
    
    stringstream ss(line);
    string word;
    int count = 0;
    
    while (ss >> word) {
        count++;
    }
    
    cout << count << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q45: Toggle Case of String
**Problem:** Convert uppercase to lowercase and vice versa.

**Input Format:** Single line string

**Output Format:** Print toggled string

**Example:**
```
Input: HeLLo
Output: hEllO
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Check each character and toggle.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] - 'a' + 'A';
        } else if (s[i] >= 'A' && s[i] <= 'Z') {
            s[i] = s[i] - 'A' + 'a';
        }
    }
    
    cout << s << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q46: Valid Parentheses
**Problem:** Check if parentheses are balanced.

**Input Format:** String with (, ), {, }, [, ]

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input: ({[]})
Output: YES

Input: ([)]
Output: NO
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Use stack to match opening and closing brackets.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    stack<char> st;
    
    for (char c : s) {
        if (c == '(' || c == '{' || c == '[') {
            st.push(c);
        } else {
            if (st.empty()) {
                cout << "NO" << endl;
                return 0;
            }
            char top = st.top();
            st.pop();
            
            if ((c == ')' && top != '(') ||
                (c == '}' && top != '{') ||
                (c == ']' && top != '[')) {
                cout << "NO" << endl;
                return 0;
            }
        }
    }
    
    if (st.empty()) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q47: Compress String
**Problem:** Compress string using counts (e.g., aaabb → a3b2).

**Input Format:** Single line string

**Output Format:** Print compressed string

**Example:**
```
Input: aaabbc
Output: a3b2c1

Input: abc
Output: a1b1c1
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Count consecutive characters.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    string result = "";
    int count = 1;
    
    for (int i = 1; i < s.length(); i++) {
        if (s[i] == s[i - 1]) {
            count++;
        } else {
            result += s[i - 1];
            result += to_string(count);
            count = 1;
        }
    }
    
    result += s[s.length() - 1];
    result += to_string(count);
    
    cout << result << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q48: Longest Common Prefix
**Problem:** Find longest common prefix among array of strings.

**Input Format:**
- First line: N
- Next N lines: strings

**Output Format:** Print longest common prefix or empty string

**Example:**
```
Input:
3
flower
flow
flight
Output: fl
```

**Constraints:** 1 ≤ N ≤ 100, 1 ≤ length ≤ 100

**Explanation:** Compare characters column-wise.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<string> strs(n);
    for (int i = 0; i < n; i++) {
        cin >> strs[i];
    }
    
    if (n == 0) {
        cout << "" << endl;
        return 0;
    }
    
    string prefix = "";
    
    for (int i = 0; i < strs[0].length(); i++) {
        char c = strs[0][i];
        
        for (int j = 1; j < n; j++) {
            if (i >= strs[j].length() || strs[j][i] != c) {
                cout << prefix << endl;
                return 0;
            }
        }
        
        prefix += c;
    }
    
    cout << prefix << endl;
    
    return 0;
}
```
**Time Complexity:** O(N * M) where M is min length  
**Space Complexity:** O(M)

---

### Q49: Remove All Adjacent Duplicates
**Problem:** Remove all adjacent duplicate characters.

**Input Format:** Single line string

**Output Format:** Print string after removing duplicates

**Example:**
```
Input: abbaca
Output: ca (abbaca → aaca → ca)
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Use stack to remove adjacent duplicates.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;
    
    stack<char> st;
    
    for (char c : s) {
        if (!st.empty() && st.top() == c) {
            st.pop();
        } else {
            st.push(c);
        }
    }
    
    string result = "";
    while (!st.empty()) {
        result = st.top() + result;
        st.pop();
    }
    
    cout << result << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q50: Isomorphic Strings
**Problem:** Check if two strings are isomorphic (characters can be mapped one-to-one).

**Input Format:** Two strings on separate lines

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
egg
add
Output: YES

Input:
foo
bar
Output: NO
```

**Constraints:** 1 ≤ length ≤ 10^5

**Explanation:** Create bijective mapping between characters.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s1, s2;
    cin >> s1 >> s2;
    
    if (s1.length() != s2.length()) {
        cout << "NO" << endl;
        return 0;
    }
    
    unordered_map<char, char> map1, map2;
    
    for (int i = 0; i < s1.length(); i++) {
        char c1 = s1[i], c2 = s2[i];
        
        if (map1.count(c1)) {
            if (map1[c1] != c2) {
                cout << "NO" << endl;
                return 0;
            }
        } else {
            map1[c1] = c2;
        }
        
        if (map2.count(c2)) {
            if (map2[c2] != c1) {
                cout << "NO" << endl;
                return 0;
            }
        } else {
            map2[c2] = c1;
        }
    }
    
    cout << "YES" << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(1) - at most 256 characters

---

## Category 4: Searching & Sorting (10 questions)

### Q51: Binary Search
**Problem:** Search for element X in sorted array using binary search.

**Input Format:**
- First line: N, X
- Second line: N sorted integers

**Output Format:** Print index (0-based) or -1

**Example:**
```
Input:
5 7
1 3 5 7 9
Output: 3
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Divide array in half repeatedly.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, x;
    cin >> n >> x;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int left = 0, right = n - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == x) {
            cout << mid << endl;
            return 0;
        } else if (arr[mid] < x) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    cout << -1 << endl;
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(N)

---

### Q52: First and Last Occurrence
**Problem:** Find first and last occurrence of element X in sorted array.

**Input Format:**
- First line: N, X
- Second line: N sorted integers

**Output Format:** Print first and last index or -1 -1

**Example:**
```
Input:
7 3
1 2 3 3 3 4 5
Output: 2 4
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use binary search twice.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int findFirst(vector<int>& arr, int x) {
    int left = 0, right = arr.size() - 1;
    int result = -1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == x) {
            result = mid;
            right = mid - 1;
        } else if (arr[mid] < x) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

int findLast(vector<int>& arr, int x) {
    int left = 0, right = arr.size() - 1;
    int result = -1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == x) {
            result = mid;
            left = mid + 1;
        } else if (arr[mid] < x) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

int main() {
    int n, x;
    cin >> n >> x;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int first = findFirst(arr, x);
    int last = findLast(arr, x);
    
    cout << first << " " << last << endl;
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(N)

---

### Q53: Count Occurrences in Sorted Array
**Problem:** Count occurrences of X in sorted array.

**Input Format:**
- First line: N, X
- Second line: N sorted integers

**Output Format:** Print count

**Example:**
```
Input:
8 3
1 2 3 3 3 4 5 6
Output: 3
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Find first and last occurrence, subtract.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, x;
    cin >> n >> x;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    auto lower = lower_bound(arr.begin(), arr.end(), x);
    auto upper = upper_bound(arr.begin(), arr.end(), x);
    
    int count = upper - lower;
    
    cout << count << endl;
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(N)

---

### Q54: Search in Rotated Sorted Array
**Problem:** Search element in rotated sorted array.

**Input Format:**
- First line: N, X
- Second line: N integers (rotated sorted array)

**Output Format:** Print index or -1

**Example:**
```
Input:
7 3
4 5 6 7 0 1 2
Output: -1

Input:
7 0
4 5 6 7 0 1 2
Output: 4
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Modified binary search considering rotation.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, x;
    cin >> n >> x;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int left = 0, right = n - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == x) {
            cout << mid << endl;
            return 0;
        }
        
        if (arr[left] <= arr[mid]) {
            if (x >= arr[left] && x < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        } else {
            if (x > arr[mid] && x <= arr[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    cout << -1 << endl;
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(N)

---

### Q55: Sort Array of 0s, 1s, and 2s
**Problem:** Sort array containing only 0s, 1s, and 2s.

**Input Format:**
- First line: N
- Second line: N integers (0, 1, or 2)

**Output Format:** Print sorted array

**Example:**
```
Input:
6
2 0 1 2 1 0
Output: 0 0 1 1 2 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use Dutch National Flag algorithm (3-way partitioning).

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int low = 0, mid = 0, high = n - 1;
    
    while (mid <= high) {
        if (arr[mid] == 0) {
            swap(arr[low], arr[mid]);
            low++;
            mid++;
        } else if (arr[mid] == 1) {
            mid++;
        } else {
            swap(arr[mid], arr[high]);
            high--;
        }
    }
    
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q56: Find Peak Element
**Problem:** Find index of a peak element (greater than neighbors).

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print any peak index

**Example:**
```
Input:
5
1 3 20 4 1
Output: 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use binary search to find peak.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    if (n == 1) {
        cout << 0 << endl;
        return 0;
    }
    
    int left = 0, right = n - 1;
    
    while (left < right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] < arr[mid + 1]) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    
    cout << left << endl;
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(N)

---

### Q57: Kth Smallest Element
**Problem:** Find Kth smallest element in unsorted array.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print Kth smallest element

**Example:**
```
Input:
5 3
7 10 4 3 20
Output: 7
```

**Constraints:** 1 ≤ K ≤ N ≤ 10^5

**Explanation:** Sort and return K-1 index element.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    sort(arr.begin(), arr.end());
    
    cout << arr[k - 1] << endl;
    
    return 0;
}
```
**Time Complexity:** O(N log N)  
**Space Complexity:** O(N)

---

### Q58: Square Root using Binary Search
**Problem:** Find square root of N (integer part only).

**Input Format:** Single integer N

**Output Format:** Print integer square root

**Example:**
```
Input: 8
Output: 2

Input: 16
Output: 4
```

**Constraints:** 0 ≤ N ≤ 10^9

**Explanation:** Binary search on answer from 0 to N.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    long long n;
    cin >> n;
    
    if (n == 0) {
        cout << 0 << endl;
        return 0;
    }
    
    long long left = 1, right = n;
    long long result = 0;
    
    while (left <= right) {
        long long mid = left + (right - left) / 2;
        
        if (mid <= n / mid) {
            result = mid;
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    cout << result << endl;
    
    return 0;
}
```
**Time Complexity:** O(log N)  
**Space Complexity:** O(1)

---

### Q59: Minimum Difference Pair
**Problem:** Find pair with minimum absolute difference in array.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print minimum difference

**Example:**
```
Input:
5
1 5 3 19 18
Output: 1 (19 - 18)
```

**Constraints:** 2 ≤ N ≤ 10^5

**Explanation:** Sort array and check adjacent elements.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    sort(arr.begin(), arr.end());
    
    int minDiff = INT_MAX;
    
    for (int i = 1; i < n; i++) {
        minDiff = min(minDiff, arr[i] - arr[i - 1]);
    }
    
    cout << minDiff << endl;
    
    return 0;
}
```
**Time Complexity:** O(N log N)  
**Space Complexity:** O(N)

---

### Q60: Merge Sort Implementation
**Problem:** Sort array using merge sort.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print sorted array

**Example:**
```
Input:
5
5 2 8 1 9
Output: 1 2 5 8 9
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Divide and conquer sorting algorithm.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

void merge(vector<int>& arr, int left, int mid, int right) {
    vector<int> temp;
    int i = left, j = mid + 1;
    
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp.push_back(arr[i++]);
        } else {
            temp.push_back(arr[j++]);
        }
    }
    
    while (i <= mid) temp.push_back(arr[i++]);
    while (j <= right) temp.push_back(arr[j++]);
    
    for (int i = 0; i < temp.size(); i++) {
        arr[left + i] = temp[i];
    }
}

void mergeSort(vector<int>& arr, int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    mergeSort(arr, 0, n - 1);
    
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N log N)  
**Space Complexity:** O(N)

---

## Category 5: Hashing & Frequency Counting (10 questions)

### Q61: Find Frequency of Each Element
**Problem:** Count frequency of each element in array.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print elements and their frequencies

**Example:**
```
Input:
6
1 2 1 3 2 1
Output:
1 3
2 2
3 1
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use hash map to count frequencies.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    map<int, int> freq;
    
    for (int i = 0; i < n; i++) {
        freq[arr[i]]++;
    }
    
    for (auto p : freq) {
        cout << p.first << " " << p.second << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N log N)  
**Space Complexity:** O(N)

---

### Q62: Find Elements with Odd Frequency
**Problem:** Print all elements that appear odd number of times.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print elements with odd frequency

**Example:**
```
Input:
7
1 2 3 2 3 1 3
Output: 3
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Count frequencies and filter odd counts.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_map<int, int> freq;
    
    for (int i = 0; i < n; i++) {
        freq[arr[i]]++;
    }
    
    for (auto p : freq) {
        if (p.second % 2 != 0) {
            cout << p.first << " ";
        }
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q63: Two Sum Problem
**Problem:** Find indices of two numbers that add up to target.

**Input Format:**
- First line: N, Target
- Second line: N integers

**Output Format:** Print two indices or -1 -1

**Example:**
```
Input:
4 9
2 7 11 15
Output: 0 1
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use hash map to store complements.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, target;
    cin >> n >> target;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_map<int, int> seen;
    
    for (int i = 0; i < n; i++) {
        int complement = target - arr[i];
        if (seen.count(complement)) {
            cout << seen[complement] << " " << i << endl;
            return 0;
        }
        seen[arr[i]] = i;
    }
    
    cout << -1 << " " << -1 << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q64: Subarray with Sum Zero
**Problem:** Check if there exists a subarray with sum 0.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
5
4 2 -3 1 6
Output: YES (2 + (-3) + 1 = 0)
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use prefix sum with hash set.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_set<long long> prefixSums;
    long long sum = 0;
    
    for (int i = 0; i < n; i++) {
        sum += arr[i];
        
        if (sum == 0 || prefixSums.count(sum)) {
            cout << "YES" << endl;
            return 0;
        }
        
        prefixSums.insert(sum);
    }
    
    cout << "NO" << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q65: Longest Consecutive Sequence
**Problem:** Find length of longest consecutive elements sequence.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print maximum length

**Example:**
```
Input:
6
100 4 200 1 3 2
Output: 4 (1, 2, 3, 4)
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use hash set for O(1) lookup.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_set<int> nums(arr.begin(), arr.end());
    int maxLen = 0;
    
    for (int num : nums) {
        if (!nums.count(num - 1)) {
            int currentNum = num;
            int currentLen = 1;
            
            while (nums.count(currentNum + 1)) {
                currentNum++;
                currentLen++;
            }
            
            maxLen = max(maxLen, currentLen);
        }
    }
    
    cout << maxLen << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q66: Group Anagrams
**Problem:** Count number of anagram groups in array of strings.

**Input Format:**
- First line: N
- Next N lines: strings

**Output Format:** Print number of groups

**Example:**
```
Input:
4
eat
tea
tan
nat
Output: 2
```

**Constraints:** 1 ≤ N ≤ 100

**Explanation:** Sort each string and use as key.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    unordered_map<string, int> groups;
    
    for (int i = 0; i < n; i++) {
        string s;
        cin >> s;
        
        string sorted = s;
        sort(sorted.begin(), sorted.end());
        
        groups[sorted]++;
    }
    
    cout << groups.size() << endl;
    
    return 0;
}
```
**Time Complexity:** O(N * K log K) where K is max string length  
**Space Complexity:** O(N * K)

---

### Q67: First Repeating Element
**Problem:** Find first element that repeats in array.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print first repeating element or -1

**Example:**
```
Input:
6
1 2 3 4 2 1
Output: 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Track seen elements and first repeat.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_set<int> seen;
    
    for (int i = 0; i < n; i++) {
        if (seen.count(arr[i])) {
            cout << arr[i] << endl;
            return 0;
        }
        seen.insert(arr[i]);
    }
    
    cout << -1 << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q68: Union of Two Arrays
**Problem:** Find count of unique elements in union of two arrays.

**Input Format:**
- First line: N, M
- Second line: N integers
- Third line: M integers

**Output Format:** Print count

**Example:**
```
Input:
5 3
1 2 3 4 5
3 4 5
Output: 5
```

**Constraints:** 1 ≤ N, M ≤ 10^5

**Explanation:** Use set to store all unique elements.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;
    
    unordered_set<int> unionSet;
    
    for (int i = 0; i < n; i++) {
        int x;
        cin >> x;
        unionSet.insert(x);
    }
    
    for (int i = 0; i < m; i++) {
        int x;
        cin >> x;
        unionSet.insert(x);
    }
    
    cout << unionSet.size() << endl;
    
    return 0;
}
```
**Time Complexity:** O(N + M)  
**Space Complexity:** O(N + M)

---

### Q69: Intersection of Two Arrays
**Problem:** Find common elements in two arrays.

**Input Format:**
- First line: N, M
- Second line: N integers
- Third line: M integers

**Output Format:** Print count of common elements

**Example:**
```
Input:
5 4
1 2 3 4 5
3 4 5 6
Output: 3
```

**Constraints:** 1 ≤ N, M ≤ 10^5

**Explanation:** Use hash set for first array, check second.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;
    
    unordered_set<int> set1;
    
    for (int i = 0; i < n; i++) {
        int x;
        cin >> x;
        set1.insert(x);
    }
    
    unordered_set<int> intersection;
    
    for (int i = 0; i < m; i++) {
        int x;
        cin >> x;
        if (set1.count(x)) {
            intersection.insert(x);
        }
    }
    
    cout << intersection.size() << endl;
    
    return 0;
}
```
**Time Complexity:** O(N + M)  
**Space Complexity:** O(N)

---

### Q70: Count Distinct Elements in Window
**Problem:** Count distinct elements in every window of size K.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print distinct counts for each window

**Example:**
```
Input:
7 4
1 2 1 3 4 2 3
Output: 3 4 4 3
```

**Constraints:** 1 ≤ K ≤ N ≤ 10^5

**Explanation:** Use sliding window with hash map.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_map<int, int> freq;
    
    for (int i = 0; i < k; i++) {
        freq[arr[i]]++;
    }
    
    cout << freq.size() << " ";
    
    for (int i = k; i < n; i++) {
        freq[arr[i - k]]--;
        if (freq[arr[i - k]] == 0) {
            freq.erase(arr[i - k]);
        }
        
        freq[arr[i]]++;
        
        cout << freq.size() << " ";
    }
    
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(K)

---

## Category 6: Two-pointer & Sliding Window Basics (10 questions)

### Q71: Container With Most Water
**Problem:** Find two lines that together with x-axis form a container with maximum water.

**Input Format:**
- First line: N
- Second line: N heights

**Output Format:** Print maximum area

**Example:**
```
Input:
6
1 8 6 2 5 4
Output: 20
```

**Constraints:** 2 ≤ N ≤ 10^5

**Explanation:** Use two pointers from both ends, move the pointer with smaller height.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> height(n);
    for (int i = 0; i < n; i++) {
        cin >> height[i];
    }
    
    int left = 0, right = n - 1;
    int maxArea = 0;
    
    while (left < right) {
        int width = right - left;
        int h = min(height[left], height[right]);
        maxArea = max(maxArea, width * h);
        
        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }
    
    cout << maxArea << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q72: Three Sum - Count Triplets with Sum Zero
**Problem:** Count triplets that sum to zero.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print count of triplets

**Example:**
```
Input:
6
-1 0 1 2 -1 -4
Output: 2
```

**Constraints:** 3 ≤ N ≤ 1000

**Explanation:** Sort array, fix one element, use two pointers for remaining.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    sort(arr.begin(), arr.end());
    int count = 0;
    
    for (int i = 0; i < n - 2; i++) {
        if (i > 0 && arr[i] == arr[i - 1]) continue;
        
        int left = i + 1, right = n - 1;
        
        while (left < right) {
            int sum = arr[i] + arr[left] + arr[right];
            
            if (sum == 0) {
                count++;
                left++;
                right--;
                
                while (left < right && arr[left] == arr[left - 1]) left++;
                while (left < right && arr[right] == arr[right + 1]) right--;
            } else if (sum < 0) {
                left++;
            } else {
                right--;
            }
        }
    }
    
    cout << count << endl;
    
    return 0;
}
```
**Time Complexity:** O(N²)  
**Space Complexity:** O(N)

---

### Q73: Maximum Sum Subarray of Size K
**Problem:** Find maximum sum of any contiguous subarray of size K.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print maximum sum

**Example:**
```
Input:
5 3
2 1 5 1 3
Output: 9
```

**Constraints:** 1 ≤ K ≤ N ≤ 10^5

**Explanation:** Use sliding window to maintain sum of K elements.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    long long windowSum = 0;
    for (int i = 0; i < k; i++) {
        windowSum += arr[i];
    }
    
    long long maxSum = windowSum;
    
    for (int i = k; i < n; i++) {
        windowSum = windowSum - arr[i - k] + arr[i];
        maxSum = max(maxSum, windowSum);
    }
    
    cout << maxSum << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q74: Longest Subarray with Sum K
**Problem:** Find length of longest subarray with sum equal to K (positive integers).

**Input Format:**
- First line: N, K
- Second line: N positive integers

**Output Format:** Print maximum length or 0

**Example:**
```
Input:
5 5
1 2 3 7 5
Output: 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use two pointers with sliding window.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int left = 0, sum = 0, maxLen = 0;
    
    for (int right = 0; right < n; right++) {
        sum += arr[right];
        
        while (sum > k && left <= right) {
            sum -= arr[left];
            left++;
        }
        
        if (sum == k) {
            maxLen = max(maxLen, right - left + 1);
        }
    }
    
    cout << maxLen << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q75: Count Subarrays with Sum K
**Problem:** Count number of subarrays with sum equal to K.

**Input Format:**
- First line: N, K
- Second line: N integers (can be negative)

**Output Format:** Print count

**Example:**
```
Input:
4 3
1 1 1 1
Output: 2
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use prefix sum with hash map.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_map<long long, int> prefixCount;
    prefixCount[0] = 1;
    
    long long sum = 0;
    int count = 0;
    
    for (int i = 0; i < n; i++) {
        sum += arr[i];
        
        if (prefixCount.count(sum - k)) {
            count += prefixCount[sum - k];
        }
        
        prefixCount[sum]++;
    }
    
    cout << count << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q76: Smallest Subarray with Sum Greater Than K
**Problem:** Find length of smallest subarray with sum > K.

**Input Format:**
- First line: N, K
- Second line: N positive integers

**Output Format:** Print minimum length or -1

**Example:**
```
Input:
6 51
1 4 45 6 10 19
Output: 3
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use sliding window, shrink when sum > K.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    int left = 0, sum = 0, minLen = INT_MAX;
    
    for (int right = 0; right < n; right++) {
        sum += arr[right];
        
        while (sum > k && left <= right) {
            minLen = min(minLen, right - left + 1);
            sum -= arr[left];
            left++;
        }
    }
    
    if (minLen == INT_MAX) {
        cout << -1 << endl;
    } else {
        cout << minLen << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q77: Count Pairs with Difference K
**Problem:** Count pairs with absolute difference equal to K.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print count

**Example:**
```
Input:
5 2
1 5 3 4 2
Output: 3
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use hash set to check if x+K or x-K exists.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    unordered_set<int> nums(arr.begin(), arr.end());
    int count = 0;
    
    for (int num : nums) {
        if (nums.count(num + k)) {
            count++;
        }
    }
    
    cout << count << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q78: Maximum of All Subarrays of Size K
**Problem:** Find maximum element in each window of size K.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print maximums for each window

**Example:**
```
Input:
7 3
1 3 -1 -3 5 3 6
Output: 3 3 5 5 6
```

**Constraints:** 1 ≤ K ≤ N ≤ 10^5

**Explanation:** Use deque to maintain decreasing order of useful elements.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    deque<int> dq;
    
    for (int i = 0; i < k; i++) {
        while (!dq.empty() && arr[i] >= arr[dq.back()]) {
            dq.pop_back();
        }
        dq.push_back(i);
    }
    
    cout << arr[dq.front()] << " ";
    
    for (int i = k; i < n; i++) {
        while (!dq.empty() && dq.front() <= i - k) {
            dq.pop_front();
        }
        
        while (!dq.empty() && arr[i] >= arr[dq.back()]) {
            dq.pop_back();
        }
        
        dq.push_back(i);
        cout << arr[dq.front()] << " ";
    }
    
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(K)

---

### Q79: Remove Duplicates from Sorted Array (Two Pointer)
**Problem:** Remove duplicates in-place from sorted array, return new length.

**Input Format:**
- First line: N
- Second line: N sorted integers

**Output Format:** Print new length

**Example:**
```
Input:
5
1 1 2 2 3
Output: 3
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use two pointers to place unique elements.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    if (n == 0) {
        cout << 0 << endl;
        return 0;
    }
    
    int j = 0;
    for (int i = 1; i < n; i++) {
        if (arr[i] != arr[j]) {
            j++;
            arr[j] = arr[i];
        }
    }
    
    cout << j + 1 << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q80: Trapping Rain Water
**Problem:** Calculate how much water can be trapped after raining.

**Input Format:**
- First line: N
- Second line: N heights

**Output Format:** Print total water trapped

**Example:**
```
Input:
6
0 1 0 2 1 0 1 3 2 1 2 1
Output: 6
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use two pointers tracking left and right max heights.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> height(n);
    for (int i = 0; i < n; i++) {
        cin >> height[i];
    }
    
    if (n == 0) {
        cout << 0 << endl;
        return 0;
    }
    
    int left = 0, right = n - 1;
    int leftMax = 0, rightMax = 0;
    int water = 0;
    
    while (left < right) {
        if (height[left] < height[right]) {
            if (height[left] >= leftMax) {
                leftMax = height[left];
            } else {
                water += leftMax - height[left];
            }
            left++;
        } else {
            if (height[right] >= rightMax) {
                rightMax = height[right];
            } else {
                water += rightMax - height[right];
            }
            right--;
        }
    }
    
    cout << water << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

## Category 7: Recursion Basics (5 questions)

### Q81: Print N to 1 using Recursion
**Problem:** Print numbers from N to 1 using recursion.

**Input Format:** Single integer N

**Output Format:** Print N to 1 space-separated

**Example:**
```
Input: 5
Output: 5 4 3 2 1
```

**Constraints:** 1 ≤ N ≤ 10^4

**Explanation:** Base case at 0, recursive call with N-1.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

void printNto1(int n) {
    if (n == 0) return;
    cout << n << " ";
    printNto1(n - 1);
}

int main() {
    int n;
    cin >> n;
    
    printNto1(n);
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N) recursion stack

---

### Q82: Sum of Array using Recursion
**Problem:** Find sum of array elements using recursion.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print sum

**Example:**
```
Input:
4
1 2 3 4
Output: 10
```

**Constraints:** 1 ≤ N ≤ 10^4

**Explanation:** Base case at index N, add current element and recurse.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int arraySum(vector<int>& arr, int index) {
    if (index == arr.size()) return 0;
    return arr[index] + arraySum(arr, index + 1);
}

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    cout << arraySum(arr, 0) << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N) recursion stack

---

### Q83: Power Function using Recursion
**Problem:** Calculate A^B using recursion.

**Input Format:** Two integers A and B

**Output Format:** Print A^B

**Example:**
```
Input: 2 5
Output: 32
```

**Constraints:** 1 ≤ A ≤ 10, 0 ≤ B ≤ 20

**Explanation:** Base case B=0 returns 1, else multiply A with A^(B-1).

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

long long power(int a, int b) {
    if (b == 0) return 1;
    return a * power(a, b - 1);
}

int main() {
    int a, b;
    cin >> a >> b;
    
    cout << power(a, b) << endl;
    
    return 0;
}
```
**Time Complexity:** O(B)  
**Space Complexity:** O(B) recursion stack

---

### Q84: Check Palindrome String using Recursion
**Problem:** Check if string is palindrome using recursion.

**Input Format:** Single line string

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input: racecar
Output: YES
```

**Constraints:** 1 ≤ length ≤ 10^4

**Explanation:** Compare first and last, recurse on substring.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPalindrome(string& s, int left, int right) {
    if (left >= right) return true;
    if (s[left] != s[right]) return false;
    return isPalindrome(s, left + 1, right - 1);
}

int main() {
    string s;
    cin >> s;
    
    if (isPalindrome(s, 0, s.length() - 1)) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N) recursion stack

---

### Q85: Generate All Binary Strings of Length N
**Problem:** Generate all binary strings of length N.

**Input Format:** Single integer N

**Output Format:** Print all binary strings (one per line)

**Example:**
```
Input: 2
Output:
00
01
10
11
```

**Constraints:** 1 ≤ N ≤ 15

**Explanation:** Use backtracking to build strings.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

void generate(string current, int n) {
    if (current.length() == n) {
        cout << current << endl;
        return;
    }
    
    generate(current + "0", n);
    generate(current + "1", n);
}

int main() {
    int n;
    cin >> n;
    
    generate("", n);
    
    return 0;
}
```
**Time Complexity:** O(2^N)  
**Space Complexity:** O(N) recursion depth

---

## Category 8: Input/Output Based Coding Patterns (5 questions)

### Q86: Pattern - Right Triangle
**Problem:** Print right-angled triangle pattern with stars.

**Input Format:** Single integer N

**Output Format:** Print pattern

**Example:**
```
Input: 4
Output:
*
**
***
****
```

**Constraints:** 1 ≤ N ≤ 100

**Explanation:** Nested loops for rows and columns.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= i; j++) {
            cout << "*";
        }
        cout << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N²)  
**Space Complexity:** O(1)

---

### Q87: Pattern - Pyramid
**Problem:** Print pyramid pattern.

**Input Format:** Single integer N

**Output Format:** Print pattern

**Example:**
```
Input: 4
Output:
   *
  ***
 *****
*******
```

**Constraints:** 1 ≤ N ≤ 100

**Explanation:** Print spaces then stars for each row.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n - i; j++) {
            cout << " ";
        }
        for (int j = 1; j <= 2 * i - 1; j++) {
            cout << "*";
        }
        cout << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N²)  
**Space Complexity:** O(1)

---

### Q88: Pattern - Number Triangle
**Problem:** Print number triangle pattern.

**Input Format:** Single integer N

**Output Format:** Print pattern

**Example:**
```
Input: 4
Output:
1
1 2
1 2 3
1 2 3 4
```

**Constraints:** 1 ≤ N ≤ 100

**Explanation:** Print numbers from 1 to row number.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= i; j++) {
            cout << j << " ";
        }
        cout << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N²)  
**Space Complexity:** O(1)

---

### Q89: Matrix Diagonal Sum
**Problem:** Calculate sum of both diagonals of a square matrix.

**Input Format:**
- First line: N (size of matrix)
- Next N lines: N integers each

**Output Format:** Print sum of diagonals

**Example:**
```
Input:
3
1 2 3
4 5 6
7 8 9
Output: 25
```

**Constraints:** 1 ≤ N ≤ 100

**Explanation:** Add elements where i==j (main) and i+j==N-1 (anti).

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<vector<int>> matrix(n, vector<int>(n));
    
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cin >> matrix[i][j];
        }
    }
    
    int sum = 0;
    
    for (int i = 0; i < n; i++) {
        sum += matrix[i][i];
        if (i != n - 1 - i) {
            sum += matrix[i][n - 1 - i];
        }
    }
    
    cout << sum << endl;
    
    return 0;
}
```
**Time Complexity:** O(N²)  
**Space Complexity:** O(N²)

---

### Q90: Transpose of Matrix
**Problem:** Find transpose of a matrix.

**Input Format:**
- First line: N, M
- Next N lines: M integers each

**Output Format:** Print transposed matrix

**Example:**
```
Input:
2 3
1 2 3
4 5 6
Output:
1 4
2 5
3 6
```

**Constraints:** 1 ≤ N, M ≤ 100

**Explanation:** Swap rows and columns.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<int>> matrix(n, vector<int>(m));
    
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            cin >> matrix[i][j];
        }
    }
    
    for (int j = 0; j < m; j++) {
        for (int i = 0; i < n; i++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N * M)  
**Space Complexity:** O(N * M)

---

## Category 9: Time & Space Complexity Reasoning (5 questions)

### Q91: Identify Time Complexity - Nested Loops
**Problem:** What is the time complexity of the following code?
```cpp
for (int i = 0; i < n; i++) {
    for (int j = i; j < n; j++) {
        // O(1) operation
    }
}
```

**Answer:** O(N²)

**Explanation:** Outer loop runs N times. Inner loop runs N, N-1, N-2, ..., 1 times. Total = N(N+1)/2 ≈ O(N²)

---

### Q92: Identify Space Complexity - Recursive Call
**Problem:** What is the space complexity of calculating factorial recursively for N?

**Answer:** O(N)

**Explanation:** Each recursive call adds a frame to the call stack. For factorial(N), there are N recursive calls, so space complexity is O(N) for the recursion stack.

---

### Q93: Identify Time Complexity - Binary Search
**Problem:** What is the time complexity of binary search on a sorted array of size N?

**Answer:** O(log N)

**Explanation:** Binary search divides the search space in half with each iteration. Number of divisions needed is log₂(N).

---

### Q94: Identify Time Complexity - Hash Map Operations
**Problem:** What is the average time complexity of inserting N elements into a hash map and then checking if K elements exist?

**Answer:** O(N + K)

**Explanation:** Inserting N elements takes O(N) on average (O(1) per insertion). Checking K elements takes O(K) on average (O(1) per lookup). Total: O(N + K).

---

### Q95: Identify Space Complexity - Merge Sort
**Problem:** What is the space complexity of merge sort for an array of size N?

**Answer:** O(N)

**Explanation:** Merge sort requires O(N) auxiliary space for the temporary arrays used during merging, plus O(log N) for recursion stack. Total is O(N).

---

## Category 10: Mixed Practice (5 questions)

### Q96: Find Kth Largest Element
**Problem:** Find Kth largest element in unsorted array.

**Input Format:**
- First line: N, K
- Second line: N integers

**Output Format:** Print Kth largest element

**Example:**
```
Input:
6 2
3 2 1 5 6 4
Output: 5
```

**Constraints:** 1 ≤ K ≤ N ≤ 10^5

**Explanation:** Sort in descending order and pick K-1 index.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    sort(arr.begin(), arr.end(), greater<int>());
    
    cout << arr[k - 1] << endl;
    
    return 0;
}
```
**Time Complexity:** O(N log N)  
**Space Complexity:** O(N)

---

### Q97: Check if Array Can Be Sorted by Reversing Subarray
**Problem:** Check if array can be sorted by reversing exactly one subarray.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print "YES" or "NO"

**Example:**
```
Input:
5
1 5 4 3 2
Output: YES
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Find unsorted segment, reverse it, check if sorted.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    vector<int> sorted_arr = arr;
    sort(sorted_arr.begin(), sorted_arr.end());
    
    int left = 0, right = n - 1;
    
    while (left < n && arr[left] == sorted_arr[left]) {
        left++;
    }
    
    while (right > left && arr[right] == sorted_arr[right]) {
        right--;
    }
    
    reverse(arr.begin() + left, arr.begin() + right + 1);
    
    if (arr == sorted_arr) {
        cout << "YES" << endl;
    } else {
        cout << "NO" << endl;
    }
    
    return 0;
}
```
**Time Complexity:** O(N log N)  
**Space Complexity:** O(N)

---

### Q98: Next Greater Element
**Problem:** For each element, find the next greater element on its right.

**Input Format:**
- First line: N
- Second line: N integers

**Output Format:** Print next greater element for each (or -1)

**Example:**
```
Input:
4
4 5 2 25
Output: 5 25 25 -1
```

**Constraints:** 1 ≤ N ≤ 10^5

**Explanation:** Use stack to track elements waiting for their next greater.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    vector<int> result(n, -1);
    stack<int> st;
    
    for (int i = 0; i < n; i++) {
        while (!st.empty() && arr[st.top()] < arr[i]) {
            result[st.top()] = arr[i];
            st.pop();
        }
        st.push(i);
    }
    
    for (int i = 0; i < n; i++) {
        cout << result[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N)  
**Space Complexity:** O(N)

---

### Q99: Longest Palindromic Substring Length
**Problem:** Find length of longest palindromic substring.

**Input Format:** Single line string

**Output Format:** Print maximum length

**Example:**
```
Input: babad
Output: 3 (bab or aba)
```

**Constraints:** 1 ≤ length ≤ 1000

**Explanation:** Expand around center for each position.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int expandAroundCenter(string& s, int left, int right) {
    while (left >= 0 && right < s.length() && s[left] == s[right]) {
        left--;
        right++;
    }
    return right - left - 1;
}

int main() {
    string s;
    cin >> s;
    
    int maxLen = 0;
    
    for (int i = 0; i < s.length(); i++) {
        int len1 = expandAroundCenter(s, i, i);
        int len2 = expandAroundCenter(s, i, i + 1);
        int len = max(len1, len2);
        maxLen = max(maxLen, len);
    }
    
    cout << maxLen << endl;
    
    return 0;
}
```
**Time Complexity:** O(N²)  
**Space Complexity:** O(1)

---

### Q100: Zigzag (or Spiral) Array Traversal
**Problem:** Print array elements in zigzag order (alternating left-right, right-left).

**Input Format:**
- First line: N, M
- Next N lines: M integers each

**Output Format:** Print zigzag traversal

**Example:**
```
Input:
3 3
1 2 3
4 5 6
7 8 9
Output: 1 2 3 6 5 4 7 8 9
```

**Constraints:** 1 ≤ N, M ≤ 100

**Explanation:** Traverse rows alternating direction.

**Solution:**
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<int>> matrix(n, vector<int>(m));
    
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            cin >> matrix[i][j];
        }
    }
    
    for (int i = 0; i < n; i++) {
        if (i % 2 == 0) {
            for (int j = 0; j < m; j++) {
                cout << matrix[i][j] << " ";
            }
        } else {
            for (int j = m - 1; j >= 0; j--) {
                cout << matrix[i][j] << " ";
            }
        }
    }
    cout << endl;
    
    return 0;
}
```
**Time Complexity:** O(N * M)  
**Space Complexity:** O(N * M)

---

# Summary

This question bank contains **100 carefully curated coding problems** designed to match the IBM Associate System Engineer online assessment:

## Category Distribution:
1. **Basic Logic & Mathematics**: 15 questions
2. **Arrays**: 20 questions
3. **Strings**: 15 questions
4. **Searching & Sorting**: 10 questions
5. **Hashing & Frequency Counting**: 10 questions
6. **Two-pointer & Sliding Window**: 10 questions
7. **Recursion Basics**: 5 questions
8. **Input/Output Patterns**: 5 questions
9. **Time & Space Complexity**: 5 questions
10. **Mixed Practice**: 5 questions

## Key Features:
✅ Easy to Moderate difficulty level  
✅ Focus on fundamental DSA concepts  
✅ No advanced topics (DP, Graphs, Hard problems)  
✅ Clean, compilable C++ solutions  
✅ Comprehensive explanations  
✅ Time and space complexity analysis  
✅ Realistic constraints for online tests  

## Practice Strategy:
1. Start with Category 1 (Basic Logic) to build foundation
2. Progress through Categories 2-6 for core DSA skills
3. Practice Categories 7-8 for recursion and I/O patterns
4. Study Category 9 for complexity analysis
5. Test yourself with Category 10 (Mixed Practice)

**Good luck with your IBM ASE preparation!** 🚀
