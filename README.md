# EWC LSP - EUDI Wallet Rulebooks and Data Schemas Electronic Attribute Attestations

This repository contains all rulebooks and data schemas utilised in the EWC Large Scale Pilot use cases, providing a comprehensive reference for interoperability, governance, and compliance in digital identity frameworks.

Authors are encouraged to create new rulebooks or data schemas and commit to them in a separate branch. Once agreed upon within your WP, raise a PR to merge to the main branch.

## Rulebooks

Here is the list of all Rulebooks defined and used within the EWC scope and their status.

| **Rulebook #** | **Rulebook Title**                                                                                       | **Status (Under Development/Approved)** |
| -------------- | -------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| RB-001         | [Legal Person Identification Data (LPID) Rulebook](/rulebooks/rb001-legal-person-identification-data.md) |                                         |
| RB-002         | [EU Company Certificate Data Rulebook](/rulebooks/rb002_eu_company_certificate.md)                       |                                         |
| RB-003         | [IBAN Data Rulebook](/rulebooks/rb003_IBAN_attestation.md)                                               |                                         |

## Data Schemas

Here is the list of all Data Schemas defined and used within the EWC scope and their status.

| **Data Schemas #** | **Data Schemas Title**                                                                        | **Status (Under Development/Approved)** |
| ------------------ | --------------------------------------------------------------------------------------------- | --------------------------------------- |
| DS-001             | [EU Company Certificate](/data-schemas/ds001-eu-company-certificate.json)                     | Under Development                       |
| DS-002             | [IBAN attesatation](/data-schemas/ds002-iban-attestation.json)                                | Under Development                       |
| DS-003             | [Signatory Rights](/data-schemas/ds003-signatory-rights-attestation.json)                     | Under Development                       |
| DS-004             | [Legal PID](/data-schemas/ds004-legal-person-identification-data.json)                        | Under Development                       |
| DS-005             | [Photo ID](/data-schemas/ds005-photo-id-travel-document.json)                                 | Under Development                       |
| DS-006             | [Ultimate Beneficial Owners](/data-schemas/ds006_ultimate_beneficial_owners_attestation.json) | Under Development                       |
| DS-007             | [Payment Wallet Attestations](/data-schemas/ds007-payment-wallet-attestation.json)            | Approved                                |
| DS-008             | [Payment Data Confirmation ](/data-schemas/ds008-payment-data-confirmation.json)              | Approved                                |

## Naming Conventions

### Rulebook

1. All rulebooks shall be in the folder `/rulebook` [here](/rulebooks).

2. For the rulebook, please start with `rb001-<name-of-the-rulebook01>`, `rb002-<name-of-the-rulebook2>` etc. Use the last number in the main branch to decide the following sequence.

### Data Schemas

1. All data schemas shall be in the folder `/data-schemas` [here](/data-schemas).

2. For the data schemas, please start with `ds001-<name-of-the-rulebook01>`, `ds002-<name-of-the-rulebook2>` etc. Use the last number in the main branch to decide the following sequence.
