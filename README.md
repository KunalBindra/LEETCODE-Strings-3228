# LEETCODE-Strings-3228
`s = "1001101"`

---

### 🔹 Code Recap

```java
class Solution {
    public int maxOperations(String s) {
       int n = s.length();
       int result = 0;
       int count = 0;
       int i = 0;

       while (i < n) {
           if (s.charAt(i) == '0') {
               result += count;
               while (i < n && s.charAt(i) == '0') {
                   i++;
               }
           } else {
               count++;
               i++;
           }
       }

       return result; 
    }
}
```

---

### 🔹 Initial Values:

| Variable | Value       |
| -------- | ----------- |
| `s`      | `"1001101"` |
| `n`      | `7`         |
| `result` | `0`         |
| `count`  | `0`         |
| `i`      | `0`         |

---

### 🔹 Step-by-step Execution

#### **Iteration 1**

* `i = 0`, `s.charAt(0) = '1'`
  → `'1'` branch executes:

  * `count++` → `count = 1`
  * `i++` → `i = 1`

| result | count | i |
| ------ | ----- | - |
| 0      | 1     | 1 |

---

#### **Iteration 2**

* `i = 1`, `s.charAt(1) = '0'`
  → `'0'` branch executes:

  * `result += count` → `result = 0 + 1 = 1`
  * Inner while: move through all `'0'`s

    * `i = 2` (since `s.charAt(1)` was `'0'`, then next `'0'` is checked)
    * `s.charAt(2) = '0'`, still `'0'`, so `i++ → 3`
    * `s.charAt(3) = '1'` → exit inner while

| result | count | i |
| ------ | ----- | - |
| 1      | 1     | 3 |

---

#### **Iteration 3**

* `i = 3`, `s.charAt(3) = '1'`

  * `'1'` branch: `count++ → 2`
  * `i++ → 4`

| result | count | i |
| ------ | ----- | - |
| 1      | 2     | 4 |

---

#### **Iteration 4**

* `i = 4`, `s.charAt(4) = '1'`

  * `'1'` branch: `count++ → 3`
  * `i++ → 5`

| result | count | i |
| ------ | ----- | - |
| 1      | 3     | 5 |

---

#### **Iteration 5**

* `i = 5`, `s.charAt(5) = '0'`

  * `'0'` branch:

    * `result += count → 1 + 3 = 4`
    * inner while → move past `'0'`

      * `i = 6`
      * `s.charAt(6) = '1'` → stop

| result | count | i |
| ------ | ----- | - |
| 4      | 3     | 6 |

---

#### **Iteration 6**

* `i = 6`, `s.charAt(6) = '1'`

  * `'1'` branch: `count++ → 4`
  * `i++ → 7`

| result | count | i |
| ------ | ----- | - |
| 4      | 4     | 7 |

---

Now `i = 7 == n`, loop ends.

---

### ✅ Final Values:

| Variable | Value |
| -------- | ----- |
| `result` | **4** |
| `count`  | 4     |
| `i`      | 7     |

---

### ✅ **Output:**

`maxOperations("1001101") = 4`

---

### 💡 Explanation in words:

Each time we encounter a block of `'0'`s, we add to `result` the number of `'1'`s we have seen **before** that block.

So:

* Before first `00`: seen 1 `'1'` → +1
* Before last `0`: seen 3 `'1'` → +3
  Total = 1 + 3 = **4**

✅ **Final Answer: 4**
