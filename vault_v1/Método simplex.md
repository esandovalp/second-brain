#linealprogramming
# Simplex Method: Step-by-Step Example

## Problem Statement

Maximize: Z = 3x + 2y
Subject to:
  x + y ≤ 4
  x ≤ 3
  x, y ≥ 0

## Step 1: Convert to Standard Form

Add slack variables s1 and s2:

Maximize: Z = 3x + 2y + 0s1 + 0s2
Subject to:
  x + y + s1 = 4
  x + s2 = 3
  x, y, s1, s2 ≥ 0

## Step 2: Create Initial Tableau

| Basic | x | y | s1 | s2 | RHS |
|-------|---|---|----|----|----|
| Z     |-3 |-2 | 0  | 0  | 0  |
| s1    | 1 | 1 | 1  | 0  | 4  |
| s2    | 1 | 0 | 0  | 1  | 3  |

## Step 3: Identify Entering and Leaving Variables

Entering variable: x (most negative in Z row)
Leaving variable: s2 (smallest ratio: 3/1 = 3)

## Step 4: Pivot

Divide the s2 row by the pivot element (1):

| Basic | x | y | s1 | s2 | RHS |
|-------|---|---|----|----|----|
| Z     |-3 |-2 | 0  | 0  | 0  |
| s1    | 1 | 1 | 1  | 0  | 4  |
| x     | 1 | 0 | 0  | 1  | 3  |

Update other rows:
Z row: Add 3 times the x row
s1 row: Subtract 1 times the x row

## Step 5: New Tableau

| Basic | x | y | s1 | s2 | RHS |
|-------|---|---|----|----|----|
| Z     | 0 |-2 | 0  | 3  | 9  |
| s1    | 0 | 1 | 1  |-1  | 1  |
| x     | 1 | 0 | 0  | 1  | 3  |

## Step 6: Repeat Steps 3-5

Entering variable: y
Leaving variable: s1

Pivot and update:

| Basic | x   | y   | s1  | s2  | RHS |
| ----- | --- | --- | --- | --- | --- |
| Z     | 0   | 0   | 2   | 1   | 11  |
| y     | 0   | 1   | 1   | -1  | 1   |
| x     | 1   | 0   | 0   | 1   | 3   |

## Step 7: Check for Optimality

All coefficients in the Z row are non-negative, so we've reached the optimal solution.

## Final Solution

x = 3
y = 1
Maximum Z = 11