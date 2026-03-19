# DeltaCount

DeltaCount is a browser-based tool for translation teams to quickly calculate billable word counts for translation of changes projects.

Live site: https://oliverbirchill.github.io/deltacount

## What The Tool Does

- Opens `.docx` files directly in the browser
- Reads tracked changes from the document XML inside the Word file
- Applies billable word count rules
- Shows a per-file result table and a running total
- Runs entirely client-side, so no server or backend is required

## Word-Count Rules

DeltaCount uses these rules:

1. If an insertion or deletion happens within a sentence, the full word count of that sentence is billable.
2. If a deletion removes the entire sentence, the billable count for that sentence is `0`.
3. If a whole new sentence is inserted, that sentence's words are billable.
4. If a sentence has no tracked changes, the billable count for that sentence is `0`.
5. If a sentence contains multiple tracked changes, it is still only counted once.

Sentence boundaries are detected with punctuation-aware logic and common abbreviation handling, including cases such as "e.g.", "i.e.", "Dr.", and "Mr." to avoid false sentence splits.

Legacy .doc files must be re-saved as .docx in Word before they can be used here.

## How To Use

1. Open index.html in a browser, or visit the GitHub Pages site.
2. Drop one or more .docx files onto the table area, or click **Browse Files**.
3. Review the billable count, status, and message for each file.
4. Read the total billable word count in the status bar at the bottom.
5. Click **Clear** to remove the current batch.

## Technical Notes

- The app is a single static index.html file.
- It uses CDN-hosted JSZip to unzip .doc files in the browser.

