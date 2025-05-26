# IDProofing ETSI119461 Data Rulebook

## Table of Contents

- [IDProofing ETSI119461 Data Rulebook](#idproofing-etsi119461-data-rulebook)
  - [Table of Contents](#table-of-contents)
  - [1. Introduction](#1-introduction)
    - [1.1 Scope](#11-scope)
    - [1.2 Background](#12-background)
    - [1.3 Goal of the IdProofing etsi 461 attestation](#13-goal-of-the-idproofing-etsi-461-attestation)
    - [1.4 Key words](#14-key-words)
    - [1.5 Terminology](#15-terminology)
  - [2. IDProofing Etsi 119.461 Issuance process](#2-idproofing-etsi-119461-issuance-process)
  - [3. IDProofing Etsi 119.461 Verification process](#3-idproofing-etsi-119461-verification-process)
  - [4. Revocation](#4-revocation)
  - [5. Identity attributes](#5-identity-attributes)
    - [5.1 Credential Subject attributes](#51-credential-subject-attributes)
    - [5.2 Identity document attributes](#52-identity-document-attributes)
  - [6. Trust infrastructure details](#6-trust-infrastructure-details)
  - [6. References](#6-references)

## 1. Introduction

*Disclaimer: This document is a draft and needs to be commented on and completed to be published as EWC WP4 T4.3 deliverable.*

The engagement of the wallet and the technical interface in order to authenticate the wallet/user and deliver the credential to the wallet is specified on RFC001. 

A rulebook instead is a document with an issuer centric perspective, so it aims to define which are the authentication/authorization allowed processes (regarding data required and its verification, checkings against open data registries) and which could be the functions in scope in order to collect and verify data properly. This data will be described in a data scheme.
Data schemes are the technical format (for now focusing on json scheme, but they could be in other formats).

Note: This rulebook will contribute for a definition of a generic specification for rulebooks, dedicated to issuers and specific sectorial opportunities in order to guarantee the trustworthiness of credentials.

### 1.1 Scope
This document focuses on the guidelines that an issuer should follow in order to manage the lifecycle of an attestation containing the identity attributes obtained by an identity proofing process compliant and certified by an accredited CAB, with the technical standard ETSI 119 461. It contains requirements specific to the identity and its issuance process. This rulebook covers the following topics: 
1. background and functional meaning of Identity Proofing credential compliant with etsi 119 461 specs, and its fields of applicability
2. a reference to identity attributes data scheme and to a generic issuance and verification process 
3. and Trust Infrastructure integration.

The ETSI standard provides different types of identification processes (in presence, based on a video call with an operator, or in self service mode) and authentication mechanisms (like eid or using a qualified signature): in this rulebook we focus on those identification processes based on identity documents because this represents a useful example of transposition from physical to digital world that could be applied in different scenarios. This is the case for instance of the PhotoID credential, that is a transposition of a passport to a credential form. 

### 1.2 Background
In EIDAS regulation, the identity proofing is not a trusted service itself, but it's a requirement to issue a qualified signature certificate or to provide all other trusted services. Similar requirements are present in different sectors for onboarding processes (like banking, insurance and so on) and require a set of evidences of applicant presence and liveness and his identity documents that have to be bound with.

In the EUDI wallet ecosystem the identity of the subject is represented by the PID, that's a attestation with level of identity proofing (LoIP, related to the strenght and trust level of the identification process) high, issued by Member States: of course there's a functional overlapping between an identity credential with PID provided by Member States. But in many business scenarios, PID data are not enough and a complete identity document, including biometric data, is required. The PID data scheme could be extended for other metadata bound to subject identity and its documents.

In the initial phase of the EUDIW era, we know that PID won't be supported by all wallets and in any case it will mandatory for interacting with Public Administration. Probably we can foresee two parallel scenarios: the first with a wallet and official PID activated, and a second with a wallet containing an identity credential equivalent according to regulation, enriched with the information that nowadays are managed in identity proofing processes and those ones that consume that identity assertion, all onboarding processes for qualified services and other business services.

The ETSI tech reference is a market standard that describes different usecases regarding the identification of an applicant, according to attended/unattended and remote/in presence processes, and provides some guidelines regarding antitampering requirements, functional and security requirements regarding liveness and presence of the applicant and the binding with his identity document. The outcome is an identity assertion that generally is used in QeS certificate issuance or in other contexts, like in banking account opening for AML and KYC processes, and of course allow eid and QeS usage to identify the user.
In Eidas v1 this technical standard was not mandatory, and it focuses on a level of Identity Proofing substantial, that was the requirement for the issuance of a QeS certificate.
In Eidas v2 the bar has been raised, so a second version of this technical standard has been written in order to specify the requirements for both LoIPs, substantial and high, improving the quality assurance of the identification process with specific and stricter data collection and verification requirements, both for biometric analysis and document validation. The aim of this document is to provide a valuable reference to Implementing Act definition regarding id profing in EIDAS 2.

### 1.3 Goal of the IdProofing etsi 461 attestation
Among all usecases addressed in the etsi 119 461, we would like to focus on processes based on biometric liveness checks and identity document acquisition, and keeping aside eid and signature recognition at this stage (These technical forms could not be ammitted in some business cases).
So the goals of such a credential are:
1. to provide an identity assertion, as result of an identification based on phisical presence of applicant with an id document
2. to extend identification data of the PID (as credential subject) with attribute of the identity document used in the process
3. to refer to a normative and technical reference that's a recognized market standard, and so it's validity could be portable on different business cases, across different sectors.

The level of Identity Proofing is of course an important qualitative element of this credential. Probably two different credential types should be addressed according to LoIP high or substantial, and this rely on the identification process only and its security requirements.
In order to meet a vast field of application, it could be useful and easier to keep a substantial level at this stage, that's the reference of the actual version of this tech standard, and that is compliant with EBA guidelines for AML in Europe. In banking scenario is applicable for Customer Due Diligence (CDD) or Know-Your-Customer (KYC) processes.
In any case this type of credential could be a valid example of QEAA, according to the fact that QTSPs have the ability to issue credentials with a LoIP high similar to the PID. 
PhotoId is an example of a process like this: the passport could be read by NFC (in this case the loip would be high) or through OCR (optical scanning) according to ETSI TS 119.461 requirements. 

Nonetheless in the ARF ch 6.6.3.9 "Relying Party Instance verifies or trusts User binding" [6] is well described the necessity of a Relying Party of a live and active presence verification bound to a PID presentation of the subject. This verification attestation could be offered by a QEAA to enforce the identification process, so different use cases could extend this basic proposal in order to meet business necessities.

The business value of this attestation must be seeked also in the ability to represent an enablement of the ecosystem of the wallet in a transition and coexistence phase prior to the consolidation of EUDIW trust model and PID availability to all EU citizens in private contexts. And of course it could enable the availability of different attributes and information than official PID ones, nowadays managed by actual available identification processes provided by local and EU QTSPs. So we assume that within the EUDIW framework, aside the PID there will be a collection of credential related to the official identity of the user like this one and all the others that for instance will represent a credential digital form of physical documents or eIDs. These credentials will be based on existing and certified identification or data verification processes that will enable the progressive adoption of EUDIW in existing business processes of everyday life.

This credential includes subject identity data and ID document data. Because requirements for identity proofing may vary in different countries and some (Q)TSPs may have different preferences, this may lead to different data schemes. A first proposal is provided in [ds014].

### 1.4 Key words

This document uses the capitalized key words 'SHALL', 'SHOULD', and 'MAY' as specified in [RFC 2119], i.e., to indicate requirements, recommendations, and options specified in this document.

In addition, 'must' (non-capitalized) is used to indicate an external constraint, i.e., a requirement that is not mandated by this document, but, for instance, by an external document. The word 'can' indicates a capability, whereas other words, such as 'will', and 'is' or 'are' are intended as statements of fact.

### 1.5 Terminology

This document uses terminology specified in Regulation (EU) 2024/1183.

## 2. IDProofing Etsi 119.461 Issuance process

In the EWC context, a generic attestation issuance process has been described by wallet providers in the pilots. Those controls and generic steps are described in [RFC-001](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc001-issue-verifiable-credential.md).

The authorization process is generally based on a webapplication/mobile solution that includes document data collection, liveness checks and binding of biometrics collected interacting with the applicant, with the photo of the document.
Regarding the acceptance criteria, antifraud countermeasures on defining the process, we refer to the ETSI 119 461 standard.
The registration process in the preauthorized or authorization flows must be performed by a QTSP with etsi 119461 certification. And the certification is identity proofing process specific. There's no public register about this.
So in order to ensure that the issuer is authorize to issue this cred type, there should be a public register or this enablement should be managed through the cred issuer authentication to the wallet.
In a theoretical way, the issuer should have a QTSP credential and an ETSI 119461 certification attestation credential on its wallet.

So we assume a basic process with:
1. identity document acquisition through camera (front and back side of document) or via NFC reading, with data extraction and antitampering controls on the document
2. liveness check and selfie photo acquisition
3. binding validation between applicant's selfie photo and id document photo

The authorization phase could have two more alternative controls
1. if the user has a PID, the PID could be verified against data collected from the document 
2. if the user has not a PID, the wallet attestation must be checked

The end date of validity of the document must be set on that one of the credential.

## 3. IDProofing Etsi 119.461 Verification process

In a verification process, the integrity and validity of the attestation shall be checked.
Whether a public document registry is available (and in this case should have been inquiried during the authorization/ identity proofing process), the validity of the identity document should be checked in the validation process.
All other checks against the trust framework should be done (regarding the issuer certificate).

## 4. Revocation
The credential lifecycle should follow the identity document one, so whether it's revoked by the gov authority, the credential must be revoked too.

## 5. Identity attributes

Identity attributes have been defined in the EWC deliverable [D4.6 Annex 5], that describes all EAAs in scope of EWC pilot.
Two objects are described in this attestation, and they follow the new structure of PID provided in the ARF 1.5.1 (rif ds012): 
1. credentialSubject: it represents the subject and his information that has been collected dureing the identification process; attribute names have been adapted to PID terminology 
2. documentInfo: evidence references of the identity document used in the identification process

The identity scheme is available in the EWC schemas and rulebooks repository: [idproofing etsi 461 data schema](https://github.com/EWC-consortium/eudi-wallet-rulebooks-and-schemas/blob/main/data-schemas/ds014-idproofing-etsi461.json).

Of course this model could be extended with optional attributes according to specific information that could be present in different eu states on the document. 

Namespace? we refer ebsi data model?

### 5.1 Credential Subject attributes
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

### 5.2 Identity document attributes

This document defines the following attributes related to the identity document used in the identification process.

| Property Name | Description | Required |
| ------------- | ----------- | -------- |
| document_type | Type of official identity document used in the attestation process | Yes |
| document_number | Unique identifier on the official identity document | Yes |
| issued_on | Date when the official identity document was issued | No |
| expires_on | Expiry date of the official identity document | Yes |

## 6. Trust infrastructure details

In the ARF 1.5, the following information for Pub-EAAs and QEAAs Providers is given. 
Pub-EAAs and QEAAs Providers are trusted entities responsible to: 

- Verify the identity of the EUDI Wallet User in compliance with LoA high requirements.
- Issue attestations to the EUDI Wallet in a harmonized common format.
- Make available information for Relying Parties to verify the validity of the attestation.

The Identity attestation SHALL follow the SD-JWT format. It is fully compliant with [OpenID4VP] and [SD-JWT VC].

A QTSP register is expected with all services that's entitled to offer and their certifications.


## 6. References

1. RFC-001: [Issue Verifiable Credential](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc001-issue-verifiable-credential.md)
2. RFC-002: [Present Verifiable Credentials](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc002-present-verifiable-credentials.md)
3. SD-JWT VC: [SD-JWT VC Specification](https://datatracker.ietf.org/doc/draft-ietf-oauth-sd-jwt-vc/)
4. OpenID4VP: [OpenID4VP Specification](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html)
5. D4.6 Annex 5 : [D4.6 Annex 5](https://nextcloud.ewc-consortium.eu/apps/files/files/131128?dir=/EWC/WP4%20Interoperability%20and%20infrastructure/Task%204.3/Deliverable%20D4.6/Annexes&openfile=true)
6. ARF v1.6 [https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/architecture-and-reference-framework-main](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/architecture-and-reference-framework-main)