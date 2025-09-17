# Formatting-and-analysing-the-sales-data-in-PostgreSQL

Hi there! This project showcases my SQL skills through a hands-on data analysis and cleaning task using PostgreSQL. Working with a simulated Super Store dataset, I applied advanced SQL techniques to uncover insights, identify top product categories based on profit margins, and intelligently handle missing data. It was a great opportunity to challenge and enhance my understanding of SQL concepts in a practical setting.

## Data Dictionary:

### `orders`:
| Column | Definition | Data type | Comments |
|--------|------------|-----------|----------|
| `row_id`| Unique Record ID | `INTEGER` |
| `order_id` | Identifier for each order in table | `TEXT` | Connects to `order_id` in `returned_orders` table |
| `order_date` | Date when order was placed | `TEXT` |
| `market` | Market order_id belongs to | `TEXT` |
| `region` | Region Customer belongs to | `TEXT` | Connects to `region` in `people` table |
| `product_id` | Identifier of Product bought | `TEXT` | Connects to `product_id` in `products` table |
| `sales` | Total Sales Amount for the Line Item | `DOUBLE PRECISION` |
| `quantity` | Total Quantity for the Line Item | `DOUBLE PRECISION` |
| `discount` | Discount applied for the Line Item | `DOUBLE PRECISION` |
| `profit` | Total Profit earned on the Line Item | `DOUBLE PRECISION` |

### `returned_orders`:
| Column | Definition | Data type |
|--------|------------|-----------|
| `returned`| Yes values for Order / Line Item Returned | `TEXT` |
| `order_id` | Identifier for each order in table | `TEXT` |
| `market` | Market order_id belongs to | `TEXT` |

### `people`:
| Column | Definition | Data type |
|--------|------------|-----------|
| `person`| Name of Salesperson credited with Order | `TEXT` |
| `region` | Region Salesperson in operating in | `TEXT` |

### `products`:
| Column | Definition | Data type |
|--------|------------|-----------|
| `product_id`| Unique Identifier for the Product | `TEXT` |
| `category` | Category Product belongs to | `TEXT` |
| `sub_category` | Sub Category Product belongs to | `TEXT` |
| `product_name` | Detailed Name of the Product | `TEXT` |

In the Data Dictionary above, date fields have been written to the `orders` table as `TEXT` and numeric fields like sales, profit, etc. have been written to the `orders` table as `Double Precision`. we will need to take care of these types in some of the queries. This project is an excellent opportunity to apply our SQL skills in a practical setting and gain valuable experience in data cleaning and analysis. 





## 🔍 What I Did

### 1. Ranked Top Products by Category
- I wrote a query to find the **top 5 products** in each category based on **total sales**.
- Results are sorted by:
  - Category (ascending)
  - Sales (descending within each category)
- Final output includes:
  - `category`
  - `product_name`
  - `product_total_sales` (rounded to 2 decimals)
  - `product_total_profit` (rounded to 2 decimals)
  - `product_rank`

### 2. Imputed Missing Quantity Values
- Some orders had missing `quantity` values, so I calculated unit prices using available data.
- I factored in:
  - `discount`
  - `market`
  - `region`
- Then I estimated the missing quantities and added a new column:
  - `calculated_quantity` (rounded to whole numbers)

## 🧠 Skills I Applied

- SQL subqueries and joins
- Data cleaning and transformation
- Aggregation and ranking
- Conditional logic
- PostgreSQL formatting functions

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/postgresql-sales-analysis.git
   cd postgresql-sales-analysis

