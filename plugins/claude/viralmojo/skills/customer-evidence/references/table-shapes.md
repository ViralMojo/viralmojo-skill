# Customer-evidence table shapes

Described in product terms — the exact stored shape lives in code.

## Customer reviews

One row per review: when it was left, its rating, the product it's about, the review's headline and full text, who left it (when the source names them), where it came from (a first-party store versus a third-party site), and a link back where one exists.

## Post-purchase surveys

**One row per answer, not per respondent.** A buyer who answered five questions becomes five rows, all tied to the same response and to the paid order behind it. Each row carries its question, the answer (as free text or as a number, depending on the question) and, for multi-select questions, the chosen options.

The tie to a paid order is what makes a survey a **confirmed-buyer** signal — a review, by contrast, may not come from a buyer at all.

## What is never added

The product surfaces only what the upload actually contained. It does **not** invent a verified-purchase flag, helpful / upvote counts, or a sentiment score the source didn't carry.
