📊 Bangladesh Generic Medicine Market Analysis — Power BI Project
📌 Project Overview

This project analyzes the Bangladesh Generic Medicine Market using Power BI.
It covers:

Market structure across Medicines, Generics, Drug Classes, Dosage Forms, Manufacturers & Indications

Price extraction from messy text fields

Market competitiveness

Key insights for anti-malarial, insulin, paracetamol IV, and anti-hypertensive medicines

Business recommendations for new entrants

The goal was to build an end-to-end analytical dashboard using cleaning, modeling, DAX, and visualization.

📁 Dataset Summary

You worked with 6 interconnected tables:

1. Medicines

Brand Name

Generic Name

Manufacturer Name

Dosage Form

Package Container

Dosage Size

Price Extracted

2. Generics

Generic ID

Generic Name

Drug Class

Indication

3. Drug Class

Drug Class ID

Drug Class Name

Generic Count

4. Dosage Form

Dosage Form ID

Dosage Form Name

Brand Count

5. Indication

Indication ID

Indication Name

Generic Count

6. Manufacturers

Manufacturer ID

Manufacturer Name

Generic Count

Brand Count

🔧 Data Cleaning & Transformation (Power Query)
✔️ Extracted Price from “Package Container”

Split column by delimiter

Used Text.Split and Value.FromText logic

Standardized formats

Converted currency strings → numeric values

✔️ Cleaned Dosage Size

Extracted numbers (mg/ml/unit)

Separated quantity + unit

Removed brackets and noise text

✔️ Replaced Missing or Inconsistent Fields

Filled null dosage forms

Standardized manufacturer and generic naming

✔️ Removed Duplicate Brand Records
🧠 Data Modeling (Star Schema)

Final star schema includes:

Fact Table: Medicines

Dimension Tables: Generics, Drug Class, Dosage Form, Manufacturers, Indication

Relationships were created using:

Generic → Generic Name

Manufacturer → Manufacturer Name

Dosage Form → Dosage Form Name

This ensured correct filtering across visuals.

🧮 DAX Measures (Key)
Manufacturer Competitor Count
Manufacturer Count =
CALCULATE(
    DISTINCTCOUNT(Medicines[Manufacturer Name])
)

Competitor Count per Generic
Generic Competitors =
CALCULATE(
    DISTINCTCOUNT(Medicines[Manufacturer Name]),
    ALLEXCEPT(Medicines, Medicines[Generic Name])
)

Average Price Per Generic
Avg Generic Price = AVERAGE(Medicines[Price])

📈 Dashboard Highlights
1️⃣ Total Number of:

Medicine Brands

Generics

Manufacturers

Drug Classes

Dosage Forms

2️⃣ Percentage of Herbal Medicines

Used filtering on Generic Name containing keywords like herbal, herb, etc.

3️⃣ Most Common Dosage Form

Bar chart → Count of brands by dosage form
✔ Tablet emerged as the highest

4️⃣ Generic with Highest Number of Medicines

Sorted bar chart
✔ Paracetamol / other top generic appears at the top

5️⃣ Top Drug Class by Number of Generics

✔ Anti-infective or relevant drug class

6️⃣ Most Competitive Manufacturer

Based on highest number of unique brands

🧪 Specific Problem Statement Answers
✔ Anti-Malarial — Single Competitor?

Filter:

Drug Class contains malaria

Then report generics where:
Generic Competitors = 1

✔ Entry Price Suggestion for Mefloquine

Compare price distribution of same dosage size

Recommend midpoint of competitor prices
✔ Ensures competitive entry

✔ Paracetamol (IV Infusion) Suppliers

Filter:

Generic = Paracetamol

Dosage Form contains “IV Infusion”
Then count Manufacturer Name

✔ Competitors for Insulin Medicines

Filter:

Generic Name contains insulin
Count distinct manufacturers
Count distinct brands

✔ Insulin vs Anti-Hypertensive Competition

Filter generics for:

“Insulin”

“Anti-hypertensive”

Compare:

Manufacturers count

Brand count

🌟 Business Insights (Easy to Read)

✔ Tablet dosage forms dominate → Higher production & adoption
✔ Herbal medicines have small share → Growth potential
✔ Some generics have only one competitor → Ideal for new market entry
✔ Competitive pricing varies by dosage form → Strategy needed per product
✔ Insulin market highly competitive → Many manufacturers
✔ Anti-hypertensives show broader competition → Wider market share



🚀 Final Conclusion

This project demonstrates:

Strong Power BI skills

Real-world data cleaning

Star schema modeling

Deep domain analysis

Effective storytelling through dashboards

This analysis can support market entry strategy, pricing, and competitor landscape understanding for pharmaceutical stakeholders.
