# Power BI Automation: Load All CSV Files at Once Using Python

This project automates the process of combining multiple CSV files into a single Excel workbook, which can then be easily loaded into Power BI for efficient data analysis and visualization.

## ❌ The Old Method (Manual)

Traditionally, users needed to:
- Upload an entire folder into Power BI
- Extract and load each CSV file one by one
- Create multiple tables for each file
- Waste time on repetitive import steps

This manual process is time-consuming and inefficient, especially when dealing with large numbers of CSVs.

## ✅ The New Method (Automated with Python)

This automation:
- Combines all CSV files in a folder into a **single Excel workbook**
- Saves time by automating data prep using **Python**
- Allows you to directly import one Excel file into Power BI
- Simplifies data modeling and visualization

## 🛠️ Tech Stack

- 🐍 Python (3.x)
- 📁 VS Code (or any IDE)
- 📊 Power BI Desktop
- 📦 Libraries: `pandas`, `openpyxl` or `xlsxwriter`

---

## 🔁 Process Workflow

1. 📂 Place all your `.csv` files into the `input/` folder.
2. 🐍 Run the Python script to:
   - Read all CSVs
   - Merge them into one Excel file (`output/data.xlsx`)
3. 📈 Open Power BI and load the `data.xlsx` file
4. 🎨 Create your dashboard and visualizations


## 📄 Python Script Summary

import os
import pandas as pd

# 📂 Folder containing your CSV files
input_folder = r"D:\SQL\Project\CSV_Files"  # 🖊️ Change to your folder path

# 📁 Output Excel workbook file
output_file = r"D:\SQL\Project\Excel_Workbook\AllCSVs_In_One_Workbook.xlsx"  # 🖊️ Change path and filename

# 🧾 Create Excel writer
with pd.ExcelWriter(output_file, engine='xlsxwriter') as writer:
    for filename in os.listdir(input_folder):
        if filename.lower().endswith(".csv"):
            file_path = os.path.join(input_folder, filename)
            sheet_name = os.path.splitext(filename)[0][:31]  # Excel sheet names max 31 chars
         try:
                df = pd.read_csv(file_path)
                df.to_excel(writer, sheet_name=sheet_name, index=False)
                print(f"✅ Added sheet: {sheet_name}")
            except Exception as e:
                print(f"❌ Error processing {filename}: {e}")

print("\n All CSVs have been combined into one Excel file!")


[ # - that line are comment(will not run) means this is only for understanding not for the code] 

> 💡 Don’t know Python? No problem — use ChatGPT to generate the script, paste it into VS Code, and run it!

Author

name- Akash Maurya
Email- mauryaakash681@gmail.com
linkedin- https://www.linkedin.com/in/akashrkrmaurya/




