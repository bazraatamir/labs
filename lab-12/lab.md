# Recursion, Tail Recursion, Divide & Conquer, Backtracking

## 1. Recursion гэж юу вэ?

Recursion гэдэг нь **нэг функц өөрийгөө шууд эсвэл шууд бусаар дахин дуудах** программчлалын техник юм.

### Гол ойлголт:

- **Base Case** → дахин дуудах хэрэггүй, termination нөхцөл.
- **Recursive Case** → асуудлыг жижигрүүлэн өөрийгөө дахин дуудна.
- Recursion нь **Stack (Call Stack)** дээр тулгуурладаг → function бүр өөрийн state-тайгаар стек дээр байрлана.

### Жишээ (Factorial):

```python
def factorial(n):
    if n == 0:            # Base Case
        return 1
    return n * factorial(n - 1)  # Recursive Case
```

### Dry Run (n = 3):

- factorial(3) → 3 × factorial(2)
- factorial(2) → 2 × factorial(1)
- factorial(1) → 1 × factorial(0)
- factorial(0) → 1 ⬅ Base Case хүрлээ → буцаж эхэлнэ
- Stack Unwind → 1 → 1×1 → 2×1 → 3×2 → **6**

---

## 2. Tail Recursion гэж юу вэ?

Tail Recursion гэдэг нь **функц өөрийгөө дуудаж байгаа тэр хэсэг нь function-ийн хамгийн сүүлийн үйлдэл байх** recursion-ын төрөл.

### Яагаад онцгой гэж?

- Tail recursion нь **stack дээр нэмэлт frame үүсгэхгүйгээр**, тухайн function-ий frame-ийг **reuse хийх** боломжтой тул **memory-efficient** байх ёстой.
- **Гэхдээ Python tail call optimization хийдэггүй!** → энэ нь Python-д tail recursion ашиглавал **stack overflow** эрсдэлтэй.
- Харин **C, Haskell, Scala** зэрэг хэлнүүд tail recursion-г автоматаар optimize хийдэг.

### Жишээ (Tail Recursion version of factorial):

```python
def factorial_tail(n, acc=1):
    if n == 0:               # Base Case
        return acc
    return factorial_tail(n - 1, n * acc)  # Tail Call = last operation
```

### Энд юу онцгой вэ?

- `return n * factorial(n - 1)` → **Tail биш** (return-ын дараа үржих процесс хүлээгдэж байгаа!)
- `return factorial_tail(n - 1, n * acc)` → **Tail Call** ✅ (буцахдаах үйлдэл байхгүй)

---

## 3. Divide & Conquer арга

Divide & Conquer (D&C) гэдэг нь **асуудлыг жижиг хэсгүүдэд хувааж, тус бүрийг шийдэж, дараа нь хариуг нэгтгэн шийдвэр гаргах** алгоритмын аргачлал юм.

### Гол алхамууд:

1. **Divide** → Асуудлыг жижиг хэсгүүдэд хуваана.
2. **Conquer** → Бүх хэсгийг recursive аргаар шийднэ.
3. **Combine** → Шийдлийг нэгтгэн эцсийн хариуг гаргана.

### Жишээ алгоритмууд:

- Merge Sort
- Quick Sort
- Binary Search
- Matrix Multiplication (Strassen)

### Recurrence Relation:

- Merge Sort: T(n) = 2\*T(n/2) + O(n)
- Quick Sort (average case): T(n) = 2\*T(n/2) + O(n)
- Quick Sort (worst case): T(n) = T(n-1) + O(n)

### Master Theorem ашиглах:

- T(n) = a\*T(n/b) + f(n)
- Merge Sort → a=2, b=2, f(n)=n → O(n log n)
- Quick Sort → worst case → O(n^2), average case → O(n log n)

---

## 4. Backtracking арга

Backtracking гэдэг нь **бүх боломжит шийдлийг судалж, шийдэл олдохгүй бол буцаж өмнөх state руу эргэж орох** алгоритмын арга юм.

### Гол ойлголт:

- **State Space Tree** → бүх боломжит шийдлийг модон хэлбэрээр дүрсэлнэ.
- **Decision / Choice** → тухайн түвшинд хийх боломжит алхмууд.
- **Constraint** → зөв шийдлийг хадгалах нөхцөл.
- **Backtrack** → Constraint зөрчсөн тохиолдолд өмнөх түвшинд эргэн очно.

### Жишээ (N-Queens):

```python
N = 4
def print_board(board):
    for row in board:
        print(" ".join(row))
    print()

def is_safe(board, row, col):
    for i in range(row):
        if board[i][col] == 'Q':
            return False
    for i,j in zip(range(row-1,-1,-1), range(col-1,-1,-1)):
        if board[i][j] == 'Q':
            return False
    for i,j in zip(range(row-1,-1,-1), range(col+1,N)):
        if board[i][j] == 'Q':
            return False
    return True

def solve(board, row=0):
    if row == N:
        print_board(board)
        return
    for col in range(N):
        if is_safe(board, row, col):
            board[row][col] = 'Q'
            solve(board, row+1)
            board[row][col] = '.'  # Backtrack

board = [['.' for _ in range(N)] for _ in range(N)]
solve(board)
```

### Онолын тайлбар:

- Function нь **row-уудаар давталт** хийж, бүх багана дээр Queen байрлуулна.
- Хэрэв **Constraint зөрчвөл** буцааж өмнөх cell рүү эргэн очно.
- Энэ нь **decision tree-г exhaustive search** аргаар судалж байгаа жишээ юм.

### Big-O тайлбар:

- N-Queens-ийн хамгийн муу case → O(N!)
- Constraint хэрэгжих тусам search space багасна.

---

## Дүгнэлт

| Арга             | Онцлог                         | Жишээ                  | Big-O               |
| ---------------- | ------------------------------ | ---------------------- | ------------------- |
| Recursion        | Функц өөрийгөө дуудах          | Factorial, Fibonacci   | O(n) / O(2^n)       |
| Tail Recursion   | Last operation recursive       | Factorial Tail         | O(n)                |
| Divide & Conquer | Divide → Conquer → Combine     | Merge Sort, Quick Sort | O(n log n) / O(n^2) |
| Backtracking     | State space tree + constraints | N-Queens, Sudoku       | O(N!) / variable    |

Энэхүү хичээл нь **их сургууль / экзаменд бэлдэх түвшний онол + Python жишээ + Big-O analysis**-г хамарсан академик бүтэц юм.

## Recursion, Tail Recursion, Divide & Conquer, Backtracking

Дасгал ажилууд + Алхам алхмаар тайлбар + Жишээ оролт, гаралт

1. Recursion
   Дасгал 1: Factorial

# Даалгавар: n! олох функц бич.

Алхам:

Base case: n==0 → 1 буцаана.

Recursive case: n \* factorial(n-1) буцаана.

print(factorial(5))

Оролт: 5

Гаралт: 120

Дасгал 2: Fibonacci

# Даалгавар: n-р Fibonacci утгыг олох.

Оролт: n=7

Гаралт: [0, 1, 1, 2, 3, 5, 8]

2. Tail Recursion

# Дасгал: Tail Factorial

Даалгавар: Tail recursion ашиглан factorial олох.

Оролт: 6

Гаралт: 720

3. Divide & Conquer
   Дасгал 1: Merge Sort

# Даалгавар: [38, 27, 43, 3, 9, 82, 10] массивыг эрэмбэл.

Оролт: [38,27,43,3,9,82,10]

Гаралт: [3, 9, 10, 27, 38, 43, 82]

Дасгал 2: Quick Sort

Даалгавар: [29,10,14,37,14] массивыг Quick Sort-оор эрэмбэл.

Оролт: [29,10,14,37,14]

Гаралт: [10, 14, 14, 29, 37]

4. Backtracking

# Дасгал 1: N-Queens

Даалгавар: N=4, бүх боломжит шийдлийг хэвлэ.

Оролт: N=4

Гаралт: 2 боломжит шийдэл (Queen байрлалт модон хэлбэрээр)

### Дасгал 2: Permutations

Даалгавар: 'ABC' string-ийн бүх боломжит permutation гаргах.

Оролт: 'ABC'

Гаралт: ABC, ACB, BAC, BCA, CBA, CAB

## Дасгал ажилууд (Хүнд шат)

### 1. Recursion (Advanced)

#### Дасгал 1: Factorial array sum

- **Даалгавар:** Өгөгдсөн list дахь factorial-уудын нийлбэрийг recursion ашиглан олох.
- **Оролт:** [3, 4, 5]

- **Гаралт:** 3!+4!+5! = 6+24+120 = 150

#### Дасгал 2: Recursive string reverse

- Өгөгдсөн string-г recursion ашиглан эргүүл.
- **Оролт:** 'Algorithm'
- **Гаралт:** 'mhtiroglA'

### 2. Tail Recursion (Advanced)

#### Дасгал: Tail Fibonacci

- **Даалгавар:** Tail recursion ашиглан n-р Fibonacci утгыг ол. n=10

- **Гаралт:** 55

### 3. Divide & Conquer (Advanced)

#### Дасгал 1: Merge k sorted arrays

- **Даалгавар:** k=3 sorted arrays-ийг нэг array болгон merge хийх.
- **Оролт:** [[1,4,7],[2,5,8],[3,6,9]]

- **Гаралт:** [1,2,3,4,5,6,7,8,9]

#### Дасгал 2: Quick Sort with median pivot

- Өгөгдсөн массивыг Quick Sort ашиглан median pivot-оор эрэмбэл.

### 4. Backtracking (Advanced)

#### Дасгал 1: N-Queens, N=8

- **Даалгавар:** 8x8 самбар дээр бүх шийдлийг ол.

#### Дасгал 2: Sudoku Solver 9x9

- **Даалгавар:** 9x9 sudoku-г backtracking ашиглан шийд.

#### Дасгал 3: Word Search Problem

- **Даалгавар:** Өгөгдсөн 2D grid-д string-г backtracking ашиглан хайж, байгаа эсэхийг шалгах.
- **Оролт:** Grid = [['A','B','C'],['D','E','F'],['G','H','I']], word='BEF'
- **Гаралт:** True

```

```
