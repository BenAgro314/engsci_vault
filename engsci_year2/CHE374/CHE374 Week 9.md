# Week 9: Taxation

### Corporate Taxes
- corporations pay taxes on their profits 

##### Calculating Cash Flows With Taxes

Cash flow diagram: **first cost**, **revenues - expenses**, **salvage value**.

**Discount cash flows to present with MARR**


##### Calculating Corporate Tax

$$\text{taxable income} = \text{revenue} - \text{expenses}$$

$$\text{corporate tax} = \text{taxable income} \times \text{tax rate}$$

**Paying tax** is a negative cash flow. **Saving taxes** is a positive cash flow. 

##### Revenues

- any income earned by the company
	- sales revenues
	- interest revenues
	- captial gains (when assets is sold)
- **increased revenues mean greater taxes**

##### Expenses and Deducations

- cost of goods sold
- interest expenses
- depreciation of long term assets
- captial losses (assets sale below book value)
- **not allowed**
	- dividends
	- asset purchases (does not appear on income statement, only balance sheet)
	- other
- **increased expenses mean less taxes**

##### Assets Affect On Depreciation

- asset purchase has not immediate affect on corporate taxes
- can affect taxes later
	- claiming depreciation
	- capital gains/loss

##### Effect of Taxes on Rate of Return

- discounting after tax cash flows requires a lower rate because the expected profits decrease as a result of paying taxes

$$\text{MARR(after tax)} \approx \text{MARR(before tax)}\times(1- \text{tax rate})$$

$$\text{IRR(after tax)} \approx \text{IRR(before tax)}\times(1- \text{tax rate})$$

### Capital Cost Allowance

##### Depreciation

- not a real cash flow
- an expense that is on income statement
- claiming depreciation -> tax savings (positive cash flow)
- claiming depreciation earns real money in the form of taxes
- **depreciate as quickly as possible** due to time value of money tax savings 

##### Captial Cost Allowance (CCA)

- canadian system for calculating depreciation and taxes
- Assets are grouped by CCA asset class and each class has a CCA rate (depreciation rate)

|Book Depreciation Term|Tax Depreciation Term/Meaning|
|---|---|
|Depreciation|Capital Cost Allowance (CCA)|
|Book Value|Undepreciated captial cost (UCC)|
|Salvage Value|Proceeds from disposition|

1. pooling: assets are pooled into classes
	- depreciated based on UCC for all assets in that class
	- **Assets are not depreciated individually**
2. Depreciation method used is a slightly modified [[CHE374 Week 7#Declining Balance]] method:

Declining balance:
$$D = d(\text{this year's addition} + \text{BV from last year})$$
CCA:
$$\text{CCA} = (\text{CCA rate})(\frac{\text{this year's addition}}{2} + \text{UCC from last year})$$

This is known as the **half year rule**
Declining balance:
$$BV_t = BV_{t-1}+\text{this years addition} - D$$
UCC:
$$UCC_t = UCC_{t-1} + \text{this years addition}- CCA$$

![[Pasted image 20210307080230.png]]

##### Tax Savings From Depreciation

- no out-of-pocket expense from depreciation
- claiming depreciation saves taxes

$$ \text{tax savings(for year n)} = CCA_n\times\text{tax rate}$$

##### CCA Rules on Disposition

- UCC/BV can be different than the salvage value
- if there are other items in the pool (**open book**):
	- selling asset does not close out the pool
	- the UCC/BV is reduced by the salvage value
- only item in pool (**closed book**):
	- see three cases for end of life [[CHE374 Week 7#Depreciation at end of life]]

|Case|Amount to Remove|Implications of Diposition|
|---|---|---|
|**Open books**| Salvage Value |No Taxes|
|**Closed books**|
|$S<BV$| BV|claim terminal loss $(S-BV)$|
|$BV <S <P$|BV|Report recapture $(S-BV)$|
|$S>P$| BV| Report recapture $(P-BV)$|

### Calculating PW with taxes (Explicit Method)

##### Items affected by taxes

1. MARR: use after tax MARR
2. Annual Revenues (reduced by taxes)
3. First Cost: no direct affect (assuming it is an asset cost)
4. Depreciation: follow CCA depreciation rules
5. Salvage value: follow CCA disposition rules

**just change cash flows based on the above factors and calculate PW as normal**

### Calculating PW with taxes (Tax Benifit Factor $\tau$)

- purchasing an asset provides inherent value and **the value associated with tax benifits**
- what is the present value of all the tax savings for every dollar I spend today on one particular asset

$$ \tau = \frac{PW(\text{tax savings})}{FC}$$

- eg. if $\tau = 0.2$, for every dollar spent -> future tax savings with a total PW of $0.20

- $\tau$ depends on depreciation method, tax rate, time value of money ...

| Depreciation Method | Tax Benefit Factor |
| --- | --- |
| Declining Balance $\tau_{db}$| $\frac{td}{i+d}$ |
| Declining Balance with half year rule $\tau_{1/2}$|$\frac{td}{i+d}(\frac{1+i/2}{1+i})$|

$i$: after tax MARR
$d$: depreciation rate
$t$: tax rate

##### Using Tax Benefit Factor

- if we spend $FC$ on an asset purchase, the **effective first cost** is reduced because of tax savings
	
$$ PW(FC) = -FC +FC\tau_{1/2} = -FC\left(1-\frac{td}{i+d}\left(\frac{1+i/2}{1+i}\right)\right)$$

- if we sell assets worth $S$ and the asset pool is reduced by $R$, the **effective salvage value** is reduced because of losing tax savings

$$PW(S) = (S - R\tau_{db})(P/F, i, N) = \left( S- R\left( \frac{td}{i+d} \right)\right)(P/F, i,N)$$

##### Calculating PW

1. first cost + tax savings from depreciation
	- $PW = -FC(1-\tau_{1/2}) = -FC(\text{CTF})$
	- CTF is called the **capital tax factor**
2. after tax revenues (same as explicit method)
3. disposition
	- check cases: one of many items in pool or only item in pool
	- -> **open books**: 
		1. recieve S for selling asset, lose take benifits of R = S
		2. $PW(S) = S(1-\tau_{db})(P/F, \text{MARR}, N)$
			- $(1-\tau_{db})$ is called the **capital salvage factor (CSF)**
		3. no tax gain/loss
	- -> **closed books**
		1. recieve S
		2. lose tax benifit: decrease in UCC (R) = remaining UCC
			- $-UCC_{N} \times \tau_{db}$
		3. tax or savings on gain or loss
			- use terminal loss or recapture as savings or loss respectively
		4. **discount all of these values back to the present **


