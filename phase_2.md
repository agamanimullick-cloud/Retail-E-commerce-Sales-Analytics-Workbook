## Phase 2: Data Quality Assessment

Before cleaning the dataset, I reviewed the raw transactions to understand the different data-quality issues and distinguish genuine business events from errors or administrative adjustments.

### 1. Missing Customer IDs

Some transactions contain blank `Customer ID` values.

These records were not removed immediately because a missing customer identifier does not necessarily mean the underlying transaction is invalid.

### 2. Cancelled and Returned Transactions

Invoices beginning with `C` were identified as cancelled or returned transactions.

These records generally contain negative quantities and represent reversals of previous sales.

Rather than deleting these transactions, they will be retained so that return value and net revenue can be analysed separately.

### 3. Negative Quantities

The dataset also contains negative quantities where the invoice does not begin with `C`.

Examples included descriptions such as:

- `lost`
- `damages`
- `short`

This suggests that some negative-quantity records represent inventory adjustments rather than customer returns.

This means negative quantity alone should not be used to classify a transaction as a return.

### 4. Zero-Price Transactions

Transactions with `Price = 0` were reviewed separately.

Many appeared to be operational or inventory adjustments, including records relating to lost or damaged stock.

These transactions will not contribute to sales revenue, but they may still contain useful operational information.

### 5. Negative Prices

Only a small number of negative-price transactions were found.

These records had the description:

`Adjust bad debt`

They are accounting adjustments rather than product sales and will therefore be excluded from sales revenue calculations.

### Duplicate Transactions

Exact duplicate rows were identified by comparing all transaction fields:

- Invoice
- StockCode
- Description
- Quantity
- InvoiceDate
- Price
- Customer ID
- Country

Duplicate records could cause revenue, units sold, and transaction counts to be overstated.

Because the dataset does not contain a unique line-item identifier, exact matches across all fields will be treated as duplicate records during the cleaning stage.

---

## Key Findings from the Initial Data Review

The raw dataset contains several distinct transaction types rather than a simple set of sales records:

- Standard customer sales
- Customer returns and cancellations
- Inventory adjustments
- Bad-debt accounting adjustments
- Transactions with missing customer information
- Exact duplicate records

These findings will determine the cleaning rules used in the next phase rather than applying broad filters such as removing every negative quantity or every transaction with missing data.
