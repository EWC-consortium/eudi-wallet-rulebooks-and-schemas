# Identity Data Rulebook

## Table of Contents

- [Identity Data Rulebook](#identity-data-rulebook)
  - [Table of Contents](#table-of-contents)
  - [1. Introduction](#1-introduction)
    - [1.1 Scope](#11-scope)
    - [1.2 Background](#12-background)
    - [1.3 Goal of the Identity attestation](#13-goal-of-the-identity-attestation)
    - [1.4 Key words](#14-key-words)
    - [1.5 Terminology](#15-terminology)
  - [2. Identity Issuance process](#2-identity-issuance-process)
  - [3. Identity Verification process](#3-identity-verification-process)
  - [4. Identity attributes](#4-identity-attributes)
    - [4.1 Credential Subject attributes](#41-credential-subject-attributes)
    - [4.2 Identity document attributes](#42-identity-document-attributes)
    - [4.3 Identity Proofing Process Compliance](#43-identity-proofing-process-compliance)
  - [5. Trust infrastructure details](#5-trust-infrastructure-details)
    - [5.1 Trust requirements on the identity attestation](#51-trust-requirements-on-the-identity-attestation)
    - [5.2 Trust a signature or seal over a Identity attestation](#52-trust-a-signature-or-seal-over-a-identity-attestation)
    - [5.3 Identity Provider Trusted List](#53-identity-provider-trusted-list)
    - [5.4 SD-JWT-compliant](#54-sd-jwt-compliant)
  - [6. References](#6-references)

## 1. Introduction

*Disclaimer: This document is a draft and needs to be commented on and completed to be published as EWC WP4 T4.3 deliverable. *
note: riportare metodologia e linee guida , like structure etsi
riferimento a loip, esti 461
### 1.1 Scope

This document is the Identity Data Rulebook. It contains requirements specific to the identity and its issuance process. This Rulebook covers the following topics: background and functional meaning of Identity credential, a reference to Identity attributes and to a generic issuance and verification process, and Trust Infrastructure details.

[Topic 10/23](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/blob/main/docs/annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-the-eudi-wallet) in the ARF 1.4 specifies that attestation must be issued in the [SD-JWT VC] format, among others. This rulebook supports the [SD-JWT VC] requirements.

### 1.2 Background

In the ARF and in eidas 2, the identity of the subject is represented by the PID, that's a attestation with level of identity proofing (LoIP, related to the strenght and trust level of the identification process) high, issued by MSs. The person identity data could be provided with different attribute schemas and different loip, according to identity proofing processes defined in eidas 1 and by national regulations or ETSI 119 461 v1 technical specification, that could have same LoIP high or LoIP substantial. 
So the "Identity" attestation will represent a technical form of an identity assertion, that includes a valid identity document used in the identification process, with LoIP high. 
*** Note** A new identity attestation with substantial level could be introduced.

### 1.3 Goal of the Identity attestation

This data set describes the credential used for attestating identity attributes, based on a strict manner of user authentication and data verification. This attestation is required at scenarios where Customer Due Diligence (CDD) or Know-Your-Customer (KYC) have to be performed by Relying Party (RP) based on e.g. legal background such as 4th AML (Directive (EU) 2015/849) or 5th AML (Directive (EU) 2018/843): “name, the month and year of birth, the nationality and the country of residence”.
The business value of this attestation must be seeked also in the ability to represent an enablement of the ecosystem of the wallet in a transition phase prior to the consolidation of EUDIW trust model and PID availability to all EU citizens. And of course it could enable the availability of different attributes and information than official PID ones, nowadays managed by actual available identification processes provided by local and EU QTSPs. So we assume that within the EUDIW framework, aside the PID there will be a collection of credential related to the official identity of the user like this one and all the others that for instance will represent a credential digital form of physical documents or eIDs. These credentials will be based on existing and certified identification or data verification processes that will enable the progressive adoption of EUDIW in existing business processes of everyday life.


### 1.4 Key words

This document uses the capitalized key words 'SHALL', 'SHOULD', and 'MAY' as specified in [RFC 2119], i.e., to indicate requirements, recommendations, and options specified in this document.

In addition, 'must' (non-capitalized) is used to indicate an external constraint, i.e., a requirement that is not mandated by this document, but, for instance, by an external document. The word 'can' indicates a capability, whereas other words, such as 'will', and 'is' or 'are' are intended as statements of fact.

### 1.5 Terminology

This document uses terminology specified in Regulation (EU) 2024/1183.

## 2. Identity Issuance process

Identity Proofing is not itself a qualified service among eidas 1 and 2, but it is a prerequisite for all qualified trust services. To comply with the Regulation, only QTSP are allowed to be the authoritative source of the identity attestation, and they can decide to use a EAAs provider to issue it on their behalf.

In the EWC context, a generic attestation issuance process has been described by wallet providers in the pilots. Those controls and generic steps are described in [RFC-001](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc001-issue-verifiable-credential.md).

## 3. Identity Verification process

It's not in scope of this rulebook to specify which caracteristics should have an identity proofing process, whether attended or not, remote or in presence, and so on. A market reference for this is the well known ETSI 119 461 standard, and in particular the version 2 that is going to be approved in Feb 2025 and that will be probably referred by the IA related to id proofing. 
The identity attestation requires a valid wallet attestation but could be indipendent by PID validation: it is based on a identification process and qualified by the level of identity proofing according eidas guidelines. 

## 4. Identity attributes

Identity attributes have been defined in the EWC deliverable [D4.6 Annex 5], that describes all EAAs in scope of EWC pilot.
Two objects are described in this attestation: 
1. credentialSubject: it represents the subject and his information that has been collected dureing the identification process; attribute names have been adapted to PID terminology 
2. documentInfo: evidence references of the identity document used in the identification process
3. identityProofingProcessCompliance: a set of generic strings that collects all regulatory and technical specifications against with the remote identification process is compliant with, that are ensured by the issuer

The identity schema is available in the EWC schemas and rulebooks repository: [identity data schema](https://github.com/EWC-consortium/eudi-wallet-rulebooks-and-schemas/blob/main/data-schemas/ds006-identity.json).

### 4.1 Credential Subject attributes
This document defines the following attributes related to the credential subject that has been identified through the process.
This table contains the name of the attribute, its description, and whether the attribute is required or not.

| Property Name | Description | Required |
| ------------- | ----------- | -------- |
| family_name | Family name given at the time of birth of the natural person | Yes |
| given_name | Current first name of the natural person | Yes |
| birth_date |  | Yes |
|  |  | Yes |
|  |  | Yes |
|  |  | Yes |
|  |  | Yes |

### 4.2 Identity document attributes

This document defines the following attributes related to the identity document used in the identification process.

| Property Name | Description | Required |
| ------------- | ----------- | -------- |
| document_type | Type of official identity document used in the attestation process | Yes |
| document_number | Unique identifier on the official identity document | Yes |
| issued_on | Date when the official identity document was issued | No |
| expires_on | Expiry date of the official identity document | Yes |

### 4.3 Identity Proofing Process Compliance

This is a list of national regulations, technical specifications, european references (for instance Eidas 2 and its implementing Acts) according to which the identification process and service provider are compliant with. This is optional, but qualifies the identity attestation itself and its compliance against regulation when consumed in sectorial processes, like the AML process in banking sector.
As now this is represented by a generic string array, but of course could be structured qithin a compliance framework rappresentation.

## 5. Trust infrastructure details

In this chapter, trust requirements and general considerations regarding the identity attestation itself are described.

### 5.1 Trust requirements on the identity attestation

In the ARF 1.4, the following information for Pub-EAAs and QEAAs Providers is given.

Pub-EAAs and QEAAs Providers are trusted entities responsible to:

- Verify the identity of the EUDI Wallet User in compliance with LoA high requirements.
- Issue attestations to the EUDI Wallet in a harmonized common format.
- Make available information for Relying Parties to verify the validity of the attestation.

The Identity attestation SHALL follow the SD-JWT format.

### 5.2 Trust a signature or seal over a Identity attestation

NOTE Validation mechanism should be indipendent by the specific rulebook

### 5.3 Identity Provider Trusted List

For authenticating , trust anchors will be used that are present in an Identity issuer Provider Trusted List.

### 5.4 SD-JWT-compliant

Identity is fully compliant with [OpenID4VP] and [SD-JWT VC].

## 6. References

- RFC-001: [Issue Verifiable Credential](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc001-issue-verifiable-credential.md)
- RFC-002: [Present Verifiable Credentials](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc002-present-verifiable-credentials.md)
- SD-JWT VC: [SD-JWT VC Specification](https://datatracker.ietf.org/doc/draft-ietf-oauth-sd-jwt-vc/)
- OpenID4VP: [OpenID4VP Specification](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html)
- D4.6 Annex 5 : [D4.6 Annex 5](https://nextcloud.ewc-consortium.eu/apps/files/files/131128?dir=/EWC/WP4%20Interoperability%20and%20infrastructure/Task%204.3/Deliverable%20D4.6/Annexes&openfile=true)
