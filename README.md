#UiPath Invoice Processing Bot
This project demonstrates an end-to-end RPA automation for invoice processing using UiPath Studio. The bot automatically reads PDF invoices, extracts key information, and logs it into an Excel sheet, mimicking a real-world business process.

#Key Features
-Extracts invoice details: Invoice Number, Date, Vendor Name, Total Amount
-Writes structured data to an Excel file
-Handles multiple invoices from a folder
-Implements error handling and logging for reliability

#Folder Structure
Invoice-Processing-Bot/
│
├─ Main.xaml                  # Main workflow
├─ Invoice_Report.xlsx        # Sample Excel output
├─ Invoices_To_Process/       # Folder containing sample PDF invoices
├─ Processed_Invoices/        # Folder where processed PDFs are moved
├─ README.md                  # Project description
└─ project.json               # UiPath project file

#How It Works
##Bot Trigger
-Monitors the Invoices_To_Process folder for new PDF files.
-Can be extended to trigger from email attachments.
##PDF Data Extraction
-Reads each invoice using Read PDF Text activity.
-Extracts fields using Regex patterns:
-Invoice Number
-Invoice Date
-Vendor Name
-Total Amount
-**Error Handling:** PDFs that cannot be read are logged; the bot continues processing remaining files.
##Excel Automation
-Opens Invoice_Report.xlsx using Excel Application Scope.
-Adds each invoice as a new row in the Excel table.
-**Error Handling:** If Excel is locked or missing, errors are logged, and the bot continues.
##File Management
-Moves processed PDFs to Processed_Invoices folder.
-**Error Handling:** Handles missing folders or file conflicts without stopping the bot.
##Loop Handling
-For Each File loop ensures that even if one invoice fails, others are still processed.
##Logging
-Key actions and exceptions are logged using Log Message activities for easy debugging.

#Sample Data
-Invoice_Report.xlsx contains dummy invoice data for testing.
-Sample PDFs in Invoices_To_Process/ are mock invoices with no sensitive information.

#How to Use
1.Clone or download the repository.
2.Open the project in UiPath Studio.
3.Update folder paths in Main.xaml if needed.
4.Run the bot to process sample PDFs.
5.Check Invoice_Report.xlsx for extracted data.

#Tech Stack
-UiPath Studio
-UiPath.Excel.Activities
-UiPath.PDF.Activities
-Regex for data extraction
-Excel for output

#Optional Enhancements
-Connect to UiPath Orchestrator for scheduling and queue management.
-Build the project using REFramework for production-level standards.
-Add a simple UI form to start/stop the bot or display logs.
