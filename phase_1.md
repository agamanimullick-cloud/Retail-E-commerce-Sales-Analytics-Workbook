## Phase 1: Data Import and Power Query Setup

The project uses the Online Retail II dataset, containing over 1 million transaction-level records from a UK-based online retailer.

Because the dataset exceeds Excel's worksheet row limit, the raw CSV was imported using Power Query rather than loaded directly into a worksheet.

### Steps completed

- Imported `online_retail_II.csv` using Power Query
- Promoted the first row to column headers
- Reviewed and corrected column data types
- Converted `Customer ID` to text because it is an identifier rather than a numeric measure
- Cleaned the `Customer ID` field by removing the unnecessary `.0` suffix from values such as `13085.0`
- Retained the raw dataset within Power Query for transformation rather than attempting to load all rows into the Excel grid

### Why Power Query was used

Power Query provides a repeatable and structured way to clean and transform large datasets. Each transformation is stored as an applied step, meaning the cleaning process can be reproduced automatically whenever the source data is refreshed.

The dataset contains more rows than a standard Excel worksheet can display, so Power Query also provides a practical way to work with the full dataset before producing smaller analysis tables.
