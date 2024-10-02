# Legal Person Identification Data (LPID) Rulebook

5 September 2024

updated 17 September 2024

# Table of Contents

[Legal Person Identification Data (LPID) Rulebook]
(#legal-person-identification-data-lpid-rulebook)

1. [Introduction](#introduction)

1.1 [Scope ](#scope)

1.2 [Background](#background)

1.3 [Goal of the LPID attestation](#goal-of-the-lpid-attestation)

1.4 [Key words](#key-words)

1.5 [Terminology](#terminology)

2 [LPID Issuance process](#lpid-issuance-process)

3 [LPID attributes](#lpid-attributes)

4 [Trust infrastructure details](#trust-infrastructure-details)

4.1 [Trust requirements on the LPID attestation from the perspective of
company registration offices as authentic sources for the LPID](#trust-requirements-on-the-lpid-attestation-from-the-perspective-of-company-registration-offices-as-authentic-sources-for-the-lpid)

4.2 [Trust a signature or seal over a LPID](#trust-a-signature-or-seal-over-a-lpid)

4.3 [LPID Provider Trusted List](#lpid-provider-trusted-list)

4.4 [SD-JWT-compliant PIDs](#sd-jwt-compliant-pids)

5 [References](#references)

# 1 Introduction

## 1.1 Scope

This document is the Legal Person Identification Data (LPID) Rulebook.
It contains requirements specific to the LPID and its issuance process.
This LPID Rulebook contains the following topics: background of LPID, a
reference to LPID attributes, a reference to the generic LPID issuance
process, and Trust Infrastructure details.

\[[Topic
10](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/blob/main/docs/annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-the-eudi-wallet)/[23](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/blob/main/docs/annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-the-eudi-wallet)\]
in the ARF 1.4 specifies that PID must be issued in the \[SD-JWT VC\]
format amongst other. This rulebook supports the \[SD-JWT VC\]
requirements.

## 1.2 Background

The LPID is defined in the Regulation (EU) 2024/1183 as "*"person
identification data" means a set of data that is issued in accordance
with Union or national law and that enables the establishment of the
identity of a natural or legal person, or of a natural person
representing another natural person or a legal person*. "

The Legal PID is Person Identification Data for legal persons. The LPID
attributes and generic LPID issuance process have been agreed upon by
all company registration offices in the pilot for the EWC and are the
basis for a common LPID schema. The Legal PID will henceforth be
abbreviated as \"LPID\".

## 1.3 Goal of the LPID attestation

The goal of the LPID attestation is for relying parties to ensure trust
in an organization that is the Holder of the LPID by

1\) verifying the integrity of the LPID. This could for example be done
by verifying trusted lists or technical controls against schema.

2\) validating the LPID. Validating includes checking that the LPID is
not altered or revoked

The LPID ensures those two factors and therefore that a Legal person
EUDI Wallet Instance is trustworthy. 

## 1.4 Key words

This document uses the capitalized key words 'SHALL', 'SHOULD' and 'MAY'
as specified in \[RFC 2119\], i.e., to indicate requirements,
recommendations and options specified in this document.

In addition, 'must' (non-capitalized) is used to indicate an external
constraint, i.e., a requirement that is not mandated by this document,
but, for instance, by an external document. The word 'can' indicates a
capability, whereas other words, such as 'will', and 'is' or 'are' are
intended as statements of fact.

## 1.5 Terminology

This document uses terminology specified in Regulation (EU) 2024/1183.

# 2 LPID Issuance process

A generic LPID Issuance process has been described by business
registries in the EWC pilot. While different business registries have
national processes, there is an agreement on the controls that need to
be done before issuing an LPID. Those controls and generic steps are
described in RFC-005 chapter 3.0 LPID Issuance process:

[eudi-wallet-rfcs/ewc-rfc005-issue-legal-person-identification-data.md
at main · EWC-consortium/eudi-wallet-rfcs ·
GitHub](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc005-issue-legal-person-identification-data.md)

# 3 LPID attributes

LPID attributes have been decided together by business registries in the
EWC pilot.

The LPID SHALL only have two mandatory LPID attributes, the legal person
identifier in form of the EUID, and the legal person name(s).

The reason is that the LPID would have to be revoked more often if the
LPID attestation would include more attributes which could change over
time, and since the LPID is the basis for trust in an organization and
is being exchanged in all attestation transactions, this would disturb
business processes too often. Other legal person attributes, such as
other types of IDs or signatories, can instead be issued in other
separate attestations.

The LPID attributes are described in a table in chapter 5.10.3 in
RFC-005:
[eudi-wallet-rfcs/ewc-rfc005-issue-legal-person-identification-data.md
at main · EWC-consortium/eudi-wallet-rfcs ·
GitHub](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc005-issue-legal-person-identification-data.md)

# 4 Trust infrastructure details

In this chapter, trust requirements and general considerations regarding
the LPID attestation itself are described.

## 4.1 Trust requirements on the LPID attestation from the perspective of company registration offices as authentic sources for the LPID

In the ARF 1.2. the following information for PID Providers is given.

PID Providers are trusted entities responsible to:

● verify the identity of the EUDI Wallet User in compliance with LoA
high requirements,

● issue PID to the EUDI Wallet in a harmonised common format and

● make available information for Relying Parties to verify the validity
of the PID.

The LPID SHALL contain the qualified electronic signature or qualified
electronic seal of the issuing body and adhere to the legal requirements
defined in Annex VII of the Regulation (EU) 2024/1183.

The LPID SHALL follow the SD-JWT format.

It SHALL not be possible to log into company registers solely with the
LPID, since procedures legally require an individual person to act.

LPID Issuers SHALL follow the LPID requirements and trust mechanisms
defined by Authentic Sources on national level.

Authentic Sources that are company registration offices need to accept
each other's PUB-EAA attestations according to the regulation.
Therefore, common legal trust mechanisms need to be stablished in order
for the trust ecosystem to be trustworthy:

-   The LPID unique identifier SHALL be unique and agreed upon on EU and
    EES level.

-   There SHALL be one common schema for the LPID which is accepted by
    all company registries offices.

-   Only mandatory metadata and attributes SHALL be present in the LPID
    attestations.

-   The LPID attestation SHALL be an atomic attestation, i.e. it cannot
    be enriched with other data, and selective disclosure is not
    possible.

-   The LPID SHALL be in a machine-readable format defined in the ARF
    during its whole lifecycle.

-   The LPID SHALL be in a format that can scale to additional/new legal
    forms.

-   The LPID SHALL apply for all legal persons.

-   The issuer of the LPID SHALL be responsible for its revocation.

## 4.2 Trust a signature or seal over a LPID

To trust a signature or seal over an LPID, the Relying Party needs a
mechanism to validate that the public key it uses to verify that
signature or seal is trusted. OpenID4VP provides such mechanisms.
However, additional details need to be analysed to fully specify these
mechanisms for LPIDs within the EUDI Wallet ecosystem. It is assumed
that this will be part of a detailed specification from a standard
organization.

## 4.3 LPID Provider Trusted List

For authenticating LPIDs, trust anchors will be used that are present in
a LPID Provider Trusted List.

## 4.4 SD-JWT-compliant PIDs

LPID is fully compliant with \[OpenID4VP\] and \[SD-JWT VC\].

# 5 References

RFC-005:
[eudi-wallet-rfcs/ewc-rfc005-issue-legal-person-identification-data.md
at main · EWC-consortium/eudi-wallet-rfcs ·
GitHub](https://github.com/EWC-consortium/eudi-wallet-rfcs/blob/main/ewc-rfc005-issue-legal-person-identification-data.md)

\[SD-JWT VC\]:
<https://datatracker.ietf.org/doc/draft-ietf-oauth-sd-jwt-vc/>

\[OpenID4VP\]:
<https://openid.net/specs/openid-4-verifiable-presentations-1_0.html>
