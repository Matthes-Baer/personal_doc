# Excel

This section covers information and resources related to Microsoft Excel.

## Useful Links
- ...


## Helpful Keyboard Shortcuts
- Ctrl + T → Convert data range into a Table.
- Ctrl + ; → Insert today’s date.
- Ctrl + Shift + L → Toggle filters on/off.
- Ctrl + Arrow Keys → Jump to edge of data.
- Ctrl + Shift + Arrow Keys → Select data until edge.
- Ctrl + Space → Select entire column.
- Shift + Space → Select entire row.
- Alt + = → AutoSum quickly.
- F2 → Edit a cell directly (instead of double-clicking).
- F4 → Repeat last action / Toggle absolute/relative references ($A$1).


## Helpful Functions
- SUM(range) → Add numbers.

- AVERAGE(range) → Calculate mean.

- MEDIAN(range) → Middle value.

- MIN(range) / MAX(range) → Lowest and highest.

- COUNT(range) → Count numbers only.

- COUNTA(range) → Count non-empty cells.

- COUNTIF(range, criteria) → Count based on condition.

- SUMIF(range, criteria, sum_range) → Sum based on condition.

- IF(logical_test, value_if_true, value_if_false) → Conditional logic.

- VLOOKUP(lookup_value, table, col_index, FALSE) → Find value vertically.

- HLOOKUP(lookup_value, table, row_index, FALSE) → Find value horizontally.

- XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found]) → Modern, flexible lookup (replaces VLOOKUP/HLOOKUP).

- INDEX(array, row_num, [col_num]) → Return value by row/column position.

- MATCH(lookup_value, lookup_array, 0) → Find position of a value.

- INDEX + MATCH combo → More powerful than VLOOKUP.

- TRIM(text) → Remove extra spaces.

- CLEAN(text) → Remove non-printable characters.

- LEN(text) → Count characters.

- LEFT(text, num_chars) → Extract characters from start.

- RIGHT(text, num_chars) → Extract from end.

- MID(text, start_num, num_chars) → Extract from middle.

- TEXT(value, format_text) → Format numbers/dates as text.

- CONCAT(text1, text2, …) / TEXTJOIN(delimiter, ignore_empty, range) → Combine text efficiently.

- TODAY() → Current date.

- NOW() → Current date & time.

- DATEDIF(start, end, unit) → Difference in days, months, years.

- EOMONTH(start_date, months) → End of month calculation.

- WORKDAY(start, days, [holidays]) → Add working days, skipping weekends/holidays.

- FILTER(array, include, [if_empty]) → Filter data dynamically.

- SORT(array, [sort_index], [sort_order]) → Sort data in a formula.

- UNIQUE(array, [by_col], [exactly_once]) → Extract unique values.

- SEQUENCE(rows, [columns], [start], [step]) → Generate sequential numbers.

- IFS(condition1, result1, condition2, result2, …) → Multiple conditions without nesting IFs.


## General Information
- Most people know F4 locks cell references ($A$1 style), but it also repeats your last action. For example, if you just highlighted a cell yellow, press F4 on another cell and it repeats the highlight instantly. This works for formatting, inserting rows, deleting columns, and more—huge time saver.

- If you have a large dataset, you don’t need to scroll endlessly. Press Ctrl + ↓ to jump to the last filled cell in a column, or Ctrl + → to go to the end of a row. If you want to select everything between your starting point and that end, hold Shift while doing it.

- If you press the Alt key in Excel, you’ll see small letters appear over the ribbon menus. You can navigate entirely with the keyboard (e.g., Alt → H → B → A to add borders). It feels slow at first, but power users can fly through tasks without touching the mouse.

- Instead of only using built-in options (like highlighting duplicates), you can create formula-based rules. For example, if you want to highlight cells in column B when they’re greater than the average of column B, use =B1>AVERAGE($B:$B) in conditional formatting. It unlocks creative data visualization.

- Instead of manually combining cells with =A1&" "&B1, the TEXTJOIN function is much smarter. For example: =TEXTJOIN(", ", TRUE, A1:A10) will combine values from A1 through A10 into one cell, separated by commas, while ignoring blanks. Great for lists.

- Converting data into a Table (Insert → Table or Ctrl + T) adds built-in filters, auto-expanding formulas, and easier references. You can write formulas like =SUM(Table1[Amount]) instead of guessing ranges. Tables are also friendlier with PivotTables and charts.

- Instead of referencing $A$2:$A$100, you can assign a name to that range (Formulas → Define Name). Then, your formula can read =SUM(Sales) instead of =SUM(A2:A100). It makes formulas easier to understand, especially in complex workbooks.

- Right-click → Paste Special offers gems like “Values” (strip formulas), “Transpose” (flip rows into columns), and even “Multiply” (multiply all selected cells by a number). For example, copy a cell with 1.05, select a range of prices, and Paste Special → Multiply to instantly apply a 5% increase.

- Most people use VLOOKUP, but it’s limited because it requires the lookup column to be on the left. The combo INDEX(MATCH()) is more flexible, faster on big datasets, and doesn’t break when you insert columns. For example: =INDEX(B:B, MATCH("Apple", A:A, 0)).

- If you type a pattern in a column (like extracting first names from “John Smith”), Excel’s Flash Fill can auto-complete the rest. Just press Ctrl + E after typing a couple of examples. It’s like a lightweight AI inside Excel for cleaning messy data.
