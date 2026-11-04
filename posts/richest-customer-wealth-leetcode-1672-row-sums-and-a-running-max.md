---
title: "Richest Customer Wealth (LeetCode 1672): Row Sums and a Running Max"
slug: richest-customer-wealth-leetcode-1672-row-sums-and-a-running-max
date: 2026-11-04
published: true
public: true
---

You get an `m x n` grid `accounts`, where `accounts[i][j]` is how much money customer `i` keeps in bank `j`. A customer's wealth is the sum of their row. Return the largest wealth.

It is an easy warm-up, but interviewers like it because it shows whether you read the grid correctly (rows are customers, columns are banks) and whether you avoid extra memory.

## The idea

Walk the rows. For each row, add its numbers, then compare with the best total so far.

```python
def maximumWealth(accounts):
    best = 0
    for row in accounts:
        total = sum(row)
        if total > best:
            best = total
    return best
```

A one-liner works too: `return max(map(sum, accounts))`. In an interview, say both: the loop shows the logic, the one-liner shows you know the language.

## Complexity

- Time: O(m * n), because every cell is read once.
- Space: O(1) extra, since only `best` and `total` are stored.

## Edge cases to mention

- A single customer: the answer is that row's sum.
- Starting `best` at 0 is safe because the constraints say every amount is at least 1. If negatives were allowed, start from the first row's sum instead.
- Very large grids: Python integers don't overflow; in Java or C++ check that the sum fits in an `int` (here it does, at most 50 * 100).

## Follow-up questions you may hear

1. *Return the index of the richest customer.* Track the index alongside `best`.
2. *Ties?* Ask whether the first or all indices should be returned.
3. *Accounts stream in one customer at a time?* The same running max works with O(1) memory.

## Practicing for the real round

Easy questions like this are usually the opener, and the follow-ups are where you earn points. Talking through them out loud helps. If you want live hints while you practice, the [Linkjob AI coding interview copilot](https://www.linkjob.ai/coding-interview-copilot/) can suggest approaches and complexity notes in real time.

*Disclosure: this note was written by the Linkjob AI team.*