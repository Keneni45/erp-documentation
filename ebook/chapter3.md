Below is a **chapter-by-chapter, field-by-field** walk-through of the **OnyxERP – Vendors Management System** user guide (January-2024 edition).  
I kept the original structure, but replaced the heavy prose with **plain language**, **bullet-style** explanations, and **real-life examples** so you can actually use the screen the same day you read it.

--------------------------------------------------------
CHAPTER 1  –  SYSTEM SETUP  (do once, then forget)
--------------------------------------------------------
1.1  Vendors System Parameters  
(“The rule book – get it wrong and every later transaction is wrong.”)

A.  VENDOR NUMBERING  
- Vendor Number Length – max digits you will ever allow (9 = 999,999,999).  
- Vendor Number Type –  
  – Numerical = system auto-counts 1,2,3…  
  – Alphanumerical = you type V001, V002… (no auto-sequence).

B.  GENERAL LEDGER LINK  
- Multi Accounts = every vendor gets his own G/L account (big suppliers).  
- Accounts Group = one common G/L account per group (small suppliers).  
→ Decide now; you can’t swap after you start entering invoices.

C.  DOCUMENT SEQUENCES (all modules)  
Pick one column that controls the running number:  
  Automatic-Can-Be-Modified | Automatic-Cannot-Be-Modified | Manual  
Same three choices for: Purchase Requests, Orders, Invoices, Returns, GRN, Promissory Notes.

D.  PURCHASE INVOICE SEQUENCE LEVEL  
Accumulative = one series per branch.  
By Type = separate series for Local vs Foreign.  
By PaymentMethod = Cash-Inv-001, Credit-Inv-001, Cheque-Inv-001…  
Warehouse / Cost-Center / Invoice-Type = even more splits.  
→ Pick the level your auditor expects to see on the printed invoice.

E.  CONTRACTS  
Link Contracts to Purchase Order: Unused | Optional | Mandatory  
→ “Mandatory” means you can’t raise a PO without choosing an approved contract first.

F.  RETURNS  
Use Purchase Return Request: Unused | Optional | Mandatory  
→ “Mandatory” forces user to create a “request” document before they can issue a real credit-note.

G.  VAT / TAX  
VAT Calculation Method:  
  Price = before any discount.  
  Price – Discounts = after all discounts.  
  Price – First Discount = after first discount only.  
Tax Usage Method:  
  All Vendors = same method for everyone.  
  By Vendor = each vendor can have its own (set later in Vendors Data).

H.  FREE-OF-CHARGE QTY  
Use Free Of Charge Quantities: tick if you sometimes receive “buy 10 get 2 free”.  
Impact:  
  – Affects/Reduces Cost = spreads total cost over 12 pcs → unit cost lower.  
  – Post to Free-Qty-Revenue Account = books the 2 pcs as income at sales price.

I.  ROUNDING  
Rounding Fractions Method:  
  – Auto-add fractions to discount = hide pennies in discount line.  
  – <0.5 = discount, ≥0.5 = expense = keeps pennies visible.

J.  DISCOUNT POSTING  
Earned Discount:  
  – Distribute to Item Cost = reduces stock value (preferred by finance).  
  – Post to Earned-Discount Account = shows as other income.

K.  ITEM-LEVEL DISCOUNTS  
Use Discount at Items’ Level: shows a “Discount %” column inside every invoice line.  
Number of Discounts: none / one / two / three (gives separate columns so you can audit each type).

L.  PROMISSORY NOTES  
Use Promissory Notes: activates the screens Credit Promissory Notes, Due Credit Promissory Notes.  
Promissory Notes Impact on Vendor’s Account:  
  – tick = note hits vendor sub-ledger immediately.  
  – untick = note sits in intermediary account until matured.

M.  PURCHASE WORK-FLOW  
Link PO to Purchase Request = you can’t order before a request is entered.  
Link Invoice to PO = you can’t receive a bill before an order exists.  
Notify with Previous Un-processed… = pops up a warning if older PO/PR lines are still pending.

N.  WAREHOUSE CONTROLS  
Use Multiple Warehouses = grid inside invoice lets you receive goods to more than one warehouse.  
Purchase Return from Same Purchase Warehouse = only allows returns from the warehouse that originally received.

O.  VENDOR PRICING  
Auto Update Vendor Prices = every new invoice overwrites the “Last Purchase Price” in Items Data.  
Use Vendors Price-lists = activates a separate screen where you can store each vendor’s catalogue prices (with validity dates).

P.  SERVICE ITEMS  
Service Invoice flag = invoice posts to expense accounts instead of stock.  
(Use when you buy services, not physical goods.)

Q.  OTHER QUALITY CHECKS  
Check Item-Vendor Linking = blocks invoice if item has never been linked to this vendor.  
Check Item Cost Limit = blocks PO if price is outside Min/Max % set in Items Data.  
Representative Number Mandatory = can’t save invoice without choosing a purchase rep.  
Reference Number Mandatory = can’t save without typing supplier’s quotation number, delivery note, etc.

--------------------------------------------------------
1.2  Vendors Types  
Purely for reporting: Local, Foreign, Raw-Material, Spare-Parts, etc.  
→ Create once, pick in Vendors Data, filter reports later.

--------------------------------------------------------
1.3  Vendors Categories  
A, B, C or Excellent, Good, Fair.  
You set credit days, discount %, or simply use for statistics.

--------------------------------------------------------
1.4  Additional Discounts Types  
“Volume Rebate”, “Early Payment”, “Marketing Support”…  
Flag “Return Upon Making Returns” = system auto-reduces the rebate if you later return goods.

--------------------------------------------------------
CHAPTER 2  –  SYSTEM INPUTS  (master data)
--------------------------------------------------------
2.1  Vendors Group  
Example: LOCAL, FOREIGN, AFFILIATED.  
If you chose “Accounts Group” in parameters, drop the G/L account here once; every vendor inside inherits it.

--------------------------------------------------------
2.2  Vendors Data  (the heart of the system)

TAB 1  MASTER  
- Group → inherits G/L account (if group option used).  
- Vendor Number → leave blank for auto, or type your own code.  
- Name / Foreign Name → prints on PO, cheque, VAT report.  
- Branch → tie vendor to one branch or leave blank for all.  
- Inactive flag → instantly blocks new transactions (old ones stay).

TAB 2  CURRENCIES  
Tick every currency you will allow.  
Set Maximum Amount for Requests & PO per currency → system warns if you exceed.

TAB 3  OTHER DATA  
- Credit Period (days) → used to calculate invoice due date.  
- Blacklist → tick + reason → vendor appears on “Banned Suppliers” report.  
- Last Purchase Date, Last Payment → system maintains automatically.

TAB 4  ADDITIONAL DATA  
- Use Vendors Price-lists → vendor can have his own catalogue.  
- VAT Calculation Method → override the global method for this vendor only.  
- Tax Deduction at Source → tick if you must withhold WHT for him.  
- Auto Sync Customer-Vendor → enables EDI portal (advanced).

TAB 5  WITHDRAWAL PERIOD LIMITS  
Example: “SAR 500,000 per 30 days” → system warns if you try to raise PO 501,000.

TAB 6  ADDRESSES & IDs  
Unlimited address lines; pick one as Main.  
Identifiers: Commercial Register, VAT No., Tax Article → prints on invoice, VAT report.

TAB 7  ADDITIONAL FIELDS  
Create your own captions (Insurance Expiry, ISO Certificate…).

TAB 8  BANKS  
Store each bank account once; later screens pick from here.

TAB 9  ACCOUNTS  
Current, Advance Payment, Insurance → sub-accounts you want to track separately.

TAB 10 TRANSACTIONS  
Read-only list of every voucher that hit this vendor.

TAB 11 STATISTICS  
Opening, Purchases, Returns, Payments, Balance → real time.

TAB 12 ARCHIVE  
Attach PDF contracts, insurance papers, ISO certificates.

BULK TOOLS  
- Modify Vendors Data → mass update (city, credit days, category…).  
- Import from Excel → download template, fill, upload, validate, save.

--------------------------------------------------------
2.3  Purchase Representative Data  
Code, name, phone, region, guarantee (if handles cash), user privileges.  
→ Links to invoice header; appears on commission reports.

--------------------------------------------------------
2.4  Vendors Opening Balances  
Run only once, first month of go-live.  
Choose currency, enter debit or credit per vendor → system posts one journal to G/L.  
Later year-closing carries forward automatically.

--------------------------------------------------------
CHAPTER 3  –  SYSTEM TRANSACTIONS  (daily work)
--------------------------------------------------------
3.1  Contracts Data  
Header: vendor, currency, start/end dates, amount, cost-center/project.  
Detail grid: item, qty, unit price, free-of-charge qty, discount %, tax → total = contract value.  
Other tabs:  
  – Period Extension → renew without creating new number.  
  – Add Amount → increase value (needs approval).  
  – Batches Data → split value into monthly/weekly payment batches; system creates invoice for each batch automatically.  
  – Guarantee → type, value, start/end, guarantor name.  
Approval button → locks contract; now PO can pick it.

--------------------------------------------------------
3.2  Renew Contracts  
Pick old contract → system copies all lines, sets new start = old-end + 1 day, appends suffix (2.1, 2.2…).  
Edit whatever you need, approve, done.

--------------------------------------------------------
3.3  Additional Discounts on Purchase Invoices  
Reason: supplier gives you extra rebate after invoice is already posted.  
Two types:  
  a) By Invoice → header level; enter % or amount; system suggests vendor account or intermediary account.  
  b) By Item → grid appears inside invoice lines; needs “Use Discount at Items’ Level” parameter on.  
Can later pull the discount into Stock Adjustment if you want to reduce item cost.  
Accounting:  
  Dr Vendor (or Intermediary)  
  Cr Additional Discount (income)

--------------------------------------------------------
3.4  Settle Vendor Installments  
Used only when parameter “Pay Installments Manually” is on.  
Scenario: you owe vendor 1,000,000 (opening 200k + 4 invoices 200k each).  
You pay 400k and want to knock-off invoice-1 and invoice-3 only.  
Screen shows debit documents on left, credit documents on right; you allocate manually; save → system marks those invoices as paid.

--------------------------------------------------------
3.5  Credit Promissory Notes  
Three kinds: Letter-of-Credit, Vendor, Other Accounts.  
Header: number, date, currency, bank, commission %, insurance %.  
Detail: number of notes, installment days → system calculates due dates, amounts (invoice + commission + insurance).  
Posting:  
  Dr LC/Vendor/Expense accounts  
  Cr Promissory Notes account (liability)  
When bank later deducts: use “Due Credit Promissory Notes” screen → set status “Due” → system:  
  Dr Promissory Notes  
  Cr Bank

--------------------------------------------------------
3.6  Vendors Claims  
Combines several unpaid invoices into ONE claim number, then lets you pay that claim in equal installments.  
Example: 12 invoices totalling 120,000 → create claim, 4 installments 30,000 every 30 days.  
System can fetch those installments automatically into Payment Voucher or Journal Entry.

--------------------------------------------------------
CHAPTER 4  –  SYSTEM REPORTS  (one click)
--------------------------------------------------------
All reports live under “Vendors Reports” node; same print engine everywhere.

1. Vendors Data Report – mailing list, phone, city, activity.  
2. Opening Balances Report – trial balance at cut-off.  
3. Account Statement – ledger card for one vendor or range.  
4. Aged Debts – classic 0-30, 31-60, 61-90, >90 columns.  
5. Installments Report – unpaid instalments per contract.  
6. Contracts Data – list or detailed, can print items grid.  
7. Purchases Additional Discounts – audit trail of every rebate.  
8. Purchase Analysis – by vendor, item, group, branch, period.  
9. Payment Vouchers – cheque register, promissory-note register.  
10. VAT Purchase Ledger – ready for tax authority upload.

--------------------------------------------------------
THAT IS THE ENTIRE MANUAL – NOW IN NORMAL WORDS  
--------------------------------------------------------
Keep this summary open on one screen, Onyx on the other, and you can set up vendors, raise a PO, receive stock, record the bill, pay it, and print an ageing report without ever reopening the original 200-page PDF.