# 📊 Data Analytics Project

A comprehensive data analytics solution built on top of a modern 3-layer data warehouse implementing the Bronze-Silver-Gold (medallion) architecture. This project demonstrates advanced SQL analytics operations, customer segmentation, product analysis, and business intelligence reporting.

## 🏗️ Project Overview

This analytics project extends the [SQL Data Warehouse](https://github.com/wthxrsh/sql-warehouse) by performing sophisticated data analysis operations on customers, products, and sales data. The project implements various analytical patterns and generates actionable business insights through structured SQL queries.

### 🎯 Key Objectives
- Perform comprehensive data exploration and profiling
- Execute advanced analytical operations (ranking, segmentation, time-series analysis)
- Generate business-ready reports for customers and products
- Demonstrate various SQL analytical functions and techniques
- Create reusable analytical templates for business intelligence

## 📁 Project Structure

```
DataAnalyticsProject/
├── datasets/                    # Exported data from all warehouse layers
│   ├── bronze.*.csv            # Raw data exports
│   ├── silver.*.csv            # Cleaned data exports
│   ├── gold.*.csv              # Dimensional model exports
│   ├── gold.report_customers.csv    # Customer analytics report
│   └── gold.report_products.csv     # Product analytics report
├── scripts/                     # SQL analytics scripts
│   ├── 00_init_database.sql           # Database initialization
│   ├── 01_data_exploration.sql        # Database structure exploration
│   ├── 02_dimensions_exploration.sql  # Dimension table analysis
│   ├── 03_date_range_exploration.sql  # Temporal data analysis
│   ├── 04_measures_exploration.sql    # Measures and metrics analysis
│   ├── 05_magnitude_analysis.sql      # Quantitative grouping analysis
│   ├── 06_ranking_analysis.sql        # Performance ranking operations
│   ├── 07_change_over_time_analysis.sql # Time-series analysis
│   ├── 08_cumulative_analysis.sql     # Running totals and cumulative metrics
│   ├── 09_performance_analysis.sql    # Business performance metrics
│   ├── 10_data_segmentation.sql       # Customer and product segmentation
│   ├── 11_part_to_whole_analysis.sql  # Proportional analysis
│   ├── 12_report_customers.sql        # Comprehensive customer report
│   └── 13_report_products.sql         # Comprehensive product report
├── docs/
│   └── PROJECT_ROADMAP.png            # Project visualization
└── README.md
```

## 🔍 Analytics Categories

### 1. **Data Exploration & Profiling**
- **Database Structure Analysis** (`01_data_exploration.sql`)
  - Table and schema discovery
  - Column metadata inspection
  - Data type analysis

- **Dimensional Analysis** (`02_dimensions_exploration.sql`)
  - Customer dimension profiling
  - Product dimension analysis
  - Data quality assessment

- **Temporal Analysis** (`03_date_range_exploration.sql`)
  - Date range validation
  - Temporal data distribution
  - Seasonality patterns

- **Measures Analysis** (`04_measures_exploration.sql`)
  - Fact table metrics exploration
  - Sales performance indicators
  - Quantity and revenue distributions

### 2. **Quantitative Analytics**
- **Magnitude Analysis** (`05_magnitude_analysis.sql`)
  - Customer distribution by geography and demographics
  - Product categorization and pricing analysis
  - Sales volume quantification

- **Ranking Analysis** (`06_ranking_analysis.sql`)
  - Top-performing products by revenue
  - Customer ranking by purchase behavior
  - Advanced window function implementations

- **Performance Analysis** (`09_performance_analysis.sql`)
  - Revenue growth analysis
  - Customer lifetime value calculations
  - Product profitability metrics

### 3. **Time-Series Analytics**
- **Change Over Time Analysis** (`07_change_over_time_analysis.sql`)
  - Monthly and quarterly trend analysis
  - Year-over-year growth calculations
  - Seasonal pattern identification

- **Cumulative Analysis** (`08_cumulative_analysis.sql`)
  - Running totals and moving averages
  - Progressive customer acquisition metrics
  - Cumulative revenue tracking

### 4. **Advanced Segmentation**
- **Data Segmentation** (`10_data_segmentation.sql`)
  - Customer segmentation by behavior and demographics
  - Product categorization by cost ranges
  - Geographic market segmentation

- **Part-to-Whole Analysis** (`11_part_to_whole_analysis.sql`)
  - Market share calculations
  - Revenue contribution analysis
  - Proportional performance metrics

### 5. **Business Intelligence Reports**
- **Customer Analytics Report** (`12_report_customers.sql`)
  - Customer lifecycle metrics (recency, frequency, monetary)
  - Customer segmentation (VIP, Regular, New)
  - Age group analysis and customer lifetime value

- **Product Analytics Report** (`13_report_products.sql`)
  - Product performance segmentation (High, Mid, Low performers)
  - Product lifecycle analysis
  - Category and subcategory insights

## 🚀 Key Features

### Advanced SQL Techniques Demonstrated
- **Window Functions**: RANK(), DENSE_RANK(), ROW_NUMBER(), LAG(), LEAD()
- **Common Table Expressions (CTEs)**: Complex hierarchical queries
- **Conditional Logic**: CASE statements for dynamic segmentation
- **Aggregate Functions**: Advanced GROUP BY operations with statistical functions
- **Date/Time Functions**: Temporal calculations and period comparisons
- **Subqueries and Joins**: Multi-table analytical operations

### Business Intelligence Capabilities
- **Customer Segmentation**: Behavioral and demographic clustering
- **Product Performance Analysis**: Revenue-based categorization
- **Trend Analysis**: Time-series patterns and growth metrics
- **Market Analysis**: Geographic and category-based insights
- **KPI Calculations**: Recency, frequency, monetary value analytics

### Data Export & Integration
- Complete dataset exports from all warehouse layers (Bronze, Silver, Gold)
- Business-ready analytical reports in CSV format
- Structured data for downstream BI tools and visualization platforms

## 📈 Sample Analytics Insights

### Customer Analytics
```sql
-- Customer Segmentation by Purchase Behavior
SELECT 
    customer_segment,
    COUNT(*) AS customer_count,
    AVG(total_sales) AS avg_customer_value,
    AVG(total_orders) AS avg_orders_per_customer
FROM gold.report_customers
GROUP BY customer_segment
ORDER BY avg_customer_value DESC;
```

### Product Performance
```sql
-- Top Product Categories by Revenue
SELECT 
    category,
    subcategory,
    COUNT(*) AS product_count,
    SUM(total_sales) AS category_revenue,
    AVG(avg_order_revenue) AS avg_product_performance
FROM gold.report_products
GROUP BY category, subcategory
ORDER BY category_revenue DESC;
```

### Time-Series Analysis
```sql
-- Monthly Sales Trend Analysis
SELECT 
    year,
    month,
    total_sales,
    LAG(total_sales) OVER (ORDER BY year, month) AS previous_month_sales,
    ROUND(((total_sales - LAG(total_sales) OVER (ORDER BY year, month)) 
           / LAG(total_sales) OVER (ORDER BY year, month)) * 100, 2) AS growth_rate_percent
FROM monthly_sales_summary
ORDER BY year, month;
```

## 🛠️ Technical Requirements

### Prerequisites
- SQL Server (2016 or later)
- SQL Server Management Studio (SSMS) or Azure Data Studio
- Access to the [SQL Data Warehouse](https://github.com/wthxrsh/sql-warehouse) database
- Basic understanding of medallion architecture (Bronze-Silver-Gold layers)

### Data Dependencies
This project requires the following warehouse layers to be populated:
- **Bronze Layer**: Raw CRM and ERP data tables
- **Silver Layer**: Cleansed and standardized data tables
- **Gold Layer**: Dimensional model (dim_customers, dim_products, fact_sales)

## 🚀 Getting Started

### 1. Prerequisites Setup
Ensure you have the base data warehouse from [sql-warehouse](https://github.com/wthxrsh/sql-warehouse) set up and populated with data.

### 2. Clone This Analytics Project
```bash
git clone <this-repository-url>
cd DataAnalyticsProject
```

### 3. Execute Analytics Scripts
Run the scripts in numerical order for the complete analytical journey:

```sql
-- Initialize database connection
:r scripts/00_init_database.sql

-- Execute exploration scripts
:r scripts/01_data_exploration.sql
:r scripts/02_dimensions_exploration.sql
-- ... continue with other scripts

-- Generate final reports
:r scripts/12_report_customers.sql
:r scripts/13_report_products.sql
```

### 4. Export Results
The analytical results can be exported to CSV files for further analysis or visualization in tools like Power BI, Tableau, or Python/R.

## 📊 Business Value & Use Cases

### For Data Analysts
- **Template Library**: Reusable SQL patterns for common analytical operations
- **Best Practices**: Examples of efficient window functions and complex aggregations
- **Performance Optimization**: Structured approach to analytical query development

### For Business Stakeholders
- **Customer Insights**: Understanding customer behavior, segments, and lifetime value
- **Product Strategy**: Data-driven product performance and category analysis
- **Growth Metrics**: Time-series analysis for trend identification and forecasting

### For Data Engineers
- **Analytics Pipeline**: Structured approach to transforming warehouse data into business insights
- **Data Quality**: Examples of analytical data validation and profiling techniques
- **Scalable Architecture**: Modular script organization for maintainable analytics solutions

## 🔧 Customization & Extension

### Adding New Analytics
1. Create new SQL scripts following the naming convention (`##_analysis_name.sql`)
2. Include comprehensive comments explaining the analytical purpose
3. Export results to the `datasets/` folder for downstream consumption

### Modifying Existing Analyses
- Update segmentation logic in `10_data_segmentation.sql`
- Adjust KPI calculations in report scripts
- Customize time periods for trend analysis

### Integration with BI Tools
The exported CSV datasets can be directly imported into:
- **Power BI**: For interactive dashboards and visualizations
- **Tableau**: For advanced data visualization and storytelling
- **Python/R**: For machine learning and statistical analysis
- **Excel**: For ad-hoc analysis and reporting

## 📚 Documentation & Resources

### Related Projects
- **Base Data Warehouse**: [sql-warehouse](https://github.com/wthxrsh/sql-warehouse)
- **Medallion Architecture**: Bronze-Silver-Gold implementation patterns

### Learning Resources
- SQL Window Functions and Advanced Analytics
- Customer Segmentation Techniques (RFM Analysis)
- Time-Series Analysis in SQL
- Data Warehouse Analytics Best Practices

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests for:
- Additional analytical patterns and use cases
- Performance optimizations
- New business intelligence reports
- Documentation improvements

### Contribution Guidelines
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-analysis`)
3. Follow the established naming and commenting conventions
4. Test your analytical scripts thoroughly
5. Update documentation as needed
6. Submit a pull request with detailed description

## 📄 License

This project builds upon the [SQL Data Warehouse](https://github.com/wthxrsh/sql-warehouse) and follows the same licensing terms.

---

**Built with ❤️ for the data analytics community**

*This project demonstrates the power of SQL for advanced analytics and serves as a comprehensive template for building data-driven insights on top of modern data warehouse architectures.*
