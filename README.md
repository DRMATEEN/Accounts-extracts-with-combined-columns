# Accounts-extracts-with-combined-columns

# Dealing with a Tangled Mess of Financial Entries

Walk with me.

---

## 1. Promote First Row to Headers

I started by promoting the first row to headers using the **Use First Row as Headers** option under the **Transform** tab. This helped give the dataset proper column titles.

![First Row as Headers](https://github.com/user-attachments/assets/3ab36070-e37a-47fb-bba5-49287820d3b2)

---

## 2. Remove Blank Rows

Next, I removed all the blank rows to clean things up. I did this by going to **Remove Rows** and selecting **Remove Blank Rows**.

![Remove Blank Rows](https://github.com/user-attachments/assets/3185dea4-6878-42b5-8f21-18846f88ca0a)

---

## 3. Understand the Hierarchy via Indentation

Looking closer, I noticed the structure of the data relied on indentation. Leading spaces showed hierarchy:

- No indent → **Account Type** (e.g., *Income Statement*)
- Single indent → **Category** (e.g., *Revenue*)
- Deepest indent → **Subcategory** (e.g., *Stores*)

![Indented Hierarchy](https://github.com/user-attachments/assets/5b4acede-7f8b-49e8-bd4a-6d1f45d83c26)

---

## 4. Mark Hierarchical Levels

To make that structure clearer, I replaced leading spaces with visible markers:

- `/` for Category
- `*` for Subcategory

This gave me a consistent pattern for parsing the structure later.

![Markers Added](https://github.com/user-attachments/assets/fec2987e-30a9-4691-8d84-d47719686035)

![More Markers](https://github.com/user-attachments/assets/db7b2cb1-31bf-4a93-8e32-ee94a473616b)

---

## 5. Extract Category and Subcategory

Using the **Extract** function under **Add Column**, I pulled text after `/` to get the Category and after `*` to get the Subcategory.

![Extracted Columns](https://github.com/user-attachments/assets/49d7f918-e50c-4955-916b-f98b650657c9)

---

## 6. Identify Account Type

I added a conditional column:

- If the row starts with `/` or `*`, return **blank**
- Otherwise, return the original value → which gave me "Income Statement", "Balance Sheet", etc.

![Account Type Conditional](https://github.com/user-attachments/assets/0082eb39-3c27-4745-8c5e-f0f6d61b054b)

---

## 7. Fill Down Contextual Columns

To assign each line item its correct context, I filled down the `Account Type` and `Category` columns. But first, I replaced empty strings with nulls to make the fill-down work properly.

![Fill Down](https://github.com/user-attachments/assets/9afde577-979c-4869-bdc3-1688484c5ad3)

---

## 8. Filter for Line Items Only

I filtered out rows without Subcategories. These weren’t useful for my analysis, so I unchecked blanks in the `Subcategory` column.

![Filter Subcategories](https://github.com/user-attachments/assets/1c3b0826-a663-43a2-ad80-f83e82773c0b)

---

## 9. Final Cleanup

Finally, I cleaned the dataset by:

- Moving `Account Type`, `Category`, and `Subcategory` to the front
- Deleting the original unstructured column

Result: a tidy, hierarchical dataset ready for analysis.

![Final Output](https://github.com/user-attachments/assets/c8d52578-c283-4a04-93f7-a33926bdc5ba)

---

## 🧼 Done

Tangled mess turned into structured clarity.
