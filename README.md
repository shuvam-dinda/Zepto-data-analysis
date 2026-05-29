# Zepto Data Analysis

**Author:** Shuvam Dinda

## Project Overview

This repository contains a compact data analysis project for Zepto product inventory and pricing data. It includes a source dataset in CSV format and a SQL script designed for PostgreSQL that creates a table, performs basic data cleaning, and explores business-focused insights.

## Files

- `zepto_v2.csv` - dataset with product details such as category, name, MRP, discount percent, quantity, weight, stock status, and sale price.
- `Zepto_SQL_data_analysis.sql` - SQL script with table definition, data exploration queries, cleaning steps, and example analysis questions.

## Dataset Columns

The dataset includes the following columns:

- `category` - product category
- `name` - product name
- `mrp` - maximum retail price (in paise in the raw dataset)
- `discountPercent` - percentage discount applied to the product
- `availableQuantity` - stock quantity available for sale
- `discountedSellingPrice` - price after discount (in paise in the raw dataset)
- `weightInGms` - product weight in grams
- `outOfStock` - whether the product is out of stock
- `quantity` - listed quantity value in the dataset

## Analysis Goals

The SQL script is designed to answer questions such as:

- Top products by discount percentage
- High-MRP products that are out of stock
- Estimated revenue by category
- Products with high MRP and low discount
- Categories with the highest average discount
- Price-per-gram value for heavier products
- Weight-based product segmentation
- Total inventory weight by category

## Getting Started

### Option 1: Run with PostgreSQL

1. Create or use an existing PostgreSQL database.
2. Load the CSV into the `zepto` table after creating it with the SQL script.

Example:

```bash
createdb zepto_analysis
psql -d zepto_analysis -f Zepto_SQL_data_analysis.sql
```

3. Import the CSV into PostgreSQL:

```sql
\copy zepto(category, name, mrp, discountPercent, availableQuantity, discountedSellingPrice, weightInGms, outOfStock, quantity)
FROM 'zepto_v2.csv'
WITH CSV HEADER;
```

4. Run the queries in `Zepto_SQL_data_analysis.sql` to explore the dataset.

### Option 2: Explore with Python / pandas

If you prefer Python, the dataset can be loaded into pandas for analysis:

```python
import pandas as pd

df = pd.read_csv('zepto_v2.csv')
print(df.head())
```

## Notes

- The SQL script includes a conversion from paise to rupees for the price fields.
- The analysis is intentionally simple and easy to extend for additional business questions.

## License

This repository is provided for data exploration and analysis.
