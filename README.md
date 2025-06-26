# Analyze-Species-Differences
An Automated Python-Based Method for Differential KEGG Module Analysis in Novel Species Identification
─────────────────────────────  
User Guide: Extracting KEGG Module Differential Metrics from Excel  
─────────────────────────────

[1. Overview]

The purpose of this program is to extract differential metrics of KEGG modules for target species from an Excel file, sort all modules based on the calculated results, and finally select the top N ranked modules. The program automatically checks the runtime environment, reads data, calculates target metrics (mean and variance), performs standardization, sorts the results, and saves them to a new Excel file.

[2. Environment and Requirements]

2.1 Python Environment  
  - Must use Python 3.x or higher.

2.2 Required Python Libraries  
  - pandas  
  - numpy  
  - openpyxl (for reading/writing Excel files)  
  - scikit-learn (for data standardization)  

Ensure all the above libraries are installed. You can use the pip command to install them (e.g., pip install pandas numpy openpyxl scikit-learn).

[3. Main Functions of the Program]

1. Check Initial Conditions:
   - Verify that the Python version meets the requirements;
   - Check if the required libraries are installed;
   - Ensure the specified Excel file exists;
   - Validate the integrity and format of the data in the Excel file.

2. Data Reading and Processing:
   - Read species names and corresponding KEGG module data from the Excel document;
   - Use the data of the target species as a reference to calculate the differences (mean and variance) for other data rows.

3. Data Analysis and Sorting:
   - Standardize the metrics for each module, aggregate mean and variance to obtain a combined difference value;
   - Sort all modules in descending order based on the combined difference value and select the top N modules.

4. Output Results:
   - Save the selected module data and combined difference ranking results to an Excel file (default saved on the desktop, filename: top_{top_n}_modules_data.xlsx).

[4. Program Configuration Instructions]

In the program, the following parameters need to be adjusted according to the actual situation:

1. file_path  
   - Full path to the Excel file. For example: C:\Users\Username\Desktop\Workbook1.xlsx

2. target_species  
   - List of target species names to filter. For example:  
     ['Aestuariirhabdus_salina_LZHN29T', 'Thalassotalea_salina_PLHSN55T']

3. species_col  
   - Index of the column where species names are located in the Excel data (starting from 0). For example: 0

4. modules_start_col  
   - Index of the starting column for KEGG module data in Excel. If module data starts from the 5th column, enter: 4

5. top_n  
   - Number of top modules to select from the sorted results. For example: 40

6. data_skiprows & header_skiprows  
   - data_skiprows: Number of rows to skip at the beginning of the Excel file, index where data reading starts (e.g., 5th row, value is 4);
   - header_skiprows: Index of the row where module names are located (e.g., 4th row, value is 3).

[5. Steps to Use]

Step 1: Preparation  
  - Ensure Python 3.x and all necessary libraries (pandas, numpy, openpyxl, scikit-learn) are installed on your computer;  
  - Prepare an Excel file containing KEGG module data and species names, and ensure its format requirements:
      · Species names are located in the specified column (e.g., the first column);
      · Module data starts from the specified starting column;
      · The corresponding rows and columns in the Excel file need to match the program parameters.

Step 2: Modify Parameters  
  - Open the program file (e.g., script.py);
  - Modify the parameter section at the top of the file, adjusting file_path, target_species, species_col, modules_start_col, top_n, data_skiprows, and header_skiprows according to your Excel data.

Step 3: Run the Program  
  - Run the program in the command line or terminal:
     · On Windows: Open Command Prompt and type: python script.py
     · On Mac/Linux: In the terminal, type: python3 script.py
  - The program will check initial conditions during execution and output error messages if any issues are found.

Step 4: View Output  
  - After successful execution, the program will output information about each step in the console, including the number of columns read from the Excel file and the top N modules selected;
  - The result file is saved by default on the desktop, with the filename top_{top_n}_modules_data.xlsx, containing two worksheets:
      · "Top Modules Data": Contains only species names and the top N ranked module data;
      · "Combined Differences": Lists the combined difference value ranking results for each module.

[6. Common Issues and Solutions]

Issue 1: Error indicating the Excel file does not exist  
   - Check if file_path is correct, paying attention to the backslash format and file name accuracy.

Issue 2: Target species name does not exist  
   - Check the column where species names are located in the Excel file, ensuring the names listed in target_species exist and are free of spaces or case errors.

Issue 3: Error or exception in reading module data  
   - Ensure module data in Excel starts from the specified starting column, and each column is numeric or convertible to numeric;
   - Check for special characters or missing values in the Excel file and ensure the na_values parameter in the program matches the actual situation.

[7. Additional Tips]

- If the data volume is large, it is recommended to test the program on a smaller dataset first;
- Modify the standardization method or metric calculation method in the program as needed to suit specific data characteristics;
- The code includes detailed comments to facilitate future maintenance and upgrades.

─────────────────────────────  
This detailed user guide aims to help you successfully run and understand the program. If you have any other questions, please refer to the comments or contact the relevant developers.  
─────────────────────────────
