# IBAN Attestation Data Rulebook

## Table of Contents

1. [Introduction](#1-introduction)
   
    1.1. [Scope](#11-scope)  
    1.2. [Background](#12-background)  
    1.3. [Goal of the IBAN Attestation](#13-goal-of-the-iban-attestation)  
    1.4. [Key words](#14-key-words)  
    1.5. [Terminology](#15terminology)  
2. [IBAN attestation Issuance process](#2-iban-attestation-issuance-process)  
3. [IBAN attestation Verification process](#3-iban-attestation-verification-process)  
4. [IBAN attributes](#4-iban-attestation-attributes)
   
   4.1. [Parties-related attributes](#41-parties-related-attributes)  
   4.2. [Minimum number of optional attributes](#42-minimum-number-of-optionnal-attributes)
   
6. [Trust infrastructure details](#5-trust-infrastructure-details)
   
    5.1. [Trust requirements on the IBAN attestation from the perspective of company registration offices as authentic sources for the IBAN](#51-trust-requirements-on-the-iban-attestation-from-the-perspective-of-company-registration-offices-as-authentic-sources-for-the-iban)  
    5.2. [Trust a signature or seal over a IBAN](#52-trust-a-signature-or-seal-over-an-iban)  
    5.3. [IBAN Provider Trusted List](#53-iban-provider-trusted-list)  
    5.4. [SD-JWT-compliant](#54-sd-jwt-compliant)  
7. [References](#6-references)  

## 1. Introduction

*Disclaimer: This document is a draft and requires further review and completion before its publication as the EWC WP3 T3.2.3 deliverable. The terminology in Section 1.5 was generated using AI and serves as a preliminary framework for Business Registries to discuss with their legal departments to determine the most appropriate terms for the given context.*

### 1.1 Scope

This document serves as the International Bank Account Number (IBAN) Attestation Rulebook. It outlines the requirements specific to IBAN attestation, including the processes for its issuance and verification. The rulebook provides information on the background and attributes of IBAN attestation, its trust infrastructure, and technical implementation.

The IBAN attestation is intended exclusively for use by legal entities (companies).

[Topic 10/23](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/blob/main/docs/annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-the-eudi-wallet) in the ARF 1.4 specifies that attestation must be issued in the [SD-JWT VC] format, among others. This rulebook is designed to align with the [SD-JWT VC] requirements.

### 1.2 Background

The necessity for IBAN attestation stems from the extensive use of IBANs for cross-border banking and payment transactions within the SEPA (Single Euro Payments Area) and beyond. Financial institutions and service providers require a secure, standardized method to verify bank account ownership to mitigate fraud, enhance trust, and improve process efficiency.

The IBAN attestation will be employed by companies participating in EWC pilots, and adjustments to this rulebook may be required based on pilot findings.

### 1.3 Goal of the IBAN attestation

The IBAN attestation is designed to:

- Provide a secure and verifiable credential to confirm a legal entity’s ownership of an IBAN.
- Enable interoperability and machine-readability for streamlined financial system automation.
- Establish a unified standard to replace diverse national verification processes.

### 1.4 Key words

This document uses the capitalized key words 'SHALL', 'SHOULD', and 'MAY' as specified in [RFC 2119], i.e., to indicate requirements, recommendations, and options specified in this document.

Additionally, 'must' (non-capitalized) is used to denote external constraints mandated by other documents or regulations. The term 'can' indicates capability, while terms like 'will,' 'is,' or 'are' are used as factual statements.

### 1.5 Terminology

The terminology in this document follows Regulation (EU) 2024/1183.

To fully understand the data schema, the following definitions are provided :

- **IBAN** (International Bank Account Number): A standardized international numbering system used to uniquely identify a bank account. The format includes a two-letter country code, check digits, and a basic bank account number (BBAN).
- **Holder**: A legal person who owns the bank account associated with the IBAN.
- **ASPSP** (Account Servicing Payment Service Provider): A financial institution that provides and maintains payment accounts accessible via online platforms.
- **PSD2** (Payment Services Directive 2): An EU directive that regulates payment services and providers throughout the European Economic Area, promoting competition and innovation.
- **SCA** (Strong Customer Authentication): A requirement that ensures electronic payments are performed with multi-factor authentication to increase the security of electronic payments. It is a requirement of the PSD2 on payment service providers.
- **BIC** (Bank Identifier Code): A unique code assigned to financial institutions used to identify the bank during international transactions. Also known as the SWIFT code.
- **Clearing Number**: A number used to identify a financial institution or a branch within a country’s clearing system.
- **SWIFT** (Society for Worldwide Interbank Financial Telecommunication): A global provider of secure messaging services and financial transactions among banks and financial institutions.
- **Open Banking**: The practice of enabling third-party financial service providers to access banking and transaction data via APIs, typically under PSD2 compliance.


## 2. IBAN Issuance process

Only financial institutions acting as Account Servicing Payment Service Providers (ASPSP) are authorized to issue IBAN attestations. These entities are considered the authentic sources of IBAN information. Issuance may occur directly or through a delegated Qualified Electronic Attestation Authority (QEAA).

The issuance process must comply with relevant EU regulatory and technical standards, including PSD2, to ensure secure and standardized account information access.

The individual requesting the IBAN attestation on behalf of a legal entity must have verified access to the legal entity's bank account. PSD2 mandates that such access be made through SCA.

In the EWC context, a generic attestation issuance process, as described by wallet providers in the pilots, is outlined in [RFC-001](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc001-issue-verifiable-credential.md).

Only companies possessing a valid LPID in their wallets can request IBAN attestations. Consequently, these attestations can only be issued to EUDI-compliant organizational wallets.

## 3. IBAN Verification process

In the EWC context, wallet providers have described a generic verification process during the pilots, outlined in [RFC-002](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc002-present-verifiable-credentials.md).

At this stage of the pilot, no specific data or attribute verification is required. The decision to verify attributes depends on the needs and requirements of the Relying Party within a business or administrative process.

During the testing phase, there will be no restrictions on the Holder's wallet regarding the ability to present the IBAN. However, tests will evaluate whether access limitations for IBAN presentations might be necessary in the future.

## 4. IBAN attributes

IBAN attributes have been defined together by Archipels and _**WP 2.3**_  stakeholders in the EWC pilot in accordance with the PSD2.

This table contains the name of the attribute, its description, and whether the attribute is required or not.

| Property Name | Description | Required |
| ------------- | ----------- | -------- |
| bank_account | Attributes representing the bank account. | Yes |
| account_name | Name of the account, generated by the bank or customized by the owner. | Yes |
| IBAN | International Bank Account Number, as defined in ISO 13616:2020. | Yes |
| account_type | Nature of the bank account. | Yes |
| account_currency | Currency code used of the account, as defined in ISO 4217:2015. | Yes |
| account_usage | Specification about the private or professional usage of the account. This additional information allows to further distinguish personal bank accounts from professional bank accounts. | No |
| account_ownership | Attributes representing the account ownership. | Yes |
| owner_name | Legal name of the legal person owning the account. | Yes |
| parties | List of parties involved in the account ownership. | No |
| full_name | Full name of the physical person. | Yes |
| role | Role of the physical person. | Yes |
| account_provider | Attributes representing the account provider. | Yes |
| provider_name | Name of the financial institution providing the account. | Yes |
| bank_identifier | Bank identification number. | Yes |
| provider_country | Alpha-2 country code, as defined in ISO 3166-1, of the provider country or territory. | Yes |
| BIC | BIC or SWIFT code, as defined in ISO 9362, of the financial institution. | No |
| clearing_number | Clearing number, only used in some countries, of the identification of the financial institution. | No |


IBAN metadata are aligned with the metadata of organizational credential attestations already defined in [EUDI wallet data schemas](https://github.com/EWC-consortium/eudi-wallet-rulebooks-and-schemas/tree/main/data-schemas)

This table contains the name of the metadatum, its description, and whether the metadatum is required or not.

| Metadatum Name | Description | Required |
| ------------- | ----------- | -------- |
| issuing_authority | Attributes representing the bank account. | Yes |
| issuing_authority_id | Name of the account, generated by the bank or customized by the owner. | Yes |
| issuance_date | International Bank Account Number, as defined in ISO 13616:2020. | Yes |
| expiry_date | Nature of the bank account. | Yes |
| authentic_source_id | Currency code used of the account, as defined in ISO 4217:2015. | Yes |
| authentic_source_name | Specification about the private or professional usage of the acccount. | No |
| credentialSubject | Attributes representing the account ownership. | Yes |


The IBAN schema is available in the EWC schemas and rulebooks repository: [IBAN data schema](https://github.com/EWC-consortium/eudi-wallet-rulebooks-and-schemas/blob/main/data-schemas/ds002-iban-attestation.json).

### 4.1 Parties-related attributes

*Note*: The "owner_name" field is only intended for the legal name of the company. If the company is owned by a single physical person, this physical person's relation to the company SHALL be indicated in the "parties" field. 
This document defines the following attributes related to the parties of the IBAN holder:

- full_name
- role

The detailed attributes allow the IBAN attestation to encapsulate the natural person that have access to the legal entity's bank account.

Parties included in the IBAN attestation serve solely to provide information about the individuals with access to or ownership of the bank account. 
The presence of a party in the attestation DOES NOT determine who can present or use the IBAN attestation in a business process.

### 4.2 Minimum number of optional attributes

There is no minimum number of optional attributes for the IBAN. Each Issuer will have the responsibility to fill in the attributes when provided by the original source.

## 5. Trust infrastructure details

In this chapter, trust requirements and general considerations regarding the IBAN attestation itself are described.

### 5.1 Trust requirements on the IBAN attestation from the perspective of company registration offices as authentic sources for the IBAN

In the ARF 1.4, the following information for Pub-EAAs and QEAAs Providers is given.

Pub-EAAs and QEAAs Providers are trusted entities responsible to:

- Verify the identity of the EUDI Wallet User in compliance with LoA high requirements.
- Issue attestations to the EUDI Wallet in a harmonized common format.
- Make available information for Relying Parties to verify the validity of the attestation.

The IBAN SHALL contain the qualified electronic signature or qualified electronic seal of the issuing body and adhere to the legal requirements defined in Annex VII of the Regulation (EU) 2024/1183.

The IBAN SHALL follow the SD-JWT format.

It SHALL not be possible to log into company registers solely with the IBAN, since procedures legally require an individual person to act.

IBAN Issuers SHALL follow the IBAN requirements and trust mechanisms defined by Authentic Sources on a national level.
Authentic Sources that are company registration offices need to accept each other's PUB-EAA attestations according to the regulation. Therefore, common legal trust mechanisms need to be established ifor the trust ecosystem to be trustworthy: 

- The IBAN unique identifier SHALL be unique and agreed upon on EU and EES level.
- There SHALL be one common schema for the IBAN which is accepted by all company registries offices.
- Only mandatory metadata and attributes SHALL be present in the IBAN attestations.
- The IBAN SHALL be in a machine-readable format defined in the ARF during its whole lifecycle.
- The IBAN SHALL be in a format that can scale to additional/new legal forms.
- The IBAN SHALL apply for all legal persons.
- The issuer of the IBAN SHALL be responsible for its revocation. 

### 5.2 Trust a signature or seal over a IBAN

To trust a signature or seal over an IBAN, the Relying Party needs a mechanism to validate that the public key it uses to verify that signature or seal is trusted. OpenID4VP provides such mechanisms. However, additional details need to be analyzed to fully specify these mechanisms for IBANs within the EUDI Wallet ecosystem and the trust anchor for it. It is assumed that this will be part of a detailed specification from a standardization authority.

### 5.3 IBAN Provider Trusted List

For authenticating IBANs, trust anchors will be used that are present in an IBAN Issuer Provider Trusted List.

### 5.4 SD-JWT-compliant

IBAN is fully compliant with [OpenID4VP] and [SD-JWT VC].

## 6. References

- RFC-001: [Issue Verifiable Credential](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc001-issue-verifiable-credential.md)
- RFC-002: [Present Verifiable Credentials](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc002-present-verifiable-credentials.md)
- SD-JWT VC: [SD-JWT VC Specification](https://datatracker.ietf.org/doc/draft-ietf-oauth-sd-jwt-vc/)
- OpenID4VP: [OpenID4VP Specification](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html)
