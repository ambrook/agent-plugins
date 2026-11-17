---
name: use-ambrook
description: Use when someone asks to review their Ambrook books or export financial statements, including month-end briefings, profit and loss, balance sheets, unpaid customer invoices, bills due, or transactions missing a category.
---

# Review your Ambrook books

Use the Ambrook connection to answer questions about the user's books. Fetch only the sections they ask for. For a month-end briefing, combine profit and loss, unpaid invoices, bills due, and bookkeeping cleanup.

## Choose the business and dates

- Call `whoami` when you need to identify the business or resolve relative dates. If the user names an accessible business, use its returned ID. If there is exactly one accessible business, use it. If several are accessible and the request is ambiguous, ask which one to use before pulling records; you can mention the returned default. If none are accessible, say so and stop.
- Use the selected business's local date from `whoami` to resolve relative periods. Keep Ambrook's calendar dates as returned. If the connection fails, explain what you couldn't retrieve and suggest reconnecting or opening Ambrook.
- For `query_profit_and_loss` and `query_balance_sheet`, input `start` and `end` dates are inclusive. Each column's `meta.startDate` is inclusive and `meta.endDateExclusive` is exclusive. When present, subtract one calendar day from `meta.endDateExclusive` to display the column's inclusive through-date. A column through December 31 has an exclusive bound of January 1.

## Pull and explain the results

- **Profit and loss:** Use `query_profit_and_loss` for statement totals. For a month-over-month comparison, group by month across the requested complete calendar months. Use the requested accounting basis; if omitted, use the tool's default and label it. Compare the same lines across months and explain only changes supported by the returned report. If the report has no activity, say so.
- **Unpaid customer invoices:** Use `list_invoices` with the unpaid filter, and sort by due date when asked which invoices are due first. Report the returned outstanding total for all matches separately from the limited list shown. For each listed invoice, show the customer, amount still owed, and due date when available.
- **Bills due:** Use `list_bills` with the unpaid filter. For a request through the next 30 days that includes overdue bills, set the upper due-date bound to 30 calendar days after the business's local date and leave the lower bound unset. Use the returned outstanding total across all matches and mark listed bills overdue only if their due date precedes that local date.
- **Bookkeeping cleanup:** Use `list_transactions` to find recent transactions missing a category. When suggestions are requested, fetch details with `get_transaction` as needed. Describe returned suggestions as unapplied, and say when no suggestion is available.

Give the business, dates, and accounting basis where relevant. Convert cents to dollars and use `get_app_links` for individual records you cite; pass only IDs from Ambrook and omit links that the tool reports as invalid. Distinguish an empty result from a failed or partial lookup. Keep the answer short and state what you couldn't verify.

## Export financial statements

- When `export_financial_report` is available to the connection, use it for balance sheet and profit-and-loss files. Some connections do not advertise this tool yet. If it is unavailable, use an advertised report tool that supports the request or explain what you cannot export; do not invent a tool result.
- Supply the selected `orgId`, the user's explicit `basis` (`CASH` or `ACCRUAL`), and `period`. Ask for the basis or date scope when missing. For `report=balance_sheet`, supply only `period.end`, the inclusive as-of date. For `report=profit_loss`, supply inclusive `period.start` and `period.end`, or `period={allTime:true}` only when the user explicitly requests all time. Resolve relative dates using the business's local date from `whoami`.
- Use `detail=summary` unless detailed rows are requested. Supported formats are `Csv` (default), `Excel`, `Html`, and `Pdf`. Use `linkedEntityId` or P&L tag filters (`enterpriseId`, `fundingProgramId`, `locationId`, `projectId`) only with IDs returned for the selected business. Leave unrecorded transactions excluded unless requested. Grouping, comparisons, and display customization are unsupported by this tool; do not silently drop them from the request.
- Present returned CSV/HTML as text and Excel/PDF as files, using the effective parameters and filename. If the result reports `size_limit_exceeded`, share its `downloadUrl` and explain that the user must open it in a browser signed in to Ambrook. The link regenerates the selected format for the selected business. Do not fetch that link through another integration or claim the file was delivered inline.

## Respect read-only access

Ambrook tools can read records. They cannot create or edit records, send invoices, pay bills, or move money. For a request to make a change through this plugin, explain the limitation without calling tools to attempt it. Do not use a browser or another integration as a fallback. If the relevant record is already identified and you have its link, offer it so the user can open Ambrook themselves.
