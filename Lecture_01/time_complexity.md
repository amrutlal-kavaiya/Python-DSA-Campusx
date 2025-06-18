# Time Complexity Practice Questions - Complete Study Guide 📚⚡

## Course Overview 🎯

**Transition**: Theory Complete → Practical Application  
**Practice Set**: 18 Carefully Selected Questions  
**Difficulty Levels**: Easy → Medium → Difficult  
**Goal**: Master time complexity analysis through hands-on practice

---

## 🧠 **Practice Strategy & Framework**

### 🎯 **Key Principle**
> **All answers will be one of the 6 complexity classes:**
> 1. O(1) - Constant
> 2. O(log n) - Logarithmic  
> 3. O(n) - Linear
> 4. O(n log n) - Linearithmic
> 5. O(n²) - Quadratic
> 6. O(2^n) - Exponential

---

## 🟢 **EASY LEVEL QUESTIONS (1-7)**

### 📚 **Question 1: Independent Loops**

```python
L = [1, 2, 3, 4, 5]

# Calculate sum
sum = 0
for i in L:
    sum += i
print(sum)

# Calculate product  
product = 1
for i in L:
    product *= i
print(product)
```

#### 🔍 **Analysis**
- **Two loops**: Both run independently
- **First loop**: O(n) operations
- **Second loop**: O(n) operations
- **Total**: O(n) + O(n) = O(2n) = **O(n)**

#### ✅ **Answer: O(n) - Linear**

---

### 📚 **Question 2: Nested Loops (All Pairs)**

```python
L = [1, 2, 3, 4, 5]

for i in L:
    for j in L:
        print("({},{})".format(i, j))

# Output: (1,1), (1,2), (1,3), (1,4), (1,5), 
#         (2,1), (2,2), (2,3), (2,4), (2,5), ...
```

#### 🔍 **Analysis**
- **Outer loop**: n iterations
- **Inner loop**: n iterations for each outer iteration
- **Total operations**: n × n = n²

#### ✅ **Answer: O(n²) - Quadratic**

---

### 📚 **Question 3: Integer to String Conversion**

```python
def intToString(i):
    digits = "0123456789"
    if i == 0:
        return "0"
    result = ""
    while i > 0:
        result = digits[i % 10] + result
        i = i // 10
    return result
```

#### 🔍 **Step-by-Step Analysis**

| Input | Iterations | Pattern |
|-------|------------|---------|
| 123 | 3 steps | 123→12→1→0 |
| 1234 | 4 steps | 1234→123→12→1→0 |
| 12345 | 5 steps | 12345→1234→123→12→1→0 |

#### 🧮 **Mathematical Insight**
- **Input grows 10x** → **Operations grow +1**
- **Input**: 10, 100, 1000, 10000
- **Operations**: 1, 2, 3, 4
- **Pattern**: Logarithmic growth

#### ✅ **Answer: O(log n) - Logarithmic**

---

### 📚 **Question 4: Modified Nested Loops**

```python
n = 1000
for i in range(n//2, n+1):    # Outer: n/2 iterations
    for j in range(2, n+1, 2): # Inner: n/2 iterations  
        k = i + j/2
```

#### 🔍 **Analysis**
- **Outer loop**: Runs n/2 times
- **Inner loop**: Runs n/2 times (step=2)
- **Total**: (n/2) × (n/2) = n²/4 = **O(n²)**

#### ✅ **Answer: O(n²) - Quadratic**

---

### 📚 **Question 5: Different Array Pairs**

```python
for i in range(0, len(L)):
    for j in range(i+1, len(L)):
        print("({},{})".format(L[i], L[j]))
```

#### 🔍 **Analysis**
- **Outer loop**: n iterations
- **Inner loop**: Varies based on i
  - i=0: n-1 iterations
  - i=1: n-2 iterations  
  - i=2: n-3 iterations
- **Total**: (n-1) + (n-2) + ... + 1 = n(n-1)/2 = **O(n²)**

#### ✅ **Answer: O(n²) - Quadratic**

---

### 📚 **Question 6: Two Different Arrays**

```python
A = [1, 2, 3, 4]
B = [2, 3, 4, 5, 6]

for i in A:           # |A| iterations
    for j in B:       # |B| iterations for each i
        if i < j:
            print("({},{})".format(i, j))
```

#### 🔍 **Analysis**
- **Complexity**: O(|A| × |B|)
- **More precise**: O(a × b) where a=len(A), b=len(B)
- **If both same size**: O(n²)

#### ✅ **Answer: O(a × b) or O(n²) if equal**

---

### 📚 **Question 7: Constant Inner Loop**

```python
A = [1, 2, 3, 4]  
B = [2, 3, 4, 5]

for i in A:                    # n iterations
    for j in B:                # m iterations  
        for k in range(1000000): # Constant!
            print("({},{})".format(i, j))
```

#### 🔍 **Analysis**
- **Innermost loop**: Constant 1,000,000 iterations
- **Middle loop**: m iterations
- **Outer loop**: n iterations
- **Total**: n × m × 1,000,000 = **O(n × m)**

#### ✅ **Answer: O(n²) - Quadratic (if n=m)**

---

## 🟡 **MEDIUM LEVEL QUESTIONS (8-12)**

### 📚 **Question 8: Half Array Processing**

```python
L = [1, 2, 3, 4, 5]

for i in range(0, len(L)//2):   # n/2 iterations
    other = L[i]
    temp = L[i]  
    L[i] = L[other]
    L[other] = temp
print(L)
```

#### 🔍 **Analysis**
- **Loop runs**: n/2 times
- **Operations inside**: Constant
- **Total**: n/2 = **O(n)**

#### ✅ **Answer: O(n) - Linear**

---

## 🔴 **RECURSION ANALYSIS (9-15)**

### 📚 **Question 9: Factorial Recursion**

```python
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n-1)

print(factorial(5))
```

#### 🔍 **Function Call Analysis**

| Input | Function Calls | Pattern |
|-------|----------------|---------|
| 5 | 5 calls | 5→4→3→2→1 |
| 10 | 10 calls | 10→9→8→...→1 |
| 200 | 200 calls | 200→199→...→1 |

#### ✅ **Answer: O(n) - Linear**

---

### 📚 **Question 10: Fibonacci Recursion**

```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

#### 🔍 **Call Tree Analysis**

| Input | Approximate Calls | Growth Pattern |
|-------|------------------|----------------|
| 1 | 1 | Base case |
| 2 | 3 | Small tree |
| 3 | 5 | Growing |
| 5 | ~15 | Exponential |
| 6 | ~25 | Rapid growth |

#### 🧮 **Mathematical Proof**
- **Each call generates 2 more calls**
- **Input increases by +1** → **Calls multiply by ~2**
- **Pattern**: Exponential growth

#### ✅ **Answer: O(2^n) - Exponential**

---

### 📚 **Question 11: Powers of 2 Recursion**

```python
def print_powers(n):
    if n < 1:
        return
    print_powers(n//2)
    print(n)

print_powers(145)
# Output: 1, 2, 4, 8, 16, 32, 64, 128
```

#### 🔍 **Function Call Pattern**

| Input | Calls | Sequence |
|-------|-------|----------|
| 100 | 8 | 100→50→25→12→6→3→1 |
| 1000 | 11 | 1000→500→250→125→62→31→15→7→3→1 |

#### 🧮 **Pattern Recognition**
- **Input divided by 2 each time**
- **Input × 10** → **Calls + ~3**
- **Classic logarithmic pattern**

#### ✅ **Answer: O(log n) - Logarithmic**

---

### 📚 **Question 12: Simple Modulo Operation**

```python
def mod_operation(a, b):
    return a % b

result = mod_operation(5, 3)  # Returns 2
```

#### 🔍 **Analysis**
- **No loops**
- **No recursion**  
- **Only arithmetic operations**
- **Modern processors**: Arithmetic in constant time

#### ✅ **Answer: O(1) - Constant**

---

## 🔥 **ADVANCED LEVEL QUESTIONS (13-18)**

### 📚 **Question 13: Digit Extraction (Revisited)**

```python
def count_digits(n):
    count = 0
    while n > 0:
        count += 1
        n = n // 10
    return count
```

#### 🔍 **Same Pattern as Question 3**
- **Number divided by 10 each iteration**
- **Logarithmic growth pattern**

#### ✅ **Answer: O(log n) - Logarithmic**

---

### 📚 **Question 14: Recurrence Relations**

#### 🧮 **Mathematical Expression**
```
T(n) = 3 × T(n-1)
T(0) = 1
```

#### 🔍 **Step-by-Step Calculation**

| n | T(n) | Calculation |
|---|------|-------------|
| 0 | 1 | Base case |
| 1 | 3 | 3 × T(0) = 3 × 1 = 3 |
| 2 | 9 | 3 × T(1) = 3 × 3 = 9 |
| 3 | 27 | 3 × T(2) = 3 × 9 = 27 |
| 4 | 81 | 3 × T(3) = 3 × 27 = 81 |

#### 🧮 **Mathematical Solution**
```
T(n) = 3 × T(n-1)
     = 3 × 3 × T(n-2)  
     = 3² × T(n-2)
     = 3³ × T(n-3)
     = ...
     = 3ⁿ × T(0)
     = 3ⁿ × 1
     = 3ⁿ
```

#### ✅ **Answer: O(3^n) - Exponential**

---

### 📚 **Question 15: Modified Recurrence**

#### 🧮 **Mathematical Expression**
```
T(n) = 2 × T(n-1) - 1
T(0) = 1
```

#### 🔍 **Mathematical Solution**
```
T(n) = 2 × T(n-1) - 1
     = 2 × [2 × T(n-2) - 1] - 1
     = 2² × T(n-2) - 2 - 1
     = 2² × T(n-2) - (2¹ + 2⁰)
     = 2³ × T(n-3) - (2² + 2¹ + 2⁰)
     = ...
     = 2ⁿ × T(0) - (2^(n-1) + ... + 2¹ + 2⁰)
     = 2ⁿ × 1 - (2ⁿ - 1)
     = 2ⁿ - 2ⁿ + 1
     = 1
```

#### ✅ **Answer: O(1) - Constant**

---

### 📚 **Question 16: Power Set Generation**

```python
def generate_powerset(s):
    if len(s) == 0:
        return [[]]
    
    first = s[0]
    rest = s[1:]
    
    # Get powerset of rest
    powerset_rest = generate_powerset(rest)
    
    # Generate new combinations
    result = []
    for subset in powerset_rest:
        result.append(subset)           # Without first
        result.append([first] + subset) # With first
    
    return result
```

#### 🔍 **Growth Analysis**

| Input Size | Output Size | Pattern |
|------------|-------------|---------|
| 1 | 2 | {}, {1} |
| 2 | 4 | {}, {1}, {2}, {1,2} |
| 3 | 8 | All subsets of {1,2,3} |
| 4 | 16 | All subsets of {1,2,3,4} |

#### 🧮 **Mathematical Insight**
- **Each element**: Include or exclude (2 choices)
- **n elements**: 2 × 2 × ... × 2 = 2ⁿ combinations
- **Algorithm must generate all combinations**

#### ✅ **Answer: O(2^n) - Exponential**

---

## 📊 **Summary of All Answers**

| Question | Algorithm Type | Time Complexity | Reasoning |
|----------|---------------|-----------------|-----------|
| 1 | Independent Loops | **O(n)** | Two separate O(n) loops |
| 2 | Nested Loops | **O(n²)** | n × n iterations |
| 3 | Integer to String | **O(log n)** | Divide by 10 each step |
| 4 | Modified Nested | **O(n²)** | (n/2) × (n/2) = n²/4 |
| 5 | Pair Generation | **O(n²)** | Triangular iteration pattern |
| 6 | Two Arrays | **O(a×b)** | Different array sizes |
| 7 | Constant Inner | **O(n²)** | Constant doesn't affect growth |
| 8 | Half Array | **O(n)** | n/2 operations |
| 9 | Factorial Recursion | **O(n)** | n function calls |
| 10 | Fibonacci Recursion | **O(2^n)** | Exponential call tree |
| 11 | Powers of 2 | **O(log n)** | Divide by 2 each step |
| 12 | Modulo Operation | **O(1)** | Single arithmetic operation |
| 13 | Digit Counting | **O(log n)** | Divide by 10 pattern |
| 14 | Recurrence T(n)=3T(n-1) | **O(3^n)** | Exponential growth |
| 15 | Modified Recurrence | **O(1)** | Telescoping series |
| 16 | Power Set | **O(2^n)** | Generate all subsets |

---

## 🎯 **Key Learning Patterns**

### 🔄 **Loop Patterns**
- **Single Loop**: O(n)
- **Nested Loops**: O(n²)  
- **Independent Loops**: Add complexities
- **Constant Iterations**: Don't affect growth

### 🔁 **Recursion Patterns**
- **Linear Recursion**: O(n) - factorial
- **Divide by 2**: O(log n) - binary operations
- **Tree Recursion**: O(2^n) - fibonacci
- **Mathematical Relations**: Solve algebraically

### 📈 **Growth Recognition**
- **Divide by constant**: Logarithmic
- **Add constant**: Linear  
- **Multiply by constant**: Exponential
- **Arithmetic operations**: Constant

---

## 💡 **Practice Strategy Tips**

### ✅ **Step-by-Step Approach**
1. **Identify the structure**: Loops, recursion, or arithmetic
2. **Count operations**: How many times does core operation run?
3. **Analyze growth**: How does operation count change with input?
4. **Apply simplification**: Remove constants, keep highest order
5. **Verify with examples**: Test with small inputs

### 🚀 **Mastery Indicators**
- **Pattern Recognition**: Quickly identify complexity type
- **Mathematical Intuition**: Understand growth relationships  
- **Edge Case Awareness**: Handle tricky recurrence relations
- **Speed**: Solve within 30 seconds for basic problems

---

*📚 These 18 practice problems cover the essential patterns you'll encounter in algorithm analysis. Master these, and you'll be well-prepared for both technical interviews and real-world performance optimization!*
