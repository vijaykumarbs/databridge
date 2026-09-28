# DataBridge — Product plan

## What it does

DataBridge takes a CSV or Excel file and a list of required output columns. It lets an analyst match the input columns to the output columns, check each row, and download a new Excel file. Rows that fail a check carry an error message.

Optional AI mapping can suggest which input column matches each output column. It sends the headers and up to three sample rows per file to the selected AI provider. Without AI, DataBridge matches columns by name.

## Who it is for

An ERP data analyst preparing vendor or legacy master data for review before a migration or cutover.

## The problem

The analyst receives files whose column names and layouts differ from the ERP import template. Today, the analyst renames columns, copies data into a new file, adds spreadsheet checks, and follows up on bad rows. The same work must be repeated for each source. A missed error can delay the next migration step.

This describes the problem the product is designed to address. No pilot or measured time savings have been reported.

## First version

1. Upload CSV, XLS, or XLSX files.
2. Set the output columns, required fields, and checks such as email, number, date, maximum length, minimum value, or regular expression.
3. Optionally ask AI to suggest column matches.
4. Run the checks and review the row count and errors.
5. Download all rows, only valid rows, or only rows with errors.

Files are processed in the browser. The app does not write to an ERP. Settings and the optional API key are stored in browser storage.

## Why this scope

Start with file mapping and row checks because these are the steps an analyst repeats before loading data. Keep exact-name mapping and manual review available when AI cannot be used. Make errors visible in the downloaded file so the analyst can send them back for correction.

## Not included

- connecting to an ERP or loading data into one;
- team accounts, approvals, shared schemas, or a history of changes;
- changing source values automatically;
- checking whether a value is correct in the business context;
- handling several worksheets as one combined input.

## Pilot and measures

**Status: no pilot run yet.** Test with one data analyst and an approved sample file. First time the analyst's normal process; then time the same task with DataBridge. Have a reviewer prepare the correct list of errors before the trial.

Record:

- minutes to produce a reviewed output;
- number of column matches the analyst had to correct;
- known errors found and known errors missed;
- whether each error message tells the analyst what to fix.

Agree in advance what counts as an acceptable result. A faster file is not a success if it misses a known error. Do not publish customer files or claim savings until a pilot has been run and permission is granted.

## Questions to answer

- Which checks do analysts repeat most often?
- How many AI-suggested matches need correction?
- Can teams share the error file with data owners as-is?
- Which data is not allowed to be sent to an AI provider?
