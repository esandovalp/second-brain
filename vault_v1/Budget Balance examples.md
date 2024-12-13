#marketdesign
# VCG Mechanism with Budget Balance: Single-Item Auction

Consider a single-item auction with three bidders: A, B, and C. Their valuations are as follows:

- Bidder A: $10
- Bidder B: $15
- Bidder C: $20

## VCG Payments Calculation

1. The item is allocated to Bidder C (highest bid).
2. Calculate the social welfare loss for each bidder if they were removed:
   - Without A: No change, loss = $0
   - Without B: No change, loss = $0
   - Without C: Item goes to B, loss = $20 - $15 = $5

3. VCG payments:
   - Bidder A pays: $0
   - Bidder B pays: $0
   - Bidder C pays: $5

## Budget Balance Check

Total payments received: $0 + $0 + $5 = $5
Amount to be paid to the seller: $5

In this case, the total amount paid by the bidders equals the amount to be paid to the seller, achieving budget balance.

# VCG Mechanism with Budget Balance: Two Bidders, Single Item

Consider a single item auction with two bidders: 1 and 2.

Bidder 1's possible values: {1, 3}
Bidder 2's possible values: {2, 4}

Let h₁(v₂) and h₂(v₁) be the VCG payment functions for bidders 1 and 2 respectively, where v₁ and v₂ are their reported values.

For budget balance, we need the sum of payments to equal zero in all cases:

1. If (v₁, v₂) = (1, 2): h₁(2) + 1 + h₂(1) = 0
2. If (v₁, v₂) = (3, 4): h₁(4) + 3 + h₂(3) = 0
3. If (v₁, v₂) = (1, 4): h₁(4) + h₂(1) = 0
4. If (v₁, v₂) = (3, 2): 2 + h₁(2) + h₂(3) = 0

Solving this system of equations:

h₁(2) = -2
h₁(4) = -3
h₂(1) = -1
h₂(3) = -2

These values satisfy all equations, achieving budget balance in all cases.

## Verification

1. (1, 2): -2 + 1 + (-1) = -2 + 0 = 0
2. (3, 4): -3 + 3 + (-2) = -2 + 2 = 0
3. (1, 4): -3 + (-1) = -4 + 4 = 0
4. (3, 2): 2 + (-2) + (-2) = 0 + 0 = 0

Budget balance is achieved in all cases.