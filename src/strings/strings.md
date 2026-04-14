# Strings & Arrays

---

## 1. 125. Valid Palindrome `[1/29][3/16]`

**Pattern:** Two pointers from both ends, skip non-alphanumeric characters.

**Key Insight:** Use `str.isalnum()` to check if a character is alphanumeric (works for both letters and digits).

> Watch out: don't let pointers go out of array bounds when skipping characters.

---

## 2. 670. Maximum Swap `[2/23][3/16][6/3]`

**Pattern:** For each digit, find the rightmost larger digit to its right. Swap the leftmost such pair.

**Key Insight:** Build a map `last[digit] = last_index`. For each position left to right, check digits 9 down to current+1 — if a larger digit appears later, swap and return.

---

## 3. 1868. Product of Two Run-Length Encoded Arrays `[2/23][3/16]`

**Pattern:** Two pointers, one per encoded array. Consume the minimum run length of both, emit result, advance whichever runs out.

---

## 4. 680. Valid Palindrome II `[3/9][6/1]`

**Pattern:** Two pointers. On first mismatch, try skipping either left or right character, check if remaining is a palindrome.

---

## 5. 408. Valid Word Abbreviation `[3/16]`

**Pattern:** Two pointers on word and abbr simultaneously. When a digit is seen in abbr, parse the full number and advance word pointer by that count.

> Watch out: abbreviations like `01` (leading zero) are invalid.

---

## 6. 498. Diagonal Traverse `[3/11][3/28]`

**Pattern:** Simulate direction changes. Going up-right: `r-=1, c+=1`. Going down-left: `r+=1, c-=1`. Reverse direction at boundaries.

---

## 7. 647. Palindromic Substrings `[3/22]`

**Pattern:** Expand around center. For each character, expand treating it as:
- Single center (odd-length palindromes)
- Gap between `i` and `i+1` (even-length palindromes)

Count every successful expansion.

---

## 8. 8. String to Integer (atoi) `[3/22]`

**Pattern:** State machine — states: start, signed, in_number, end.

**Key Insight:** Handle leading whitespace → optional sign → digits → stop on non-digit. Clamp result to `[-2^31, 2^31-1]`.

---

## 9. 791. Custom Sort String `[3/9][3/28]`

**Pattern:** Count characters in `s`, then output in order of `order`, appending remaining chars.

---

## 10. 26. Remove Duplicates from Sorted Array `[3/19]`

**Pattern:** Two pointers — slow pointer marks the next write position, fast pointer scans.

---
