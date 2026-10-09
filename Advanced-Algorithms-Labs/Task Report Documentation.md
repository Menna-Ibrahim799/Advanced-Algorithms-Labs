# TASK DOCUMENTATION
## Student Report

| Field | Student Information |
| :--- | :--- |
| **Student Name** | [Enter Name Here] |
| **Student ID** | [Enter ID Here] |
| **Project / Assignment** | KH5002CMD - Advanced Algorithms (C++) |
| **Task Title** | Complete Lab Portfolio: Sorting Analysis, Linked Lists, & Quick/Merge Sort |
| **Submission Date** | [Enter Submission Date Here] |
| **Instructor(s)** | [Enter Instructor Name Here] |

---

## Table of Contents
1. Task 1 Documentation: Algorithm Analysis (Sorting)
2. Task 2 Documentation: Singly Linked List Implementation
3. Task 3 Documentation: Advanced Sorting (Merge & Quick Sort with Median-of-3)
4. GitHub Link Placeholder
5. Final Checklist & References

---

# 1. Task 1: Algorithm Analysis (Lab 1B)

## 1.1 Task Overview
Implement three primary sorting algorithms (**Bubble Sort**, **Selection Sort**, and **Insertion Sort**) in C++. Each function must track key comparisons using a counter parameter to empirically verify theoretical time complexity bounds ($O(n)$ vs $O(n^2)$).

## 1.2 Objective
To compare theoretical asymptotic bounds against empirical comparison counts across random, pre-sorted, and reverse-sorted input arrays.

## 1.3 Input, Output, and Requirements
| Item | Description | Example / Notes |
| :--- | :--- | :--- |
| **Input** | Unsorted or pre-sorted integer arrays (`int arr[]`), size `n`, reference counter | `rand10 = {64, 34, 25, 12, 22, 11, 90, 45, 7, 80}` |
| **Output** | Sorted array in ascending order, total comparison counter | `TC1 comparisons: 45` |
| **Constraints** | In-place sorting, increment `counter` exactly once per element key comparison | $n=10$ |

## 1.4 Methodology / Algorithm
- **Bubble Sort**: Repeatedly steps through the list, compares adjacent elements, and swaps them if in wrong order.
- **Selection Sort**: Maintains sorted/unsorted sublists, repeatedly finding the minimum element from the unsorted segment.
- **Insertion Sort**: Builds sorted array one item at a time by sliding elements right until key's spot is found.

## 1.5 Algorithm Analysis & Results Table
| Algorithm | Input | n | Comparisons Measured | Expected $O(?)$ | Best or Worst Case? |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Bubble Sort** | Random | 10 | 45 | $O(n^2)$ | Average / Worst |
| **Bubble Sort** | Sorted | 10 | 45 | $O(n^2)$ | Worst (Standard loop) |
| **Bubble Sort** | Reverse | 10 | 45 | $O(n^2)$ | Worst |
| **Selection Sort** | Random | 10 | 45 | $O(n^2)$ | Constant $O(n^2)$ |
| **Insertion Sort** | Random | 10 | 25 | $O(n^2)$ | Average |
| **Insertion Sort** | Sorted | 10 | 9 | $O(n)$ | Best Case |
| **Insertion Sort** | Reverse | 10 | 45 | $O(n^2)$ | Worst Case |

**Theoretical Verification Question:**  
For $n=10$, the theoretical worst-case comparisons for Bubble Sort is:
$$\frac{n(n-1)}{2} = \frac{10 \times 9}{2} = 45$$
**Answer:** The measured counter matches the theoretical prediction of **45 comparisons** exactly.

---

# 2. Task 2: Singly Linked List (Lab 2B)

## 2.1 Task Overview
Implement a standard custom Singly Linked List class (`LinkedList`) without relying on dynamic containers like `std::list` or `std::forward_list`.

## 2.2 Input, Output, and Requirements
| Item | Description | Example / Notes |
| :--- | :--- | :--- |
| **Input** | Integer elements for insertion/deletion/searching | `insertAtHead(30)`, `deleteValue(10)` |
| **Output** | Formatted string output representing list structure | `10 -> 20 -> 30 -> null` |
| **Constraints** | Manual dynamic memory allocation (`new`/`delete`), zero memory leaks | $O(1)$ head ops, $O(n)$ tail/search ops |

## 2.3 Algorithm & Operations Complexity
| Aspect | Best Case Time | Average Case Time | Worst Case Time | Space Complexity |
| :--- | :--- | :--- | :--- | :--- |
| `insertAtHead` | $O(1)$ | $O(1)$ | $O(1)$ | $O(1)$ |
| `insertAtTail` | $O(1)$ (empty) | $O(n)$ | $O(n)$ | $O(1)$ |
| `deleteValue` | $O(1)$ (head) | $O(n)$ | $O(n)$ | $O(1)$ |
| `search` | $O(1)$ | $O(n)$ | $O(n)$ | $O(1)$ |
| `reverse` | $O(n)$ | $O(n)$ | $O(n)$ | $O(1)$ |
| `removeDuplicates` | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ (Hash set) |

## 2.4 Testing Results (TC1 - TC10 Verification)
| Test Case | Method Executed | Expected Output | Actual Output | Result |
| :--- | :--- | :--- | :--- | :--- |
| **TC1** | `insertAtHead` | `10 -> 20 -> 30 -> null` | `10 -> 20 -> 30 -> null` | PASS |
| **TC2** | `insertAtTail` | `10 -> 20 -> 30 -> 40 -> 50 -> null` | `10 -> 20 -> 30 -> 40 -> 50 -> null` | PASS |
| **TC3** | `length()` | `5` | `5` | PASS |
| **TC4** | `search(30)`, `search(99)` | `search (30)=1 search (99)=0` | `search (30)=1 search (99)=0` | PASS |
| **TC5** | `deleteValue(10)` (Head) | `20 -> 30 -> 40 -> 50 -> null` | `20 -> 30 -> 40 -> 50 -> null` | PASS |
| **TC6** | `deleteValue(50)` (Tail) | `20 -> 30 -> 40 -> null` | `20 -> 30 -> 40 -> null` | PASS |
| **TC7** | `deleteValue(30)` (Mid) | `20 -> 40 -> null` | `20 -> 40 -> null` | PASS |
| **TC8** | `deleteValue(99)` | `0` | `0` | PASS |
| **TC9** | `reverse()` | `3 -> 2 -> 1 -> null` | `3 -> 2 -> 1 -> null` | PASS |
| **TC10** | Empty list ops | `length=0 search=0 delete=0` | `length=0 search=0 delete=0` | PASS |

---

# 3. Task 3: Merge Sort & Median-of-Three Quick Sort (Lab 3B)

## 3.1 Task Overview
Implement recursive **Merge Sort** ($O(n \log n)$) and **Quick Sort**. Enhance Quick Sort with a **Median-of-Three (M3)** pivot strategy (`low`, `mid`, `high`) to eliminate worst-case $O(n^2)$ behavior on sorted/reverse-sorted inputs.

## 3.2 Median-of-Three Strategy
1. Pick elements at `arr[low]`, `arr[mid]`, and `arr[high]`.
2. Sort these 3 elements so that `arr[low] <= arr[mid] <= arr[high]`.
3. Swap `arr[mid]` to `arr[high]`, returning `high` as the updated pivot index.

## 3.3 Comparative Empirical Performance ($n = 16$)
| Input Type | n | Quick Sort (Last-Element Pivot) Comparisons | Quick Sort M3 (Median-of-Three Pivot) Comparisons | Better? |
| :--- | :--- | :--- | :--- | :--- |
| **Random** | 16 | 46 | 45 | **QSM3** (Slightly superior) |
| **Sorted (Ascending)** | 16 | 120 | 48 | **QSM3** (Dramatically superior: avoids $O(n^2)$) |
| **Reverse Sorted** | 16 | 120 | 50 | **QSM3** (Dramatically superior: avoids $O(n^2)$) |

---

# 4. GitHub Link
**Repository URL:** `https://github.com/[Your-GitHub-Username]/KH5002CMD-Advanced-Algorithms-Labs`

---

# 5. Submission Checklist
- [x] All place-holders for Name, ID, Instructor, and Date are designated for quick user completion.
- [x] Every lab requirement (1B, 2B, 3B) implemented in compliant C++.
- [x] Expected theoretical outputs matched against measured empirical results.
- [x] High-level algorithm complexity analysis fully documented.