# Week 7: Depreciation 

**Depreciation:** Continual loss of value.
- diminish in *recorded* value over time

##### Why do assets lose value
1. assets deteriorate
	- use related physical loss
	- time related physical loss
2. assets become obsolete
	- functionally related loss

The study of depreciation asks **what curve do we use to connect the book and salvage value of an item?**

**Depreciation IS NOT A CASH FLOW**, it is an accounting fiction

##### Why does depreciation matter

- internal bookeeping and financial planning
- financial reporting
	- for investors 
	- for valuation
- assets can be used as collateral for loans 
- tax implications 

##### What do we mean by value
- **cost basis**: value against which depreciatio is measured 
- **market value**: how much could we sell it for?
- **book value**: calculated for accounting purposes via an agreed upon method

##### Key symbols

$B$: Basis value
$BV_t$: book value at time $t$. ie. $BV_0 = B$.
$N$: depreciable life of asset (not nessecarily useful life)
$S$: salvage value
$D_t$: loss of value assigned to an accounting period $t$

Core relationships: 
$$BV_t = BV_{t-1} - D_t$$
$$BV_t = BV_0 - \sum_{k=1}^t D_k = B - \sum_{k=0}^t D_k $$

#### Methods of Depreciation 
For tax purposes, the government will specify the method of depreciation. **We only consider the market value at the beginning and end of depreciation, never in the middle.**
##### Straight Line
$$D_t = \frac{B-S}{N}$$
$$BV_t = B - t\left(\frac{B-S}{N}\right)$$

##### Declining Balance
loss of value is modelled as a constant proportion of book value $d$:

$$D_t = dBV_{t-1}$$
$$BV_t = BV_{t-1}(1-d)$$
$$BV_t = B(1-d)^t$$

##### Double Declining Balance

Declining balance using $d = \frac{2}{N}$

##### Sum of Years Digits 

$$ SOYD = \sum_{k=1}^{N}k = \frac{N+1}{2}N$$
$$D_t = \frac{N-t+1}{SOYD}(B-S)$$

This is faster in earlier years and slower in later years than [[#Straight Line]] depreciation

##### Units of Production

$$D_t = \frac{\text{production in year t}}{\text{lifetime production}}(B-S)$$

##### Depreciation at end of life
Let $MV$ be the market value on sale. 

If $MV < BV_N$:
$$ \text{loss on disposal} = BV_N - MV$$
If $BV_N < M < B$:
$$ \text{recapture depreciation} = M - BV_N$$
If $MV > B$:
$$ \text{recapture depreciation} = B-BV_N$$
$$ \text{captial gain} = M - B$$

##### If Service Life Changes Mid-depreciation

Use $BV_t$ as new basis, and remaining useful life as $N$. Re-evaluate with chosen depreciation method. 