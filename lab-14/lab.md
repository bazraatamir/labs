# Dynamic Programming — Overlapping Subproblems Examples

---

## 1. Fibonacci Sequence

n дахь Фибоначчийн тоог ол.
**Сонголт:** Top-Down эсвэл Bottom-Up (хоёул сайн)
**Тайлбар:** 1D, бага state → bottom-up илүү хялбар, top-down логик ойлгомжтой. Space optimize: O(1)

**Жишээ:**

```
Input: n = 10
Output: 55

Explanation:
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55
The 10th Fibonacci number is 55.
```

---

## 2. Climbing Stairs

Нэг удаад 1 эсвэл 2 шат өгсөж чадна. n шаттай байшин руу хэдэн янзаар гарч болох
вэ?

**Сонголт:** Bottom-Up эсвэл Top-Down
**Тайлбар:** 1D dp, bottom-up илүү хурдан, top-down цэвэр логик. Space O(1)

**Жишээ:**

```
Input: n = 5
Output: 8

Explanation:
8 ways to climb 5 stairs using 1 or 2 steps:
1+1+1+1+1, 1+1+1+2, 1+1+2+1, 1+2+1+1, 2+1+1+1, 1+2+2, 2+1+2, 2+2+1
```

---

## 3. Min Cost Climbing Stairs

Шат бүр тодорхой зардалтай. Дээд шатанд хүрэх хамгийн бага нийт зардлыг ол.

**Сонголт:** Bottom-Up илүү түгээмэл
**Тайлбар:** dp[i] = cost[i] + min(dp[i-1], dp[i-2]). Space O(1)

**Жишээ:**

```
Input: cost = [10, 15, 20]
Output: 15

Explanation:
Minimum cost to reach top: min(10+20, 15) = 15
```

---

## 4. House Robber

Хэрвээ хажуугийн 2 байшинг зэрэг дээрэмдэх боломжгүй бол хамгийн их мөнгө
хулгайлах арга.

**Сонголт:** Bottom-Up давамгай
**Тайлбар:** simple 1D recurrence (exclude/include). Space O(1)

**Жишээ:**

```
Input: nums = [2,7,9,3,1]
Output: 12

Explanation:
Rob houses 1, 3, 5 → 2 + 9 + 1 = 12
```

---

## 5. Unique Paths (m x n)

m x n хэмжээтэй хүснэгтэд зүүн дээдээс баруун доод буланд хүрэх замын тоог ол
(зөвхөн доош, баруун тийш алхаж болно).

**Сонголт:** Bottom-Up түгээмэл
**Тайлбар:** dp[i][j] = dp[i-1][j] + dp[i][j-1]. Space optimize: 1D row O(n)

**Жишээ:**

```
Input: m = 3, n = 7
Output: 28

Explanation:
28 unique paths from top-left to bottom-right moving only down or right
```

---

## 6. Coin Change Problem (min coins)

Өгөгдсөн зоосны утгууд ашиглан тодорхой мөнгөний дүнг гаргах хамгийн бага
зоосны тоог ол.

**Сонголт:** Bottom-Up түгээмэл
**Тайлбар:** dp[amount] = min(dp[amount], dp[amount-coin]+1)

**Жишээ:**

```
Input: coins = [1, 2, 5], amount = 11
Output: 3

Explanation:
11 = 5 + 5 + 1 → minimum 3 coins
```

---

## 7. Partition Equal Subset Sum

Өгөгдсөн тоонуудаас нийлбэр нь яг тал хувийн тэнцүү болох 2 бүлэг үүсгэж болох
уу?

**Сонголт:** Bottom-Up хэвийн
**Тайлбар:** subset sum → boolean dp, 1D bitset оптимизац сайхан

**Жишээ:**

```
Input: nums = [1, 5, 11, 5]
Output: true

Explanation:
Can partition into [1, 5, 5] and [11] (both sum = 11)
```

---

## 8. Maximum Subarray Sum (Kadane’s Algorithm)

Нэг хэмжээст массиваас хамгийн их нийлбэртэй дэд массиваа ол.

**Сонголт:** Neither classic DP forms — Kadane (iterative) хамгийн сайн
**Тайлбар:** Шууд O(n) итератив

**Жишээ:**

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6

Explanation:
Subarray [4,-1,2,1] has maximum sum = 6
```

---

## 9. Subset Sum Count

Өгөгдсөн массивын дундаас нийлбэр нь X болох хэдэн дэд бүлэг байгааг тоол.

**Сонголт:** Bottom-Up түгээмэл (1D possible)
**Тайлбар:** count of subsets → dp[sum] update (reverse loop) эсвэл 2D

**Жишээ:**

```
Input: nums = [1,2,3,3], sum = 6
Output: 3

Explanation:
Subsets with sum = 6 are: [1,2,3], [1,2,3], [3,3]
```
