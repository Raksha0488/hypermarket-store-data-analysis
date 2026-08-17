# Hypermarket Store Data Analysis 🛍️📊

Excel-based data analytics project done as part of my self-learning / portfolio building during
M.Tech (2nd year). The project takes raw retail sales data from a fashion/apparel store, cleans
it, and builds an interactive dashboard to answer common business questions like *which category
sells the most*, *which state generates the most revenue*, *who spends more — men or women*, etc.

> Note: The dataset is originally called "Vrinda Store" (an Indian D2C clothing brand) sales data,
> but I have referred to the overall project as **Hypermarket Store Data Analysis** since the
> workflow (raw data → cleaning → pivot tables → dashboard) is the same one used for general
> retail/hypermarket sales analysis.

---

## 🎯 Objective

To practice the complete data analysis workflow on a real-world-style retail dataset:

1. Import raw, messy sales data
2. Clean and structure it properly (handle missing values, fix data types, add helper columns)
3. Summarize it using PivotTables
4. Build a single-page interactive dashboard for quick business insights

This was mainly done to get hands-on practice with **Excel as a BI tool** (PivotTables,
PivotCharts, slicers, dashboard design) before moving to tools like Power BI / Tableau.

---

## 🗂️ Repository Structure

```
Hypermarket-Store-Data-Analysis/
│
├── README.md                          -> you are here
├── PROJECT_NOTES.md                   -> my personal working notes while doing this project
│
├── data/
│   ├── raw_sales_data.csv             -> raw exported data (before cleaning)
│   └── cleaned_sales_data.csv         -> cleaned data with helper columns (Age Type, Month)
│
├── docs/
│   └── data_dictionary.md             -> column-wise description of the dataset
│
└── dashboard/
    └── Hypermarket_Store_Data_Analysis.xlsx   -> main Excel file (raw data + cleaning + pivots + dashboard)
```

---

## 🧾 About the Dataset

- ~31,000 order-level records of a fashion/apparel store for the year 2022
- Each row = one order line item (product ordered, quantity, amount, customer & shipping info)
- Columns include: Order ID, Customer ID, Gender, Age, Date, Order Status, Sales Channel, SKU,
  Category, Size, Quantity, Amount, Shipping City/State, Country, B2B flag
- Full column-level description is in [`docs/data_dictionary.md`](docs/data_dictionary.md)

---

## 🧹 What I Did (Workflow)

1. **Raw Data Sheet** – Imported the original data as-is (`Vrinda Store Raw Data` sheet).
2. **Data Cleaning Sheet**
   - Checked for duplicate / blank rows
   - Standardized text fields (state names, category names)
   - Converted `Date` column to a proper date format
   - Added two helper columns:
     - `Month` — extracted from Date, used for monthly trend analysis
     - `Age Type` — bucketed customer age into `Teenager`, `Adult`, `Senior`
3. **PivotTables** – Built separate pivot sheets for:
   - Monthly Sales Trend (`Sheet1`)
   - Men vs Women Sales (`Men vs Women`)
   - Order Status Split — Delivered / Cancelled / Returned / Refunded (`Order Status`)
   - State-wise Sales (`Sheet5`)
   - Age Group vs Gender distribution (`AGE N GENDER`)
   - Sales Channel-wise contribution — Amazon, Flipkart, Myntra, Ajio, Meesho, Nalli, Others (`Channels`)
4. **Dashboard Sheet** – Combined all the above pivots into charts and placed them on a single
   "Supermarket Store Annual Report 2022" dashboard page for easy viewing, with slicers for
   filtering.

---

## 📌 Key Insights (from the dashboard)

- Women customers contribute a significantly higher share of total revenue than men
  (~64% vs ~36%).
- **Amazon** and **Myntra** are the top-performing sales channels, together bringing in more
  than half of the total orders.
- **Maharashtra, Karnataka and Uttar Pradesh** are the top 3 revenue-generating states.
- `Set` and `Kurta` are the best-selling product categories by a large margin.
- Delivered orders make up the majority of orders; cancelled, returned and refunded orders
  together are a relatively small chunk, but still worth tracking for operations.
- Adult customers (the middle age bucket) place the most orders across both genders.

*(These numbers are read directly off the pivot tables in the workbook — see the `dashboard`
sheet for the full visual version.)*

---

## 🛠️ Tools Used

- Microsoft Excel (PivotTables, PivotCharts, Slicers, conditional formatting, dashboard design)
- Basic data cleaning techniques (no external tool/script used — everything is native Excel)

---

## ▶️ How to View

1. Download `dashboard/Hypermarket_Store_Data_Analysis.xlsx`
2. Open it in Excel (Excel 2016 or later recommended for full PivotChart/slicer support)
3. Go to the `Dashboard` sheet to see the final report
4. Raw and cleaned data are available in their respective sheets if you want to see the process

A short video walkthrough of the project is also linked inside the workbook
(`Project Video Link` sheet).

---

## 🚧 Future Scope

- [ ] Recreate the same dashboard in Power BI for more advanced interactivity (DAX measures)
- [ ] Automate the cleaning steps using Python (pandas) instead of manual Excel cleaning
- [ ] Add a proper RFM / customer segmentation analysis
- [ ] Add return/refund reason analysis if such data becomes available

---

## 🙋 About Me

M.Tech (2nd Year) student, learning data analytics alongside my coursework. This is one of my
early hands-on projects to understand how raw business data is turned into insights that
non-technical people (like store managers) can actually use.

Feedback and suggestions are welcome — feel free to open an issue or PR!
