# ಶಬ್ದಛೇದ

Static Kannada daily word game. No application server, passwords, dependencies or build step. The complete game is [index.html](index.html); upload that one file to static hosting.

## Word editor's workflow

In the sheet, enter a date in column A when you want to set a specific day's word, and enter Kannada words in column B. Every word in column B becomes part of the fallback pool; a row with today's date takes priority. You can store 300 reviewed words in this same sheet. Use five grapheme clusters (game tiles). Google publication updates may take a few minutes; reload the game afterward.

## One-time maintainer setup

1. Set the sheet timezone to **Asia/Kolkata** in File → Settings.
2. Put `Date` and `Word` in row 1. Add 300 reviewed Kannada words below them; leave Date blank for pool-only words, or fill Date to schedule a specific day.
3. In File → Share → Publish to web, publish that sheet as **Comma-separated values (.csv)** with automatic republication enabled. Keep the sheet's edit access restricted; only the editor needs edit access.
4. Paste the published CSV URL into `SHEET_URL` near the top of `index.html` and upload that one file.

The published sheet contains the words, so a determined visitor can inspect today's answer through browser tools. This keeps the editor workflow and maintenance minimal.

An absent dated override uses a date-based word from every valid word in the sheet. The five bundled words are only a last-resort backup if the sheet has no rows. An unreachable sheet or invalid row shows an error instead of silently changing the answer. Overrides apply on reload; progress is stored separately for each date and word. Kannada conjunct segmentation may vary by browser Unicode version; test candidate words in supported browsers.

References: [Google custom functions](https://developers.google.com/apps-script/guides/sheets/functions), [publishing individual tabs](https://support.google.com/docs/answer/183965).
