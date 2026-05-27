# BAFRS Project Style Guide

This document defines the coding standards, formatting rules, and workflow conventions for the Barangay Automated Financial Reporting System (BAFRS) development team. Every team member must follow these rules strictly to keep the codebase clean, consistent, and maintainable. Graders will verify compliance in the source files.

---

## 1. Naming Conventions

To keep our variables and system entities clearly structured, we use specific case formats based on the item type. Generic labels like "Name things clearly" are insufficient; use the following concrete rules:

### Source Code Variables & Functions (`camelCase`)
All internal variables, arrays, object instances, and standard JavaScript/framework functions must follow standard camelCase.
* **Correct:** `revenueTotal`, `expenseAmount`, `calculateBalance()`, `getReceiptData()`
* **Incorrect:** `RevenueTotal`, `expense_amount`, `calc()`, `get_receipt()`

### Component & Class Layouts (`PascalCase`)
Reusable front-end UI components, specific architectural views, and object-oriented class declarations must start with an uppercase letter and use PascalCase.
* **Correct:** `FinancialDashboard`, `ReceiptUploader`, `RevenueForm`, `DatabaseConnection`
* **Incorrect:** `financialDashboard`, `receipt_uploader`, `revenue_form`

### Constants & Configuration Settings (`UPPER_SNAKE_CASE`)
Global system baselines, fixed configuration parameters, and values inside the local configuration environment (`.env`) must be entirely capitalized with underscores separating terms.
* **Correct:** `MAX_UPLOAD_SIZE`, `DEFAULT_PORT`, `DB_CONNECTION_LIMIT`
* **Incorrect:** `maxUploadSize`, `default_port`, `Max_Upload_Size`

---

## 2. Formatting Rules

Code clarity is foundational to ensuring readable logic scripts. We use standard indentation structures across all source sheets.

### Indentation and Spacing
* **Rule:** Use **2 spaces** per indentation level. Do not mix spaces and manual tabs.
* **Brace Layouts:** Use the standard Egyptian brace format. Open curly brackets `{` on the same line as the statement declaration, and place closing brackets `}` on a fresh line aligned with the root statement.
* ```javascript
// Correct Formatting Example
function logTransaction(entryAmount) {
  if (entryAmount <= 0) {
    console.error("Invalid transaction entry amount.");
    return false;
  }
  
  return true;
}
  
checkout -b feature/your-feature-name.

Semicolons and Line Lengths
Semicolons: Explicitly write trailing semicolons ; at the completion of every logical statement or function return.

Line Limits: Keep active script strings under 80 characters per line to ensure text remains readable without requiring continuous horizontal scrolling.

# 3. Commenting Standards
Comments must clarify why something is built a certain way, rather than tracking what a basic command executes. Code blocks should be clean and readable without overwhelming the files with unnecessary text.

Single-Line Logic Clarifications (//)
Use single-line markers directly above complex arithmetic formulas or condition checks. Do not use them for obvious operations.

Correct: ```javascript
// Deduct total operational expenditures from verified collections to compute net cash position
const totalRemainingBalance = currentRevenueSummary - runningExpenseTotal;

Incorrect:
*const totalRemainingBalance = currentRevenueSummary - runningExpenseTotal; // subtracts expense from revenue

Block Documentation (/ ... */)
Every custom-defined integration module, calculation engine, and internal database routing function must be introduced with a descriptive header block detailing inputs and expected outputs.

/**
 * Processes uploaded digital receipts and binds them to an expense log.
 * @param {File} receiptFile - The PDF or image file submitted by the user.
 * @param {number} trackingId - The specific ledger identification key.
 * @returns {boolean} Returns true if the file upload and database link are successful.
 */
function attachDigitalReceipt(receiptFile, trackingId) {
  // Logic goes here
}

# 4. Git Branch Naming Conventions
To keep our version control system organized, branches must never use generic titles like test or updates. All branches must follow a distinct prefix-based naming structure.

Branch Name Formats

New Application Features: feature/short-description
Example: feature/secure-login, feature/receipt-upload

Bug Patches and Fixes: bugfix/short-description
Example: bugfix/arithmetic-error, bugfix/button-alignment

Documentation Refactoring: docs/short-description
Example: docs/update-user-manual, docs/readme-cleanup

Branch Processing Flow
Always isolate a fresh work branch off the updated main structure before editing code: git checkout -b feature/your-feature-name.

Commit changes locally using meaningful tracking statements: git commit -m "Add role-based access validation logic".

Push your work branch up to the centralized workspace, and open a formal Pull Request (PR) for team peer evaluation before merging into main.



Push your work branch up to the centralized workspace, and open a formal Pull Request (PR) for team peer evaluation before merging into main.

