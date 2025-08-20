# 🚀 RPA for Automated Reimbursement Validation

## 🎯 About The Project

This project is a Robotic Process Automation (RPA) bot developed in Python to streamline and validate expense reimbursement requests automatically. The script reads "pending" requests from a Google Sheet, uses Optical Character Recognition (OCR) to extract the total amount from receipt images, and compares the values to approve or reject the request, updating the status directly on the spreadsheet.

The main goal is to eliminate manual verification, reduce human error, and dramatically accelerate the reimbursement approval cycle.

---

## 🛠️ Tech Stack

* **Python 3**
* **Tesseract (via `pytesseract`)**: For extracting text from receipt images (OCR).
* **Google Sheets API (via `gspread`)**: To read and write data on the control spreadsheet.
* **Pandas**: For efficient data handling and manipulation.
* **Pillow (PIL)**: For image preprocessing before the OCR stage.
* **Requests**: To download receipt images from URLs.
* **Regex (Python's `re` module)**: For precisely parsing monetary values from the raw OCR text.

---

## ✨ Key Features

* **Secure Google Sheets Integration**: Authenticates using service account credentials to access and modify the spreadsheet.
* **Intelligent Data Filtering**: Loads only requests with a "pending" status, optimizing the process.
* **Image Data Extraction (OCR)**: Downloads receipts (JPG, PNG) from Google Drive links and uses Tesseract to "read" the text within them.
* **Regex-Powered Validation**: Accurately finds and extracts monetary values (e.g., $123.45) from the raw text output.
* **Automated Approval Logic**: Compropares the requested amount in the spreadsheet with the value extracted from the receipt.
* **Real-Time Status Updates**: Updates the status in the spreadsheet to "Approved Automatically," "Rejected - Mismatch," or "Manual Review" in case of errors, providing instant feedback.
* **Robust Error Handling**: Gracefully handles broken image links, unreadable receipts, or missing values by flagging them for human review without crashing the entire process.

---

## 🏁 Getting Started

### **Prerequisites:**

1.  **Python 3.x** installed.
2.  **Tesseract-OCR** installed on your system.
    * *Windows:* Download the installer from the [official UB-Mannheim fork](https://github.com/UB-Mannheim/tesseract/wiki) and ensure its installation path is added to your system's PATH.
    * *Linux/Mac:* Use your package manager (`sudo apt-get install tesseract-ocr`, `brew install tesseract`).
3.  A **Google Sheet** with the following columns: `id_reembolso`, `valor_solicitado`, `link_comprovante`, and `status`.
4.  **Google Cloud API Credentials**. Follow the [gspread guide](https://docs.gspread.org/en/latest/oauth2.html) to create a `credentials.json` file, enabling the Google Sheets and Google Drive APIs. Share your spreadsheet with the `client_email` found in your `credentials.json`.

### **Installation:**

```bash
# Clone this repository
$ git clone [https://github.com/bruno272025/-Automated-Expense-Reimbursement-Bot-RPA-OCR-.git)

# Navigate to the project directory
$ cd -Automated-Expense-Reimbursement-Bot-RPA-OCR-

# Install the dependencies
pip install -r requirements.txt

# Place your 'credentials.json' file in the root of the project.
