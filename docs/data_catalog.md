# Gold Layer Data Catalog

The **Gold Layer** represents business-ready data structured for analytics and reporting. It contains **dimension tables** and **fact tables** for key business metrics.

### 1. **gold.dim_customers**
**Purpose:** Stores customer details, enriched with demographic and geographic information.

| Column Name      | Data Type     | Description                                                                 |
|-----------------|---------------|-----------------------------------------------------------------------------|
| customer_key     | INT           | Surrogate key uniquely identifying each customer.                           |
| customer_id      | INT           | Unique numeric identifier for the customer.                                 |
| customer_number  | NVARCHAR(50)  | Alphanumeric code representing the customer, used for tracking and reference. |
| first_name       | NVARCHAR(50)  | Customer's first name.                                                      |
| last_name        | NVARCHAR(50)  | Customer's last name or family name.                                        |
| country          | NVARCHAR(50)  | Country of residence (e.g., 'Australia').                                   |
| marital_status   | NVARCHAR(50)  | Marital status (e.g., 'Married', 'Single').                                 |
| gender           | NVARCHAR(50)  | Gender (e.g., 'Male', 'Female', 'n/a').                                     |
| birthdate        | DATE          | Birth date formatted as YYYY-MM-DD (e.g., 1971-10-06).                      |
| create_date      | DATE          | Date when the customer record was created in the system.                    |

---

### 2. **gold.dim_products**
**Purpose:** Contains product details and attributes.

| Column Name         | Data Type     | Description                                                                 |
|--------------------|---------------|-----------------------------------------------------------------------------|
| product_key         | INT           | Surrogate key uniquely identifying each product.                             |
| product_id          | INT           | Unique identifier assigned to the product.                                   |
| product_number      | NVARCHAR(50)  | Structured code representing the product for categorization or inventory.    |
| product_name        | NVARCHAR(50)  | Descriptive product name including type, color, and size.                    |
| category_id         | NVARCHAR(50)  | Identifier linking the product to its high-level category.                   |
| category            | NVARCHAR(50)  | Broad classification (e.g., Bikes, Components).                              |
| subcategory         | NVARCHAR(50)  | Detailed classification within the category.                                 |
| maintenance_required| NVARCHAR(50)  | Indicates if maintenance is required (Yes/No).                                |
| cost                | INT           | Base price of the product in monetary units.                                  |
| product_line        | NVARCHAR(50)  | Specific product line or series (e.g., Road, Mountain).                       |
| start_date          | DATE          | Date when the product became available for sale.                               |

---

### 3. **gold.fact_sales**
**Purpose:** Stores transactional sales data for analytics.

| Column Name     | Data Type     | Description                                                                 |
|-----------------|---------------|-----------------------------------------------------------------------------|
| order_number    | NVARCHAR(50)  | Unique identifier for each sales order (e.g., 'SO54496').                   |
| product_key     | INT           | Surrogate key linking to the product dimension.                              |
| customer_key    | INT           | Surrogate key linking to the customer dimension.                             |
| order_date      | DATE          | Date when the order was placed.                                             |
| shipping_date   | DATE          | Date when the order was shipped.                                            |
| due_date        | DATE          | Date when the order payment is due.                                         |
| sales_amount    | INT           | Total value of the sale for the line item (whole currency units).           |
| quantity        | INT           | Number of product units ordered for the line item.                           |
| price           | INT           | Unit price for the product in the line item (whole currency units).         |