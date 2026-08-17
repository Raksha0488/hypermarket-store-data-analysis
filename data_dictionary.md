# Data Dictionary

Column-wise description of `data/raw_sales_data.csv` and `data/cleaned_sales_data.csv`.
The cleaned file has two extra columns (`Month`, `Age Type`) added during the cleaning step.

| Column            | Type        | Description                                                                 |
|--------------------|-------------|-------------------------------------------------------------------------------|
| Index              | Integer     | Row serial number                                                             |
| Order ID           | Text        | Unique order identifier                                                       |
| Cust ID            | Integer     | Unique customer identifier                                                    |
| Gender             | Text        | Customer gender — `Men` / `Women`                                             |
| Age                | Integer     | Customer age (years)                                                          |
| Age Type*          | Text        | Age bucket — `Teenager` / `Adult` / `Senior` (added during cleaning)          |
| Date               | Date        | Order date (2022)                                                             |
| Month*             | Text        | Month name extracted from Date, e.g. `Jan`, `Feb` (added during cleaning)     |
| Status              | Text        | Order status — `Delivered`, `Cancelled`, `Returned`, `Refunded`               |
| Channel            | Text        | Sales channel — `Amazon`, `Flipkart`, `Myntra`, `Ajio`, `Meesho`, `Nalli`, `Others` |
| SKU                | Text        | Stock keeping unit / product code                                             |
| Category            | Text        | Product category — `kurta`, `Set`, `Western Dress`, `Top`, `Saree`, etc.      |
| Size                | Text        | Product size (S, M, L, XL, XXL, etc.)                                         |
| Qty                 | Integer     | Quantity ordered                                                              |
| currency            | Text        | Currency code (`INR`)                                                         |
| Amount              | Numeric     | Order amount in INR                                                           |
| ship-city           | Text        | Shipping city                                                                 |
| ship-state          | Text        | Shipping state                                                                |
| ship-postal-code    | Numeric     | Shipping postal / PIN code                                                    |
| ship-country        | Text        | Shipping country code (`IN`)                                                  |
| B2B                 | Boolean     | Whether the order is a business-to-business order                             |

`*` = column added during the cleaning step, not present in the raw data.
