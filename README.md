# InvoiceFinder

An Android app concept for finding, understanding, and tracking invoices delivered through Gmail.

InvoiceFinder brings invoice discovery, PDF extraction, Swedish payment-detail validation, and payment tracking into one mobile workflow. It was built as a portfolio project to demonstrate practical Android engineering and document-processing skills.

> **Source availability:** This public repository is a project showcase. The application source code is maintained in a separate private repository.

## Product Overview

- Connects to Gmail and identifies likely invoice messages, including PDF attachments and text-only invoices.
- Extracts supplier, amount, due date, invoice number, OCR reference, and Bankgiro or Plusgiro details.
- Reads native PDF text and layout, then uses on-device ML Kit text recognition when important fields are missing.
- Checks payment details, due dates, and whether net amount plus VAT matches the total.
- Organizes invoices with search, sorting, date ranges, and filters for PDFs, warnings, and upcoming due dates.
- Supports reviewing and editing extracted details, sharing invoice information or PDFs, and marking bills paid.
- Runs scheduled background checks and configurable notifications for new invoices and approaching due dates.

## Engineering Work

- Designed a staged email-classification pipeline using Swedish and English invoice terms, attachment signals, and negative signals for receipts and marketing messages.
- Built a layout-aware PDF parser that relates nearby text elements and recognizes Swedish payment-slip code lines.
- Added OCR fallback for scanned PDFs and validation rules for extracted financial fields.
- Separated UI, state, persistence, and Gmail operations across Compose screens, a ViewModel, a repository, and a Room database.
- Covered payment-slip parsing and invoice validation with unit tests, including malformed and misleading examples.

## Skills and Technologies

- **Android:** Kotlin, Jetpack Compose, Material 3, AndroidX Lifecycle
- **App architecture:** Kotlin Coroutines, Room, Hilt, WorkManager, repository and ViewModel patterns
- **Integrations:** Google Sign-In, Gmail API, Android notifications
- **Document processing:** PDFBox-Android, layout-aware text extraction, ML Kit Text Recognition
- **Quality:** JUnit, parsing tests, domain validation

## Data and Permissions

Invoice records are stored in a local Room database, and downloaded attachments are kept in app-private storage. Gmail integration requests the `gmail.modify` permission so the app can update Gmail labels when an invoice is marked paid.

The dashboard currently contains a hard-coded overdue sample invoice to illustrate the interface. It is demo content, not a message retrieved from Gmail.

