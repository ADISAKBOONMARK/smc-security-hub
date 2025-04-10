Title: EEA EthTrust Security Levels Specification version 2

URL Source: https://entethalliance.org/specs/ethtrust-sl/

Markdown Content:
[Jump to Table of Contents](https://entethalliance.org/specs/ethtrust-sl/#toc) [Pop Out Sidebar](https://entethalliance.org/specs/ethtrust-sl/#toc)

![Image 1: EEA](https://entethalliance.org/specs/ethtrust-sl/eea_logo.svg)

EEA Specification 13 December 2023
----------------------------------

This Version:

[https://entethalliance.org/specs/ethtrust-sl/v2/](https://entethalliance.org/specs/ethtrust-sl/v2/)

Latest editor's draft:

[https://entethalliance.github.io/eta-registry/security-levels-spec.html](https://entethalliance.github.io/eta-registry/security-levels-spec.html)

Editor:

Previous release:

[https://entethalliance.org/specs/ethtrust-sl/v1/](https://entethalliance.org/specs/ethtrust-sl/v1/)

Latest release URL:

[https://entethalliance.org/specs/ethtrust-sl/](https://entethalliance.org/specs/ethtrust-sl/)

Contributors to this version:

Andrew Anderson (OpenZeppelin), Ismael Arribas (LACChain), Gianfranco Bazzani (OpenZeppelin), Kenan Bešić (ChainSecurity), Christopher Cordi (Individual), Stepan Chekhovskoi / Степан Чековской (Hacken), Jan Gorzny (Quantstamp), Opal Graham (CertiK), George Kobakhidze (ConsenSys), Michael Lewellen (OpenZeppelin), Dominik Muhs (ConsenSys), Carlo Parisi (Hacken), Anton Permenev (ChainSecurity), Marta Piekarska (Consensys), Przemek Siemion (Banco Santander), Grant Southey (ConsenSys), David Tarditi (CertiK / Individual), Michael Theriault (DTCC), Ben Towne (SAE), Morgan Weaver (OpenZeppelin), Gal Weizman (ConsenSys), Mehdi Zerouali

Copyright © 2020-2023 [Enterprise Ethereum Alliance](https://entethalliance.org/).

* * *

Abstract
--------

This document defines the requirements for [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified), a set of certifications that a smart contract has been reviewed and found not to have a defined set of security vulnerabilities.

Status of This Document
-----------------------

_This section describes the status of this document at the time of its publication. Newer documents may supersede this document._

This document is an EEA Specification, published by the Enterprise Ethereum Alliance, Inc.

This specification is licensed by the Enterprise Ethereum Alliance, Inc. (EEA) under the terms of the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0) \[[License](https://entethalliance.org/specs/ethtrust-sl/#bib-license "Apache license version 2.0")\] Unless otherwise explicitly authorised in writing by the EEA, you can only use this specification in accordance with those terms.

Unless required by applicable law or agreed to in writing, this specification is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

This is the second version of the EEA EthTrust Security Levels Specification. This specification has been reviewed and approved for publishing by the EEA EthTrust Security Levels Working Group, and the EEA Board.

This version **supersedes** [version 1](https://entethalliance.org/specs/ethtrust-sl/v1/) of this Specification.

Please send any comments other than vulnerability notifications to the EEA through [https://entethalliance.org/contact/](https://entethalliance.org/contact/), or as issues via the [EthTrust-public GitHub Repository](https://github.com/EntEthAlliance/eta-registry/issues/). To notify EEA of vulnerabilities, please follow the procedures outlined in [§ 1.4 Feedback and new vulnerabilities](https://entethalliance.org/specs/ethtrust-sl/#sec-notifying-new-vulnerabilities).

The Working Group _expects_ at the time of publication to publish the next version of the Specification in 2025.

Table of Contents
-----------------

1.  [1\. Introduction](https://entethalliance.org/specs/ethtrust-sl/#sec-introduction)
    1.  [1.1 How to read this specification](https://entethalliance.org/specs/ethtrust-sl/#sec-reading-the-spec)
        1.  [1.1.1 Overview of this Document](https://entethalliance.org/specs/ethtrust-sl/#sec-document-overview)
        2.  [1.1.2 Typographic Conventions](https://entethalliance.org/specs/ethtrust-sl/#sec-typographic-conventions)
        3.  [1.1.3 How to Read a Requirement](https://entethalliance.org/specs/ethtrust-sl/#sec-reading-requirements)
            1.  [1.1.3.1 Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#sec-overriding-requirements)
            2.  [1.1.3.2 Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#sec-related-requirements)
    2.  [1.2 Why Certify Contracts?](https://entethalliance.org/specs/ethtrust-sl/#sec-intro-why-certify-contracts)
    3.  [1.3 Developing Secure Smart Contracts](https://entethalliance.org/specs/ethtrust-sl/#sec-intro-developing-secure-contracts)
    4.  [1.4 Feedback and new vulnerabilities](https://entethalliance.org/specs/ethtrust-sl/#sec-notifying-new-vulnerabilities)
2.  [2\. Conformance](https://entethalliance.org/specs/ethtrust-sl/#conformance)
    1.  [2.1 Conformance Claims](https://entethalliance.org/specs/ethtrust-sl/#sec-conformance-claims)
    2.  [2.2 Who can offer EEA EthTrust Certification?](https://entethalliance.org/specs/ethtrust-sl/#who-can-audit)
    3.  [2.3 Identifying what is certified](https://entethalliance.org/specs/ethtrust-sl/#sec-source-and-contracts)
3.  [3\. Security Considerations](https://entethalliance.org/specs/ethtrust-sl/#sec-security-considerations)
    1.  [3.1 Smart Contracts in context - broader considerations](https://entethalliance.org/specs/ethtrust-sl/#sec-eth-broader-considerations)
    2.  [3.2 Upgradable Contracts](https://entethalliance.org/specs/ethtrust-sl/#sec-proxy-contract-considerations)
    3.  [3.3 Oracles](https://entethalliance.org/specs/ethtrust-sl/#sec-oracle-considerations)
    4.  [3.4 External Interactions and Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#sec-reentrancy-considerations)
    5.  [3.5 Signature Mechanisms](https://entethalliance.org/specs/ethtrust-sl/#sec-signature-considerations)
    6.  [3.6 Gas and Gas Prices](https://entethalliance.org/specs/ethtrust-sl/#sec-gas-considerations)
    7.  [3.7 MEV (Maliciously Extracted Value)](https://entethalliance.org/specs/ethtrust-sl/#sec-mev-considerations)
    8.  [3.8 Source code, pragma, and compilers](https://entethalliance.org/specs/ethtrust-sl/#sec-source-compiler-considerations)
    9.  [3.9 Contract Deployment](https://entethalliance.org/specs/ethtrust-sl/#sec-deployment-considerations)
    10.  [3.10 Post-deployment Monitoring](https://entethalliance.org/specs/ethtrust-sl/#sec-realtime-monitoring-considerations)
    11.  [3.11 Network Upgrades](https://entethalliance.org/specs/ethtrust-sl/#sec-netupgrades-considerations)
4.  [4\. EEA EthTrust Security Levels](https://entethalliance.org/specs/ethtrust-sl/#sec-levels)
    1.  [4.1 Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-one)
        1.  [4.1.1 Text and homoglyphs](https://entethalliance.org/specs/ethtrust-sl/#sec-1-unicode)
        2.  [4.1.2 External Calls](https://entethalliance.org/specs/ethtrust-sl/#sec-1-external-calls)
        3.  [4.1.3 Improved Compilers](https://entethalliance.org/specs/ethtrust-sl/#sec-1-compile-improvements)
        4.  [4.1.4 Compiler Bugs](https://entethalliance.org/specs/ethtrust-sl/#sec-1-compiler-bugs)
    2.  [4.2 Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-two)
        1.  [4.2.1 Text and homoglyph attacks](https://entethalliance.org/specs/ethtrust-sl/#sec-2-unicode)
        2.  [4.2.2 External Calls](https://entethalliance.org/specs/ethtrust-sl/#sec-2-external-calls)
        3.  [4.2.3 Documented Defensive Coding](https://entethalliance.org/specs/ethtrust-sl/#sec-2-special-code)
        4.  [4.2.4 Signature Management](https://entethalliance.org/specs/ethtrust-sl/#sec-2-signature-requirements)
        5.  [4.2.5 Security Level \[M\] Compiler Bugs and Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#sec-level-2-compiler-bugs)
    3.  [4.3 Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-three)
        1.  [4.3.1 Documentation requirements](https://entethalliance.org/specs/ethtrust-sl/#sec-3-documentation)
        2.  [4.3.2 Access Control](https://entethalliance.org/specs/ethtrust-sl/#sec-3-access-control)
    4.  [4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations)
5.  [A. Additional Information](https://entethalliance.org/specs/ethtrust-sl/#sec-additional-information)
    1.  [A.1 Defined Terms](https://entethalliance.org/specs/ethtrust-sl/#sec-definitions)
    2.  [A.2 Summary of Requirements](https://entethalliance.org/specs/ethtrust-sl/#sec-summary-of-requirements)
    3.  [A.3 Acknowledgments](https://entethalliance.org/specs/ethtrust-sl/#sec-acknowledgments)
    4.  [A.4 Changes](https://entethalliance.org/specs/ethtrust-sl/#sec-changes)
        1.  [A.4.1 New Requirements](https://entethalliance.org/specs/ethtrust-sl/#new-requirements)
        2.  [A.4.2 Updated Requirements](https://entethalliance.org/specs/ethtrust-sl/#updated-requirements)
        3.  [A.4.3 Requirements removed](https://entethalliance.org/specs/ethtrust-sl/#requirements-removed)
6.  [B. References](https://entethalliance.org/specs/ethtrust-sl/#references)
    1.  [B.1 Normative references](https://entethalliance.org/specs/ethtrust-sl/#normative-references)
    2.  [B.2 Informative references](https://entethalliance.org/specs/ethtrust-sl/#informative-references)

1\. Introduction[](https://entethalliance.org/specs/ethtrust-sl/#sec-introduction)
----------------------------------------------------------------------------------

This document is the second version of the [**EEA EthTrust Security Levels Specification**](https://entethalliance.org/specs/ethtrust-sl/), that defines the requirements for granting [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) to a smart contract written in Solidity.

This version **supersedes** the first version of this specification, the [EEA EthTrust Security Levels Specification version 1](https://entethalliance.org/specs/ethtrust-sl/v1/) \[[EthTrust-sl-v1](https://entethalliance.org/specs/ethtrust-sl/#bib-ethtrust-sl-v1 "EEA EthTrust Security Levels Specification. Version 1")\].

[EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) is a claim by a security reviewer that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) is not vulnerable to a number of known attacks or failures to operate as expected, based on the reviewer's assessment against those specific requirements.

No amount of security review can guarantee that a smart contract is secure against **all possible** vulnerabilities, as explained in [§ 3\. Security Considerations](https://entethalliance.org/specs/ethtrust-sl/#sec-security-considerations). However reviewing a smart contract according to the requirements in this specification provides assurance that it is not vulnerable to a known set of potential attacks.

This assurance is backed not only by the reputation of the reviewer, but by the collective reputations of the multiple experts in security from many competing organizations, who collaborated within the EEA to ensure this specification defines protections against a real and significant set of known vulnerabilities.

### 1.1 How to read this specification[](https://entethalliance.org/specs/ethtrust-sl/#sec-reading-the-spec)

_This section is non-normative._

This section describes how to understand this specification, including the conventions used for examples and requirements, core concepts, references, informative sections, etc.

#### 1.1.1 Overview of this Document[](https://entethalliance.org/specs/ethtrust-sl/#sec-document-overview)

Broadly, the document is structured as follows:

Front matter

Basic information about the document - authors, copyright, etc.

Conformance section

What it means and looks like to claim conformance to this specification.

Security Considerations

A general introduction to key security concepts relevant to Smart Contracts.

EthTrust Security Levels

The core of the document. Requirements that security reviews should meet, grouped by levels and then thematically.

Additional Information

*   A glossary of terms defined.
*   A summary of each requirement that can be used as a checklist for readers familiar with the details.
*   A summary of substantial changes made since the previous release version.
*   Acknowledgements

References

Further reading, including normative references necessary to the requirements and informative references that expand on topics described in the specification.

This specification is accompanied by a [Checklist](https://entethalliance.org/specs/ethtrust-sl/checklist.html), that lists the requirements in a handy table. That checklist can be used to help developers or reviewers familiar with the specification to quickly remind themselves of each individual requirement and track whether they have tested it. In case of any discrepancy, the normative text is in this specification document.

#### 1.1.2 Typographic Conventions[](https://entethalliance.org/specs/ethtrust-sl/#sec-typographic-conventions)

The structure and formatting of requirements is described in detail in [§ 1.1.3 How to Read a Requirement](https://entethalliance.org/specs/ethtrust-sl/#sec-reading-requirements).

Examples are given in some places. These are not requirements and are not normative. They are distinguished by a background with a border and generally a title, like so:

Some examples are given of vulnerable code, or what NOT to do. It is a very bad idea to copy such examples into production code. These are marked as warnings:

Warning

Definitions of terms are formatted Like This and subsequent references to defined terms are rendered as links [Like This](https://entethalliance.org/specs/ethtrust-sl/#dfn-like-this).

References to other documents are links to the relevant entry in the [§ B. References](https://entethalliance.org/specs/ethtrust-sl/#references), within square brackets: \[[CWE](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe "Common Weakness Enumeration")\].

Links to requirements begin with a [Security Level](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-levels): **\[S\]**, **\[M\]** or **\[Q\]**, and [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations) begin with **\[GP\]**. They then include the requirement or good practice name. They are rendered as links in bold type:

Example of a link to [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

Variables, introduced to be described further on in a statement or requirement, are formatted as var.

Occasional explanatory notes, presented as follows, are not normative and do not specify formal requirements.

Note: Notes are explanatory

#### 1.1.3 How to Read a Requirement[](https://entethalliance.org/specs/ethtrust-sl/#sec-reading-requirements)

The core of this document is the requirements, that collectively define [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified).

Requirements have

*   a [Security Level](https://entethalliance.org/specs/ethtrust-sl/#sec-levels) that is one of "[**\[S\]**](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-one)", "[**\[M\]**](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-two)", or "[**\[Q\]**](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-three)",
*   a name,
*   a link (identified with "🔗") to its URL, and
*   a statement of what _MUST_ be achieved to meet the requirement.

Some requirements at the same [Security Level](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-levels) are grouped in a subsection, because they are related to a particular theme or area of potential attacks.

Requirements are followed by explanation, that can include why the requirement is important, how to test for it, links to [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) and [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements), test cases, and links to other useful information.

As well as Requirements, this document includes some [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations), that are formatted similarly with an apparent Security Level of "**\[GP\]**". It is not necessary to implement these in order to conform to the specification, but if carefully implemented they can improve the security of smart contracts.

The following requirement:

is a [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirement, denoted by the "**\[S\]**" before its name. Its name is **Compiler Bug SOL-2022-5 with `.push()`**. Its URL **in this version 2 of the specification**, as linked from the " 🔗 " character, is [https://entethalliance.org/specs/ethtrust-sl/v2/#req-1-compiler-SOL-2022-5-push](https://entethalliance.org/specs/ethtrust-sl/v2/#req-1-compiler-SOL-2022-5-push).

The statement of requirement is:

> [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies `bytes` arrays from `calldata` or `memory` whose size is not a multiple of 32 bytes, and has an empty `.push()` instruction that writes to the resulting array, _MUST NOT_ use a Solidity compiler version older than 0.8.15.

Following the requirement is a brief explanation of the relevant vulnerability, and links to further information.

Note

Good Practices are formatted the same way as Requirements, with an apparent level of **\[GP\]**. However, as explained in [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations) meeting them is not necessary and does not in itself change conformance to this specification.

##### 1.1.3.1 Overriding Requirements[](https://entethalliance.org/specs/ethtrust-sl/#sec-overriding-requirements)

For some requirements, the statement will include an alternative condition, introduced with the keyword **unless**, that identifies one or more Overriding Requirements. These are requirements at a higher Security Level, that can be satisfied to achieve conformance if the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) does not meet the lower-level requirement as stated. In some cases it is necessary to meet more than one [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) to meet the requirement they override. In this case, the requirements are described as a Set of Overriding Requirements. It is necessary to meet all the requirements in a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) in order to meet the requirement that is overriden.

In a number of cases, there will be more than one [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) or [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) that can be met in order to satisfy a given requirement. For example, it is sometimes possible to meet a [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) Requirement either by directly fulfilling it, or by meeting a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) at [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m), or by meeting a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) at [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q).

[Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) enable simpler testing for common simple cases. For more complex [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), that uses features which need to be handled with extra care to avoid introducing vulnerabilities, they ensure such usage is appropriately checked.

In a typical case of an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for a [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirement, they apply in relatively unusual cases or where automated systems are generally unable to verify that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) meets the requirement. Further verification of the applicable [Overriding Requirement(s)](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) can determine that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) is using a feature appropriately, and therefore passes the [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirement.

If there is not an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for a requirement that the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) does not meet, the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) is not eligible for [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified). However, even for such cases, note the Recommended Good Practice [**\[GP\] Meet as Many Requirements as Possible**](https://entethalliance.org/specs/ethtrust-sl/#req-R-meet-all-possible); meeting any requirements in this specification will improve the security of smart contracts.

In the following requirement:

*   the Security Level is "**\[S\]**",
*   the name is "**No `tx.origin`**", and
*   the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) is "[**\[Q\] Verify `tx.origin` Usage**](https://entethalliance.org/specs/ethtrust-sl/#req-3-verify-tx.origin)".

The requirement that the tested code does not contain a `tx.origin` instruction is automatically verifiable.

[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that does have a valid use for `tx.origin`, as decided by the auditor, and meets the Security Level \[Q\] [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[Q\] Verify `tx.origin` Usage**](https://entethalliance.org/specs/ethtrust-sl/#req-3-verify-tx.origin) conforms to this Security Level \[S\] requirement.

Requirements that are an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for another, or are part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements), expicitly mention that:

### 1.2 Why Certify Contracts?[](https://entethalliance.org/specs/ethtrust-sl/#sec-intro-why-certify-contracts)

_This section is non-normative._

A number of smart contracts that power decentralized applications on Ethereum have been found to contain security issues, and today it is often difficult or impossible in practice to see how secure an address or contract is before initiating a transaction. The Defi space in particular has exploded with a flurry of activity, with individuals and organizations approving transactions in token contracts, swapping tokens, and adding liquidity to pools in quick succession, sometimes without stopping to check security. For Ethereum to be trusted as a transaction layer, enterprises storing critical data or financial institutions moving large amounts of capital need a clear signal that a contract has had appropriate security audits.

Reviewing early, in particular before production deployment, is especially important in the context of blockchain development because the costs in time, effort, funds, and/or credibility, of attempting to update or patch a smart contract after deployment are generally much higher than in other software development contexts.

This smart contract security standard is designed to increase confidence in the quality of security audits for smart contracts, and thus to raise trust in the Ethereum ecosystem as a global settlement layer for all types of transactions across all types of industry sectors, for the benefit of the entire Ethereum ecosystem.

Certification also provides value to the actual or potential users of a smart contract, and others who could be affected by the use or abuse of a particular smart contract but are not themselves direct users. By limiting exposure to certain known weaknesses through [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified), these stakeholders benefit from reduced risk and increased confidence in the security of assets held in or managed by the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

This assurance is not complete; for example it relies on the competence and integrity of the auditor issuing the certification. That is generally not completely knowable. Professional reputations can change based on subsequent performance of [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code). This is especially so if the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) becomes sufficiently high-profile to motivate exploitation of any known weaknesses remaining after certification.

Finally, smart contract developers and ecosystem stakeholders receive value when others (including direct competitors) complete the certification process, because it means those other contracts are less likely to generate exploitation-related headlines which can lead to negative perceptions of Ethereum technology as insecure or high risk, by the general public including business leaders, prospective customers/users, regulators, and investors.

The value of smart contract security certification is in some ways analogous to the certification processes applicable to aircraft parts. Most directly, it helps reduce risks for part manufacturers and the integrators who use those parts as components of a more complex structure, by providing assurance of a minimum level of quality. Less directly, these processes significantly reduce aviation accidents and crashes, saving lives and earning the trust of both regulators and customers who consider the safety and risk of the industry and its supporting technology as a whole. Many safety certification processes began as voluntary procedures created by a manufacturer, or specified and required by a consortium of customers representing a significant fraction of the total market. Having proven their value, some of these certification processes are now required by law, to protect the public (including ground-based bystanders).

We hope the value of the certification process motivates frequent use, and furthers development of automated tools that can make the evaluation process easier and cheaper.

As new security vulnerabilities, issues in this specification, and challenges in implementation are discovered, we hope they will lead to both change requests and increased participation in the [Enterprise Ethereum Alliance](https://entethalliance.org/)'s [EthTrust Security Levels Working Group](https://entethalliance.org/groups/EthTrust/) or its successors, responsible for developing and maintaining this specification.

### 1.3 Developing Secure Smart Contracts[](https://entethalliance.org/specs/ethtrust-sl/#sec-intro-developing-secure-contracts)

_This section is non-normative._

Security issues that this specification calls for checking are not necessarily obvious to smart contract developers, especially relative newcomers in a quickly growing field.

By walking their own code through the certification process, even if no prospective customer requires it, a smart contract developer can discover ways their code is vulnerable to known weaknesses and fix that code prior to deployment.

Developers ought to make their code as secure as possible. Instead of aiming to fulfil only the requirements to conform at a particular Security Level, ensuring that code implements as many requirements of this specification as possible, per [**\[GP\] Meet as Many Requirements as Possible**](https://entethalliance.org/specs/ethtrust-sl/#req-R-meet-all-possible), helps ensure the developer has considered all the vulnerabilities this specfication addresses.

Aside from the obvious reputational benefit, developers will learn from this process, improving their understanding of potential weaknesses and thus their ability to avoid them completely in their own work.

For an organization developing and deploying smart contracts, this process reduces the amount of work required for security reviews, and risks both to their credibility, and to their assets and other capital.

### 1.4 Feedback and new vulnerabilities[](https://entethalliance.org/specs/ethtrust-sl/#sec-notifying-new-vulnerabilities)

The Working Group seeks feedback on this specification: Implementation experience, suggestions to improve clarity, or questions if a particular section or requirement is difficut to understand.

We also explicitly want feedback about the use of a standard machine-readable format for [Valid Conformance Claims](https://entethalliance.org/specs/ethtrust-sl/#dfn-valid-conformance-claim), whether being suitable for storing on a blockchain is important for such a format, and for other use cases.

EEA members are encouraged to provide feedback through joining the Working Group. Anyone can also provide feedback through the a href="https://github.com/EntEthAlliance/eta-registry/issues/"\>EthTrust-public GitHub Repository, or via EEA's contact pages at [https://entethalliance.org/contact/](https://entethalliance.org/contact/) and it will be forwarded to the Working Group as appropriate.

We expect that new vulnerabilities will be discovered after this specification is published. To ensure that we consider them for inclusion in a revised version, we welcome notification of them. EEA has created a specific email address to let us know about new security vulnerabilities: [security-notices@entethalliance.org](mailto:security-notices@entethalliance.org). Information sent to this address _SHOULD_ be sufficient to identify and rectify the problem described, and _SHOULD_ include references to other discussions of the problem. It will be assessed by EEA staff, and then forwarded to the Working Group to address the issue.

When these vulnerabilities affect the Solidity compiler, or suggest modifications to the compiler that would help mitigate the problem, the Solidity Development community _SHOULD_ be notified, as described in \[[solidity-reports](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-reports "Reporting a Vulnerability, in Security Policy")\].

2\. Conformance[](https://entethalliance.org/specs/ethtrust-sl/#conformance)
----------------------------------------------------------------------------

The key words _MAY_, _MUST_, _MUST NOT_, _RECOMMENDED_, and _SHOULD_ in this document are to be interpreted as described in [BCP 14](https://tools.ietf.org/html/bcp14) \[[RFC2119](https://entethalliance.org/specs/ethtrust-sl/#bib-rfc2119 "Key words for use in RFCs to Indicate Requirement Levels")\] \[[RFC8174](https://entethalliance.org/specs/ethtrust-sl/#bib-rfc8174 "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words")\] when, and only when, they appear in all capitals, as shown here.

This specification defines a number of requirements. As described in [§ 1.1.3 How to Read a Requirement](https://entethalliance.org/specs/ethtrust-sl/#sec-reading-requirements), each requirement has a Security Level (\[S\], \[M\] or \[Q\]), and a statement of the requirement that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ meet.

In order to achieve [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at a specific Security Level, the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ meet **all the requirements for that Security Level**, including all the requirements for lower Security Levels. Some requirements can either be met directly, or by meeting one or more [Overriding requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) that mean the requirement is considered met.

This document does not create an affirmative duty of compliance on any party, though requirements to comply with it could be created by contract negotiations or other processes with prospective customers or investors.

Section [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations), contains further recommendations. Although they are formatted similarly to requirements, they begin with a "level" marker \[GP\]. There is no requirement to test for these; however careful implementation and testing is _RECOMMENDED_.

Note that good implementation of the [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations) can enhance security, but in some cases incomplete or low-quality implementation could **reduce** security.

### 2.1 Conformance Claims[](https://entethalliance.org/specs/ethtrust-sl/#sec-conformance-claims)

To grant [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) EEA EthTrust Certification, an auditor provides a [Valid Conformance Claim](https://entethalliance.org/specs/ethtrust-sl/#dfn-valid-conformance-claim), that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) meets the requirements of the [Security Level](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-levels) for which it is certified.

There is no required format for a [Valid conformance claim](https://entethalliance.org/specs/ethtrust-sl/#dfn-valid-conformance-claim) for Version 1 of this specification, beyond being legible and containing the required information as specified in this section.

Note: Machine-readable formats

A Valid Conformance Claim _MUST_ include:

*   The date on which the certification was issued, in 'YYYY-MM-DD' format.
*   The [EVM version(s)](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm-version) (of those listed at \[[EVM-version](https://entethalliance.org/specs/ethtrust-sl/#bib-evm-version "Using the Compiler - Solidity Documentation. (§Targets)")\]) for which the certification is valid.
*   The version of the EEA EthTrust Security Levels specification for which the contract is certified (this specification is "Version 2").
*   A name and a URL for the organisation or software issuing the certification.
*   The [Security Level](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-levels) (**"S"**, "**M**", or "**Q**") that the [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) claims.
*   A \[[SHA3-256](https://entethalliance.org/specs/ethtrust-sl/#bib-sha3-256 "FIPS 202 - SHA-3 Standard: Permutation-Based Hash and Extendable-Output Functions")\] hash of the compiled bytecode for each contract in the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) certified, sorted ascending by the hash value interpreted as a number.
*   A \[[SHA3-256](https://entethalliance.org/specs/ethtrust-sl/#bib-sha3-256 "FIPS 202 - SHA-3 Standard: Permutation-Based Hash and Extendable-Output Functions")\] hash of the Solidity source code for each contract in the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) certified, sorted ascending by the hash value interpreted as a number.
*   The compiler options applied for each compilation.
*   The contract metadata generated by the compiler.
*   A list of the requirements which were tested and a statement for each one, noting whether the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) meets the requirement. This _MAY_ include further information.
*   An explicit notice stating that [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-eea-ethtrust-certified) does not provide any warranty or formal guarantee
    
    *   of the overall security of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), nor
    *   that the project is free from bugs or vulnerabilities.
    
    This notice _SHOULD_ state that [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-eea-ethtrust-certified) represents the best efforts of the issuer to detect and identify certain known vulnerabilities that can affect Smart Contracts.
*   For conformance claims where certification is granted because the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) met an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) or a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements), the conformance claim _MUST_ include the results for the [Overriding Requirement(s)](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) met, and _MAY_ omit the results for the requirement(s) whose results were thus unnecessary to determine conformance.

A [Valid Conformance Claim](https://entethalliance.org/specs/ethtrust-sl/#dfn-valid-conformance-claim) for [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q) _MUST_ contain a \[[SHA3-256](https://entethalliance.org/specs/ethtrust-sl/#bib-sha3-256 "FIPS 202 - SHA-3 Standard: Permutation-Based Hash and Extendable-Output Functions")\] hash of the documentation provided to meet [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented) and [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system).

A [Valid Conformance Claim](https://entethalliance.org/specs/ethtrust-sl/#dfn-valid-conformance-claim) _SHOULD_ include:

*   A contact address for questions about or challenges to the certification.
*   Descriptions of conformance to the good practices described in [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations).

A [Valid Conformance Claim](https://entethalliance.org/specs/ethtrust-sl/#dfn-valid-conformance-claim) _MAY_ include:

*   An address where a \[[SHA3-256](https://entethalliance.org/specs/ethtrust-sl/#bib-sha3-256 "FIPS 202 - SHA-3 Standard: Permutation-Based Hash and Extendable-Output Functions")\] hash of the conformance claim has been recorded on an identified network, e.g. Ethereum Mainnet.
*   An address of the contract deployed on an identified network, e.g. Ethereum Mainnet.

Valid values of EVM versions are those listed in the Solidity documentation \[[EVM-version](https://entethalliance.org/specs/ethtrust-sl/#bib-evm-version "Using the Compiler - Solidity Documentation. (§Targets)")\]. As of November 2023 the two most recent are `shanghai` and `paris`.

### 2.2 Who can offer EEA EthTrust Certification?[](https://entethalliance.org/specs/ethtrust-sl/#who-can-audit)

_This section is non-normative._

This version of the specification does not make any restrictions on who can perform an audit and provide [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified). There is no certification process defined for auditors or tools who grant certification. This means that Auditors' claims of performing accurate tests are made by themselves. There is always a possibility of fraud, misrepresentation, or incompetence on the part of any auditor who offers "EEA EthTrust certification" for Version 1.

Note

In principle anyone can submit a smart contract for verification. However submitters need to be aware of any restrictions on usage arising from copyright conditions or the like. In addition, meeting certain requirements can be more difficult to demonstrate in a situation of limited control over the development of the smart contract.

The Working Group expects its own members, who wrote the specification, to behave to a high standard of integrity and to know the specification well, and notes that there are many others who also do so.

The Working Group or EEA _MAY_ seek to develop an auditor certification program for subsequent versions of the EEA EthTrust Security Levels Specification.

### 2.3 Identifying what is certified[](https://entethalliance.org/specs/ethtrust-sl/#sec-source-and-contracts)

An EEA EthTrust evaluation is performed on Tested Code, which means the Solidity source code for a smart contract or several related smart contracts, along with the bytecode generated by compiling the code with specified parameters.

If the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) is divided into more than one smart contract, each deployable at a single address, it is referred to as a Set Of Contracts.

3\. Security Considerations[](https://entethalliance.org/specs/ethtrust-sl/#sec-security-considerations)
--------------------------------------------------------------------------------------------------------

_This section is non-normative._

Security of information systems is a major field of work. There are risks inherent in any system of even moderate complexity.

This specification describes testing for security problems in Ethereum smart contracts. However there is no such thing as perfect security. EEA EthTrust certification means that at least a defined minimum set of checks has been performed on a smart contract. **This does not mean the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) definitely has no security vulnerabilities**. From time to time new security vulnerabilities are identified. Manual auditing procedures require skill and judgement. This means there is always a possibility that a vulnerability is not noticed in review.

### 3.1 Smart Contracts in context - broader considerations[](https://entethalliance.org/specs/ethtrust-sl/#sec-eth-broader-considerations)

Ethereum is based on a model of account holders authorising transactions between accounts. It is very difficult to stop a malicious actor with a privileged key from using that to cause undesirable or otherwise bad outcomes.

Likewise, in practice users often interact with smart contracts through a "Ðapp" or "distributed app". Web Application Security is its own extensive area of research and development, beyond the scope of this specification.

### 3.2 Upgradable Contracts[](https://entethalliance.org/specs/ethtrust-sl/#sec-proxy-contract-considerations)

Smart contracts in Ethereum are immutable by default. However, for some scenarios, it is desirable to modify them, for example to add new features or fix bugs. An Upgradable Contract is any type of contract that fulfills these needs by enabling changes to the code executed via calls to a fixed address.

Some common patterns for Upgradable Contracts use a Proxy Contract: a simple wrapper that users interact with directly that is in charge of forwarding transactions to and from another contract (called the Execution Contract in this document, but also known as a Logic Contract), which contains the code that actually implements the Smart Contract's behaviour.

The [Execution Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract) can be replaced while the [Proxy Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-proxy-contract), acting as the access point, is never changed. Both contracts are still immutable in the sense that their code cannot be changed, but one [Execution Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract) can be swapped out with another. The [Proxy Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-proxy-contract) can thus point to a different implementation and in doing so, the software is "upgraded".

This means that a [Set of Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts) that follow this pattern to make an [Upgradable Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-upgradable-contract) generally cannot be considered immutable, as the [Proxy Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-proxy-contract) itself could redirect calls to a new [Execution Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract), which could be insecure or malicous. By meeting the requirements for [access control](https://entethalliance.org/specs/ethtrust-sl/#sec-3-access-control) in this specification to restrict upgrade capabilities enabling new [Execution Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract) to be deployed, and by documenting upgrade patterns and following that documentation per [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented), deployers of [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) can demonstrate reliability. In general, EthTrust certification of a [Proxy Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-proxy-contract) does not apply to the internal logic of an Upgradable Contract, so a new [Execution Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract) needs to be certified before upgrading to it through the [Proxy Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-proxy-contract).

There are several possible variations on this core structure, for example having a [Set of Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts) that includes multiple [Execution Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract). In the attack known as a Metamorphic Upgrade, a series of Smart Contracts are used to convince people (e.g. voters in a DAO) to approve a certain piece of code for deployment, but one of the proxy contracts in the chain is updated to deploy different, malicious, code.

Other patterns rely on using the `CREATE2` instruction to deploy a Smart Contract at a known address. It is currently possible to remove the code at that address using the `selfdestruct()` method, and then deploy new code to that address. This possibility is sometimes used to save Gas Fees, but it is also used in a [Metamorphic Upgrade](https://entethalliance.org/specs/ethtrust-sl/#dfn-metamorphic-upgrade) attack.

### 3.3 Oracles[](https://entethalliance.org/specs/ethtrust-sl/#sec-oracle-considerations)

A common feature of Ethereum networks is the use of Oracles: functions that can provide information sourced from on-chain or off-chain data. Oracles solve a range of problems, from providing random number generation to asset data, managing the operation of liquidity pools, and enabling access to weather, sports, or other special-interest information. Oracles are used heavily in DeFi and gaming, where asset data and randomization are central to protocol design.

This specification contains requirements to check that smart contracts are sufficiently robust to deal appropriately with whatever information is returned, including the possibility of malformed data that can be deliberately crafted for oracle-specific attacks.

While some aspects of [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) are within the scope of this specification, it is still possible that an [Oracle](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) provides misinformation or even actively produces harmful disinformation.

The two key considerations are the risk of corrupted or manipulated data, and the risk of oracle failure. Vulnerabilities related to these considerations - excessive reliance on [TWAP](https://entethalliance.org/specs/ethtrust-sl/#dfn-twap), and unsafe management of oracle failure - have occurred repeatedly leading to the loss of millions of dollars of value on various DeFi protocols.

While many high-quality and trusted [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) are available, it is possible to suffer an attack even with legitimate data. When calling on an Oracle, data received needs to be be checked for staleness to avoid [Front-running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running) attacks. Even in non-DeFi scenarios, such as a source of randomness, it is often important to reset the data source for each transaction, to avoid arbitrage on the next transaction.

A common strategy for pricing Oracles is to provide a time-weighted average price (known as TWAP). This provides some level of security against sudden spikes such as those created by a Flashloan attack, but at the cost of providing stale information.

It is important to choose time windows carefully: when a time window is too wide, it won't reflect volatile asset prices, leaking opportunities to arbitrageurs. However the "instantaneous" price of an asset is often not a good data point: It is the most manipulable piece of Oracle data, and in any event it will always be stale by the time a transaction is executed.

Oracles that collate a wide variety of source data, clean outliers from their data, and are well-regarded by the community, are more likely to be reliable. If an Oracle is off-chain, whether it reflects stale on-chain data, or reliable and accurate data that is truly off-chain, is an important consideration.

Even an [Oracle](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) using a well-chosen [TWAP](https://entethalliance.org/specs/ethtrust-sl/#dfn-twap) can enable a liquidity pool or other DeFi structure to be manipulated, especially by taking advantage of flashloans and flashswaps to cheaply raise funds. If an asset targeted for manipulation has insufficient liquidity this can render it vulnerable to large price swings by an attacker holding only a relatively small amount of liquidity.

The second important consideration when using [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) is that of a graceful failure scenario. What happens if an [Oracle](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) no longer returns data, or suddenly returns an unlikely value? At least one protocol has suffered losses due to 'hanging' on a minimum value in the rare event of a price crash rather than truly dropping to zero, with traders who accumulated large amounts of a near zero-priced asset able to sell it back to the protocol. Hardcoding a minimum or maximum value can lead to problems reflecting reality.

### 3.4 External Interactions and Re-entrancy Attacks[](https://entethalliance.org/specs/ethtrust-sl/#sec-reentrancy-considerations)

Code that relies on external code can introduce multiple attack vectors. This includes cases where an external dependency contains malicious code or has been subject to malicious manipulation through security vulnerabilities. However, failure to adequately manage the possible outcomes of an external call can also introduce security vulnerabilities.

One of the most commonly cited vulnerabilities in Ethereum Smart Contracts is Re-entrancy Attacks. These attacks allow malicious contracts to make a call back into the contract that called it before the originating contract's function call has been completed. This effect causes the calling contract to complete its processing in unintended ways, for example, by making unexpected changes to its state variables.

A Read-only Re-entrancy Attack arises when a view function is reentered. These are a particular additional danger because such functions often lack safeguards since they don't modify the contract's state. However, if the state is inconsistent, incorrect values could be reported. This deception can mislead other protocols into reading inaccurate state values, potentially leading to unintended actions. This issue primarily affects other contracts that rely on the accurate reporting of state from these view functions, rather than the contract itself being reentered.

### 3.5 Signature Mechanisms[](https://entethalliance.org/specs/ethtrust-sl/#sec-signature-considerations)

Some requirements in the document refer to Malleable Signatures. These are signatures created according to a scheme constructed so that, given a message and a signature, it is possible to efficiently compute the signature of a different message - usually one that has been transformed in specific ways. While there are valuable use cases that such signature schemes allow, if not used carefully they can lead to vulnerabilities, which is why this specification seeks to constrain their use appropriately. In a similar vein, Hash Collisions could occur for hashed messages where the input used is malleable, allowing the same signature to be used for two distinct messages.

Other requirements in the document are related to exploits which take advantage of ambiguity in the input used to created the signed message. When a signed message does not include enough identifying information concerning where, when, and how many times it is intended to be used, the message signature could be used (or reused) in unintended functions, contracts, chains, or even at unintended times.

For more information on this topic, and the potential for exploitation, see also \[[chase](https://entethalliance.org/specs/ethtrust-sl/#bib-chase "Malleable Signatures: New Definitions and Delegatable Anonymous Credentials")\].

### 3.6 Gas and Gas Prices[](https://entethalliance.org/specs/ethtrust-sl/#sec-gas-considerations)

Gas Griefing is the deliberate abuse of the Gas mechanism that Ethereum uses to regulate the consumption of computing power, to cause an unexpected or adverse outcome much in the style of a Denial of Service attack. Because Ethereum is designed with the Gas mechanism as a regulating feature, it is insufficient to simply check that a transaction has enough Gas; checking for Gas Griefing needs to take into account the goals and business logic that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) implements.

Gas Siphoning is another abuse of the Gas mechanism that Ethereum uses to regulate the consumption of computing power, where attackers steal Gas from vulnerable contracts either to deny service or for their own gain (e.g. to mint [Gas Tokens](https://entethalliance.org/specs/ethtrust-sl/#dfn-gas-tokens)). Similar to Gas Griefing, checking for Gas Siphoning requires careful consideration of the goals and business logic that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) implements.

Gas Tokens use Gas when minted and free slightly less Gas when burned. Gas Tokens minted when Gas prices are low can be burned to subsidize Ethereum transactions when Gas prices are high.

In addition, a common feature of Ethereum [Network Upgrades](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork) is to change the Gas Price of specific operations. EEA EthTrust certification only applies for the [EVM version(s)](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm-version) specified; it is not valid for other [EVM versions](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm-version). Thus it is important to recheck code to ensure its security properties remain the same across [Network Upgrades](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork), or take remedial action.

MEV, used in this document to mean "Maliciously Extracted Value", refers to the potential for block producers or other paticipants in a blockchain to extract value that is not intentionally given to them, in other words to steal it, by maliciously reordering transactions, as in [Timing Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-timing-attacks), or suppressing them.

Note

The term MEV is commonly expanded as "Miner Extracted Value", and sometimes "Maximum Extractable Value". As in the example above, sometimes block miners can take best advantage of a vulnerability. But MEV can be exploited by other participants, for example duplicating most of a submitted transaction, but offering a higher fee so it is processed first.

Some MEV attacks can be prevented by careful consideration of the information that is included in a transaction, including the parameters required by a contract.

Other strategies include the use of hash commitment schemes \[[hash-commit](https://entethalliance.org/specs/ethtrust-sl/#bib-hash-commit "Commitment scheme - WikiPedia")\], batch execution, private transactions \[[EEA-clients](https://entethalliance.org/specs/ethtrust-sl/#bib-eea-clients "Enterprise Ethereum Client Specification - Editors' draft")\], Layer 2 \[[EEA-L2](https://entethalliance.org/specs/ethtrust-sl/#bib-eea-l2 "Introduction to Ethereum Layer 2")\], or an extension to establish the ordering of transactions before releasing sensitive information to all nodes participating in a blockchain.

The Ethereum Foundation curates up to date information on MEV \[[EF-MEV](https://entethalliance.org/specs/ethtrust-sl/#bib-ef-mev "Maximal Extractable Value (MEV)")\].

Censorship Attacks occur when a block processor actively suppresses a proposed transaction, for their own benefit.

Future Block Attacks are those where a block proposer knows they will produce a paticular block, and uses this information to craft the block to maliciously extract value from other transactions. See for example \[[futureblock](https://entethalliance.org/specs/ethtrust-sl/#bib-futureblock "Future-block MEV in Proof of Stake")\] or \[[postmerge-mev](https://entethalliance.org/specs/ethtrust-sl/#bib-postmerge-mev "Why is Oracle Manipulation after the Merge so cheap? Multi-Block MEV")\].

Timing Attacks are a class of MEV attacks where an adversary benefits from placing their or a victim's transactions earlier or later in a block. They include [Front-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running), [Back-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-back-running), and [Sandwich Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-sandwich-attacks).

Front-Running is based on the fact that transactions are visible to the participants in the network before they are added to a block. This allows a malicious participant to submit an alternative transaction, frustrating the aim of the original transaction.

Back-Running is similar to [Front-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running), except the attacker places their transactions after the one they are attacking.

In Sandwich Attacks, an attacker places a victim's transaction undesirably between two other transactions.

### 3.8 Source code, pragma, and compilers[](https://entethalliance.org/specs/ethtrust-sl/#sec-source-compiler-considerations)

This version of the specification requires the compiled bytecode as well as the Solidity Source Code that together constitute the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code). Solidity is by a large measure the most common programming language for Ethereum smart contracts, and benefits of requiring source code in Solidity include

*   it simplifies a number of tests, and
*   there is substantial security research done on Solidity source code.

Solidity allows the source code to specify the Solidity compiler version used with a `pragma` statement. This specification currently has no requirement for a specific `pragma`, but it is good practice to ensure that the pragma refers to a bounded set of Solidity compiler versions, where it is known that those Solidity compiler versions produce identical bytecode from the given source code.

There are some drawbacks to requiring Solidity Source code. The most obvious is that some code that is not written in Solidity. Different languages have different features and often support different coding styles.

Perhaps more important, it means that a deployed contract written in Solidity cannot be tested directly without someone making the source code available.

Another important limitation introduced by reading source code is that it is subject to [Homoglyph Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-homoglyph-attacks), where characters that look the same but are different such as Latin "p" and Cyrillic "р", can deceive people visually reading the source code, to disguise malicious behaviour. There are related attacks that use features such as [Unicode Direction Control Characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters) or take advantage of inconsistent normalisation of combining characters to achieve the same type of deceptions.

### 3.9 Contract Deployment[](https://entethalliance.org/specs/ethtrust-sl/#sec-deployment-considerations)

This specification primarily addresses vulnerabilities that arise in Smart Contract code. However it is important to note that the deployment of a smart contract is often a crucial element of protocol operation. Some aspects of smart contract security primarily depend on how the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) gets deployed. Even audited protocols can be easily exploited if deployed naively.

Code written for a specific blockchain might depend on features available in that blockchain, and when the code is deployed to a different chain that is compatible (e.g. it uses the same [EVM](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm) to process smart contracts), the difference in features can expose a vulnerability. For any contract deployed to a blockchain or parachain that uses a patched fork of the EVM, common security assumptions may no longer apply to that EVM. It is valuable to deploy [EthTrust Certified](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) contracts to a testnet for each chain first, and undergo thorough penetration testing.

Of particular concern is the issue of upgradeable proxy-type contracts, and any contract utilizing an initializer function in deployment. Many protocols have been hacked due to accidentally leaving their initializer functions unprotected, or using a non-atomic deployment in which the initializing function is not called in the same transaction as the contract deployment. This scenario is ripe for [Front-running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running) attacks, and can result in protocol takeover by malicious parties, and theft or loss of funds. Initializing any initializable contract in the same transaction as its deployment reduces the risk that a malicious actor takes control of the contract.

Moreover, the deployment implications of assigning access roles to `msg.sender` or other variables in constructors and initializers need careful consideration. This is discussed further in [§ 4.3.2 Access Control](https://entethalliance.org/specs/ethtrust-sl/#sec-3-access-control) requirements.

Several libraries and tools exist specifically for safe proxy usage and safe contract deployment. From command-line tools to libraries to sophisticated UI-based deployment tools, many solutions exist to prevent unsafe proxy deployments and upgrades.

Using access control for a given contract's initializer, and limiting the number of times an initializer can be called on or after deployment, can enhance safety and transparency for the protocol itself and its users. Furthermore, a function that disables the ability to initialize an [Execution Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract) can prevent any future initializer calls after deployment, preventing later attacks or accidents.

Although this specification does not require that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) has been deployed, some requirements are more easily tested when code has been deployed to a blockchain, or can only be thoroughly tested "_in situ_".

### 3.10 Post-deployment Monitoring[](https://entethalliance.org/specs/ethtrust-sl/#sec-realtime-monitoring-considerations)

While monitoring Smart Contracts after deployment is beyond the formal scope of this specification, it is an important consideration for Smart Contract security. New attack techniques arise from time to time, and some attacks can only be prevented by active measures implemented in real time. Monitoring of on-chain activity can help detect attacks before it is too late to stop them.

Monitoring, backed by an automated dataset, can enable identifying an attack that has occurred elsewhere, even on other blockchains.

Automated monitoring can facilitate rapid response, producing alerts or automatically initiating action, improving the security of contracts that might be compromised when security responses are delayed by even a few blocks.

However, it can be difficult to determine the difference between an attack and anamolous behaviour on the part of individuals. Relying purely on automated monitoring can expose a blockchain to the risk that a malicious actor deliberately triggers an automated security response to damage a blockchain or project, analogous to a Denial of Service attack.

### 3.11 Network Upgrades[](https://entethalliance.org/specs/ethtrust-sl/#sec-netupgrades-considerations)

The EVM, or Ethereum Virtual Machine, acts as a distributed state machine for the Ethereum network, computing state changes resulting from transactions. The EVM maintains the network state for simple transfers of Ether, as well as more complex Smart Contract interactions. In other words, it is the "computer" (although in fact it is software) that runs the code of Smart Contracts.

From time to time the Ethereum community implements a Network Upgrade, sometimes also called a **hard fork**. This is a change to Ethereum that is backwards-incompatible. Because they _typically_ change the EVM, Ethereum Mainnet [Network Upgrades](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork) generally correspond to [EVM versions](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm-version).

A [Network Upgrade](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork) can affect more or less any aspect of Ethereum, including changing EVM opcodes or their Gas price, changing how blocks are added, or how rewards are paid, among many possibilities.

Because [Network Upgrades](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork) are not guaranteed to be backwards compatible, a newer [EVM version](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm-version) can process bytecode in unanticipated ways. If a [Network Upgrade](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork) changes the EVM to fix a security problem, it is important to consider that change, and it is a good practice to follow that upgrade.

Because claims of conformance to this specification are only valid for specific [EVM versions](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm-version), a [Network Upgrade](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork) can mean an updated audit is needed to maintain valid [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) for a current Ethereum network.

Network Upgrades typically only impact a few features. This helps limit the effort necessary to audit code after an upgrade: often there will be no changes that affect the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), or review of a small proportion that is the only part affected by a Network Upgrade will be sufficient to renew [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified).

4\. EEA EthTrust Security Levels[](https://entethalliance.org/specs/ethtrust-sl/#sec-levels)
--------------------------------------------------------------------------------------------

[EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) is available at three Security Levels. The Security Levels describe minimum requirements for certifications at each Security Level: **\[S\]**, **\[M\]**, and **\[Q\]**. These Security Levels provide successively stronger assurance that a smart contract does not have specific security vulnerabilities.

*   [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-one) is designed so that for most cases, where common features of Solidity are used following well-known patterns, [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) can be certified by an automated "static analysis" tool.
*   [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-two) mandates a stricter static analysis. It includes requirements where a human auditor is expected to determine whether use of a feature is necessary, or whether a claim about the security properties of code is justified.
*   [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-three) provides analysis of the business logic the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) implements, and that the code not only does not exhibit known security vulnerabilities, but also correctly implements what it claims to do.

The optional [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations), correctly implemented, further enhance the Security of smart contracts. However it is not necessary to test them to conform to this specification.

Note

The vulnerabilities addressed by this specification come from a number of sources, including Solidity Security Alerts \[[solidity-alerts](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-alerts "Solidity Blog - Security Alerts")\], the Smart Contract Weakness Classification \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\], TMIO Best practices \[[tmio-bp](https://entethalliance.org/specs/ethtrust-sl/#bib-tmio-bp "Best Practices for Smart Contracts (privately made available to EEA members)")\], various sources of Security Advisory Notices, discussions in the Ethereum community and academics presenting newly discovered vulnerabilities, and the extensive practical experience of participants in the Working Group.

### 4.1 Security Level \[S\][](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-one)

[EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) is intended to allow an unguided automated tool to analyze most contracts' bytecode and source code, and determine whether they meet the requirements. For some situations that are difficut to verify automatically, usually only likely to arise in a small minority of contracts, there are higher-level [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) that can be fulfilled instead to meet a requirement for this Security Level.

To be eligible for [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) for Security Level \[S\], [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ fulfil all [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirements, **unless** it meets the applicable **[Overriding Requirement(s)](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement)** for any [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirement it does not meet.

**\[S\] Encode Hashes with `chainid` [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-eip155-chainid)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ create hashes for transactions that incorporate `chainid` values following the recommendation described in \[[EIP-155](https://entethalliance.org/specs/ethtrust-sl/#bib-eip-155 "Simple Replay Attack Protection")\].

\[[EIP-155](https://entethalliance.org/specs/ethtrust-sl/#bib-eip-155 "Simple Replay Attack Protection")\] describes an enhanced hashing rule, incorporating a chain identifier in the hash. While this only provides a guarantee against replay attacks if there is a unique chain identifier, using the mechanism described provides a certain level of robustness and makes it much more difficult to execute a replay attack.

**\[S\] No `CREATE2` [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-create2)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain a `CREATE2` instruction  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[M\] Protect `CREATE2` Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-protect-create2), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

The `CREATE2` opcode provides the ability to interact with addresses that do not exist yet on-chain but could possibly eventually contain code. While this can be useful for deployments and counterfactual interactions with contracts, it can allow external calls to code that is not yet known, and could turn out to be malicous or insecure due to errors or weak protections.

**\[S\] No `tx.origin` [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-tx.origin)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain a `tx.origin` instruction  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[Q\] Verify `tx.origin` Usage**](https://entethalliance.org/specs/ethtrust-sl/#req-3-verify-tx.origin)

`tx.origin` is a global variable in Solidity which returns the address of the account that sent the transaction. A contract using `tx.origin` can allow an authorized account to call into a malicious contract, enabling the malicious contract to pass authorization checks in unintended cases. Use `msg.sender` for authorization instead of `tx.origin`.

See also [SWC-115](https://swcregistry.io/docs/SWC-115) \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\].

**\[S\] No Exact Balance Check [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ test that the balance of an account is exactly equal to (i.e. `==`) a specified amount or the value of a variable  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] Verify Exact Balance Checks**](https://entethalliance.org/specs/ethtrust-sl/#req-2-verify-exact-balance-check).

Testing the balance of an account as a basis for some action has risks associated with unexpected receipt of ether or another token, including tokens deliberately transfered to cause such tests to fail as an [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) attack.

See also the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Sources of Randomness**](https://entethalliance.org/specs/ethtrust-sl/#req-2-random-enough), [**\[M\] Don't Misuse Block Data**](https://entethalliance.org/specs/ethtrust-sl/#req-2-block-data-misuse), and [**\[Q\] Protect against MEV Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev), subsection [§ 3.7 MEV (Maliciously Extracted Value)](https://entethalliance.org/specs/ethtrust-sl/#sec-mev-considerations) of the Security Considerations for this specification, [SWC-132](https://swcregistry.io/docs/SWC-132) in \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\], and improper locking as described in \[[CWE-667](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-667 "CWE-667: Improper Locking")\].

**\[S\] No Conflicting Names [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-inheritance-conflict)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ include more than one variable, or operative function with different code, with the same name  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement): [**\[M\] Document Name Conflicts**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-inheritance-order).

In most programming languages, including Solidity, it is possible to use the same name for variables or functions that have different types or (for functions) input parameters. This can be hard to interpret in the source code, meaning reviewers misunderstand the code or are maliciously misled to do so, analogously to [Homoglyph Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-homoglyph-attacks).

This requirement means that unless the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) is met, any function or variable name will not be repeated, to eliminate confusion. It does however allow functions to be overridden, e.g. from a Base contract, so long as there is only one version of the function that operates within the code.

See also the [related requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Compiler Bug SOL-2020-2**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2020-2), and the [documentation of function inheritance](https://docs.soliditylang.org/en/latest/contracts.html#inheritance) in \[[solidity-functions](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-functions "Solidity Documentation: Contracts - Functions")\].

**\[S\] No Hashing Consecutive Variable Length Arguments [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-hashing-consecutive-variable-length-args)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use `abi.encodePacked()` with consecutive variable length arguments.

The elements of each variable-length argument to `abi.encodePacked()` are packed in order prior to hashing. [Hash Collisions](https://entethalliance.org/specs/ethtrust-sl/#dfn-hash-collisions) are possible by rearranging the elements between consecutive, variable length arguments while maintaining that their concatenated order is the same.

**\[S\] No `selfdestruct()` [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-self-destruct)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain the `selfdestruct()` instruction or its now-deprecated alias `suicide()`  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[M\] Protect Self-destruction**](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

If the `selfdestruct()` instruction (or its deprecated alternative `suicide()`) is not carefully protected, malicious code can call it and destroy a contract, sending any Ether held by the contract, thus potentially stealing it. This feature can often break immutability and trustless guarantees to introduce numerous security issues. In addition, once the contract has been destroyed any Ether sent is simply lost, unlike when a contract is disabled which causes a transaction sending Ether to revert.

`selfdestruct()` is officially deprecated, its usage discouraged, since Solidity compiler version 0.8.18 \[[solidity-release-818](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-release-818 "Solidity 0.8.18 Release Announcement")\].

See also [SWC-106](https://swcregistry.io/docs/SWC-106) in \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\], \[[EIP-6049](https://entethalliance.org/specs/ethtrust-sl/#bib-eip-6049 "Deprecate SELFDESTRUCT")\].

The `assembly {}` instruction allows lower-level code to be included. This give the authors much stronger control over the bytecode that is generated, which can be used for example to optimise gas usage. However, it also potentially exposes a number of vulnerabilites and bugs that are additional attack surfaces, and there are a number of ways to use `assembly {}` to introduce deliberately malicious code that is difficult to detect.

#### 4.1.1 Text and homoglyphs[](https://entethalliance.org/specs/ethtrust-sl/#sec-1-unicode)

**\[S\] No Unicode Direction Control Characters [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-unicode-bdo)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain any of the Unicode Direction Control Characters `U+2066`, `U+2067`, `U+2068`, `U+2029`, `U+202A`, `U+202B`, `U+202C`, `U+202D`, or `U+202E`  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] No Unnecessary Unicode Controls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-unicode-bdo).

Changing the apparent order of characters through the use of invisible [Unicode direction control characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters) can mask malicious code, even in viewing source code, to deceive human auditors.

More information on [Unicode direction control characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters) is available in the W3C note [How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls) \[[unicode-bdo](https://entethalliance.org/specs/ethtrust-sl/#bib-unicode-bdo "How to use Unicode controls for bidi text")\].

#### 4.1.2 External Calls[](https://entethalliance.org/specs/ethtrust-sl/#sec-1-external-calls)

See also the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements): [**\[M\] Protect External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls), and [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls).

**\[S\] Check External Calls Return [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-check-return)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls using the [Low-level Call Functions](https://entethalliance.org/specs/ethtrust-sl/#dfn-low-level-call-functions) (i.e. `call()`, `delegatecall()`, `staticcall()`, and `send()`) _MUST_ check the returned value from each usage to determine whether the call failed,  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] Handle External Call Returns**](https://entethalliance.org/specs/ethtrust-sl/#req-2-handle-return).

Normally, exceptions in calls cause a reversion. This will "bubble up", unless they are handled in a `try`/`catch`. However Solidity defines a set of Low-level Call Functions:

*   `call()`,
*   `delegatecall()`,
*   `staticcall()`, and
*   `send()`.

Calls using these functions behave differently. Instead of reverting on failure they return a boolean indicating whether the call completed successfully.

Not testing explicitly for the return value could lead to unexpected behavior in the caller contract. Assuming these calls reverting on failure _will_ lead to unexpected behaviour when they are not successful.

See also [SWC-104](https://swcregistry.io/docs/SWC-104) in \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\], error handling documentation in \[[error-handling](https://entethalliance.org/specs/ethtrust-sl/#bib-error-handling "Control Structures - Solidity Documentation. Section 'Error handling: Assert, Require, Revert and Exceptions'")\], unchecked return value as described in \[[CWE-252](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-252 "CWE-252: Unchecked Return Value")\], and the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements): [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i), [**\[M\] Handle External Call Returns**](https://entethalliance.org/specs/ethtrust-sl/#req-2-handle-return), and [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls).

**\[S\] Use Check-Effects-Interaction [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls _MUST_ use the [Checks-Effects-Interactions](https://entethalliance.org/specs/ethtrust-sl/#dfn-checks-effects-interactions) pattern to protect against [Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-re-entrancy-attacks)  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[M\] Protect external calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented),

**or** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls),
*   [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented),
*   [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), **and**
*   [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented).

The Checks-Effects-Interactions pattern ensures that validation of the request, and changes to the state variables of the contract, are performed before any interactions take place with other contracts. When contracts are implemented this way, the scope for [Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-re-entrancy-attacks) is reduced significantly.

As well as checking the particular contract effects, it is possible as part of this pattern to test protocol invariants, to provide a further assurance that a request doesn't produce an unsafe outcome.

See also [§ 3.4 External Interactions and Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#sec-reentrancy-considerations), the explanation of "Checks-Effects-Interactions" \[[c-e-i](https://entethalliance.org/specs/ethtrust-sl/#bib-c-e-i "Security Considerations - Solidity Documentation. Section 'Use the Checks-Effects-Interactions Pattern'")\] in "Solidity Security Considerations" \[[solidity-security](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-security "Security Considerations - Solidity Documentation.")\], "[Checks Effects Interactions](https://fravoll.github.io/solidity-patterns/checks_effects_interactions.html)" in \[[solidity-patterns](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-patterns "Solidity Patterns")\], and \[[freipi](https://entethalliance.org/specs/ethtrust-sl/#bib-freipi "You're writing require statements wrong")\].

**\[S\] No `delegatecall()` [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-delegatecall)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain the `delegatecall()` instruction  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements):

*   [**\[M\] Protect External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

**or** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls),
*   [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented),
*   [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), **and**
*   [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented).

The `delegatecall()` instruction enables an external contract to manipulate the state of a contract that calls it, because the code is run with the caller's balance, storage, and address.

#### 4.1.3 Improved Compilers[](https://entethalliance.org/specs/ethtrust-sl/#sec-1-compile-improvements)

Note

Implementing the Recommended Good Practice [**\[GP\] Use Latest Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-R-use-latest-compiler) means that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) passes the requirement in this subsection.

**\[S\] No Overflow/Underflow [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-overflow-underflow)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use a Solidity compiler version older than 0.8.0  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[M\] Safe Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-2-overflow-underflow), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

Like most programming languages, the EVM and Solidity represent numbers as a set of bytes that by default has a fixed length. This means arithmetic operations on large numbers can "overflow" the size by producing a result that does not fit in the space allocated. This results in corrupted data, and can be used as an attack on code. The \[[CWE](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe "Common Weakness Enumeration")\] registry of generic code vulnerabilities contains many overflow attacks; it is a well-known vector that is exposed in many systems and has regularly been exploited.

There are many ways to check for overflows, or underflows (where a negative number is large enough in magnitude to trigger the same effect). Since Solidity compiler version 0.8.0 there is built-in arithmetic overflow protection. [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) compiled with an earlier Solidity compiler version needs to check explicitly to mitigate this potential vulnerability.

See also [SWC-101](https://swcregistry.io/docs/SWC-101) in \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\].

#### 4.1.4 Compiler Bugs[](https://entethalliance.org/specs/ethtrust-sl/#sec-1-compiler-bugs)

There are a number of known security bugs in different Solidity compiler versions. The requirements in this subsection ensure that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) does not trigger these bugs. The name of the requirement includes the uid first recorded for the bug in \[[solidity-bugs-json](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-bugs-json "A JSON-formatted list of some known security-relevant Solidity bugs")\], as a key that can be used to find more information about the bug. \[[solidity-bugs](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-bugs "List of Known Bugs")\] describes the conventions used for the JSON-formatted list of bugs.

The requirements in this subsection are ordered according to the latest Solidity compiler versions that are vulnerable.

Note

Implementing the Recommended Good Practice [**\[GP\] Use Latest Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-R-use-latest-compiler) means that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) passes all requirements in this subsection.

Some compiler-related bugs are in the [§ 4.2.5 Security Level \[M\] Compiler Bugs and Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#sec-level-2-compiler-bugs) as [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m) requirements, either because they are [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for requirements in this subsection, or because they are part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirements that already ensure that the bug cannot be triggered.

Some bugs were introduced in known Solidity compiler versions, while others are known or assumed to have existed in all Solidity compiler versions until they were fixed.

**\[S\] Compiler Bug SOL-2023-3 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2023-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that includes Yul code and uses the `verbatim` instruction twice, in each case surrounded by identical code, _MUST_ disable the Block Deduplicator when using a Solidity compiler version between 0.8.5 and 0.8.22 (inclusive).

From Solidity compiler version 0.8.5 until 0.8.22, the block deduplicator incorrectly processed `verbatim` items, meaning that sometimes it conflated two items based on the code surrounding them instead of comparing them properly.

See also the [8 November 2023 security alert](https://soliditylang.org/blog/2023/11/08/verbatim-invalid-deduplication-bug/).

**\[S\] Compiler Bug SOL-2022-6 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-6)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that ABI-encodes a tuple (including a `struct`, `return` value, or a parameter list) that includes a dynamic component with the ABIEncoderV2, and whose last element is a `calldata` static array of base type `uint` or `bytes32`, _MUST NOT_ use a Solidity compiler version between 0.5.8 and 0.8.15 (inclusive).

From Solidity compiler version 0.5.8 until 0.8.15, ABI encoding a tuple whose final component is a `calldata` static array of base type `uint` or `bytes32` with the ABIEncoderV2 could result in corrupted data.

See also the [8 August 2022 security alert](https://blog.soliditylang.org/2022/08/08/calldata-tuple-reencoding-head-overflow-bug/).

**\[S\] Compiler Bug SOL-2022-5 with `.push()` [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-5-push)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies `bytes` arrays from `calldata` or `memory` whose size is not a multiple of 32 bytes, and has an empty `.push()` instruction that writes to the resulting array, _MUST NOT_ use a Solidity compiler version older than 0.8.15.

Until Solidity compiler version 0.8.15 copying memory or calldata whose length is not a multiple of 32 bytes could expose data beyond the data copied, which could be observable using code through `assembly {}`.

See also the [15 June 2022 security alert](https://blog.soliditylang.org/2022/06/15/dirty-bytes-array-to-storage-bug/) and the [related requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Compiler Bug SOL-2022-5 in `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly).

**\[S\] Compiler Bug SOL-2022-3 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that

*   uses `memory` and `calldata` pointers for the same function, **and**
*   changes the data location of a function during inheritance, **and**
*   performs an internal call at a location that is only aware of the original function signature from the base contract

_MUST NOT_ use a Solidity compiler version between 0.6.9 and 0.8.13 (inclusive).

Solidity compiler versions from 0.6.9 until it was fixed in 0.8.13 had a bug that incorrectly allowed internal or public calls to use a simpification only valid for external calls, treating `memory` and `calldata` as equivalent pointers.

See also the 17 May 2022 [security alert](https://blog.soliditylang.org/2022/05/17/data-location-inheritance-bug/).

**\[S\] Compiler Bug SOL-2022-2 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-2)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) with a nested array that

*   passes it to an external function, **or**
*   passes it as input to `abi.encode()`, **or**
*   uses it in an event

_MUST NOT_ use a Solidity compiler version between 0.6.9 and 0.8.13 (inclusive).

Solidity compiler versions from 0.5.8 until it was fixed in 0.8.13 had a bug that meant a single-pass encoding and decoding of a nested array could read data beyond the `calldatasize()`.

See also the 17 May 2022 [security alert](https://blog.soliditylang.org/2022/05/17/calldata-reencode-size-check-bug/).

**\[S\] Compiler Bug SOL-2022-1 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that

*   uses Number literals for a [`bytesNN`](https://entethalliance.org/specs/ethtrust-sl/#dfn-bytesnn) type shorter than 32 bytes, **or**
*   uses String literals for any [`bytesNN`](https://entethalliance.org/specs/ethtrust-sl/#dfn-bytesnn) type,

**and** passes such literals to `abi.encodeCall()` as the first parameter, _MUST NOT_ use Solidity compiler version 0.8.11 nor 0.8.12.

Solidity defines a set of types for variables known collectively as `bytesNN` or Fixed-length Variable types, that specify the length of the variable as a fixed number of bytes, following the pattern

*   `bytes1`
*   `bytes2`
*   ...
*   `bytes10`
*   ...
*   `bytes32`

Solidity compiler versions 0.8.11 and 0.8.12 had a bug that meant literal parameters were incorrectly encoded by `abi.encodeCall()` in certain circumstances.

See also the 16 March 2022 [security alert](https://blog.soliditylang.org/2022/03/16/encodecall-bug/).

**\[S\] Compiler Bug SOL-2021-4 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-sol-2021-4)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses custom value types shorter than 32 bytes _MUST NOT_ use Solidity compiler version 0.8.8.

Solidity compiler version 0.8.8 had a bug that assigned a full 32 bytes of storage to custom types that did not need it. This can be misused to enable reading arbitrary storage, as well as causing errors if the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) contains code compiled using different Solidity compiler versions.

See also the 29 September 2021 [security alert](https://blog.soliditylang.org/2021/09/29/user-defined-value-types-bug/)

**\[S\] Compiler Bug SOL-2021-2 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2021-2)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses `abi.decode()` on byte arrays as `memory` _MUST NOT_ use the ABIEncoderV2 with a Solidity compiler version between 0.4.16 and 0.8.3 (inclusive).

Solidity compiler version 0.4.16 introduced a bug, fixed in 0.8.4, that meant the ABIEncoderV2 incorrectly validated pointers when reading `memory` byte arrays, which could result in reading data beyond the array area due to an overflow error in calculating pointers.

See also the 21 April 2021 [security alert](https://blog.soliditylang.org/2021/04/21/decoding-from-memory-bug/).

**\[S\] Compiler Bug SOL-2021-1 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2021-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that has 2 or more occurrences of an instruction `keccak(mem,length)` where

*   the values of mem are equal, **and**
*   the values of length are unequal, **and**
*   the values of length are not multiples of 32,

_MUST NOT_ use the Optimizer with a Solidity compiler version older than 0.8.3.

Solidity compiler versions before 0.8.3 had an Optimizer bug that meant keccak hashes, calculated for the same content but different lengths that were not multiples of 32 bytes, incorrectly used the first value from cache instead of recalculating.

See also the 23 March 2021 [security alert](https://blog.soliditylang.org/2021/03/23/keccak-optimizer-bug/).

**\[S\] Compiler Bug SOL-2020-11-push [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-11-push)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies an empty byte array to storage, and subsequently increases the size of the array using `push()` _MUST NOT_ use a Solidity compiler version older than 0.7.4.

Solidity compiler versions before 0.7.4 had a bug that meant data would be packed after an empty array, and if the length of the array is subsequently extended by `push()`, that data would be readable from the array.

See also the 19 October 2020 [security alert](https://blog.soliditylang.org/2020/10/19/empty-byte-array-copy-bug/).

**\[S\] Compiler Bug SOL-2020-10 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-10)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies an array of types shorter than 16 bytes to a longer array _MUST NOT_ use a Solidity compiler version older than 0.7.3.

Solidity compiler versions before 0.7.3 had a bug that meant when array data for types shorter than 16 bytes are assigned to a longer array, the extra values in that longer array are not correctly reset to zero.

See also the 7 October 2020 [security alert](https://blog.soliditylang.org/2020/10/07/solidity-dynamic-array-cleanup-bug).

**\[S\] Compiler Bug SOL-2020-9 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-9)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that defines [Free Functions](https://entethalliance.org/specs/ethtrust-sl/#dfn-free-functions) _MUST NOT_ use Solidity compiler version 0.7.1.

Solidity compiler version 0.7.1 introduced Free Functions \[[solidity-functions](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-functions "Solidity Documentation: Contracts - Functions")\]: Functions that are defined in the source code of a smart contract but outside the scope of the formal contract declaration. [Free Functions](https://entethalliance.org/specs/ethtrust-sl/#dfn-free-functions) have `internal` visibility, and the compiler "inlines" them to the contracts that call them. The solidity documentation explains that they are:

> executed in the context of a contract. They still have access to the variable this, can call other contracts, send them Ether and destroy the contract that called them, among other things. The main difference to functions defined inside a contract is that free functions do not have direct access to storage variables and functions not in their scope.[https://docs.soliditylang.org/en/latest/contracts.html#functions](https://docs.soliditylang.org/en/latest/contracts.html#functions)

Solidity compiler version 0.7.1 did not correctly distinguish overlapping [Free Function](https://entethalliance.org/specs/ethtrust-sl/#dfn-free-functions) declarations, meaning that the wrong function could be called.

See examples of a [passing contract](https://entethalliance.github.io/eta-registry/examples/SOL-2020-9-fail.sol) and a [failing contract](https://entethalliance.github.io/eta-registry/examples/SOL-2020-9-fail.sol) for this requirement.

**\[S\] Compiler Bug SOL-2020-8 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-8)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that calls internal library functions with `calldata` parameters called via `using for` _MUST NOT_ use Solidity compiler version 0.6.9.

Solidity compiler version 0.6.9 incorrectly copied `calldata` parameters passed to internal library functions with `using for` as if they were calling to external library functions, leading to stack corruption and an incorrect jump destination.

See also a [Github issue with a code example](https://github.com/ethereum/solidity/issues/9172).

**\[S\] Compiler Bug SOL-2020-6 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-6)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that accesses an array slice using an expression for the starting index that can evaluate to a value other than zero _MUST NOT_ use the ABIEncoderV2 with a Solidity compiler version between 0.6.0 and 0.6.7 (inclusive).

Solidity compiler version 0.6.0 introduced a bug fixed in 0.6.8 that incorrectly calculated index offsets for the start of array slices, used in dynamic `calldata` types, when using the ABIEncoderV2.

**\[S\] Compiler Bug SOL-2020-7 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-7)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that passes a string literal containing two consecutive backslash ("\\") characters to an encoding function or an external call _MUST NOT_ use the ABIEncoderV2 with a Solidity compiler version between 0.5.14 and 0.6.7 (inclusive).

Solidity compiler version 0.5.14 introduced a bug fixed in 0.6.8 that incorrectly encoded consecutive backslash characters in string literals when passing them to an external function, or an encoding function, when using the ABIEncoderV2.

**\[S\] Compiler Bug SOL-2020-5 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-5)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that defines a contract that does not include a constructor, but has a base contract that defines a constructor not defined as `payable` _MUST NOT_ use a Solidity compiler version between 0.4.5 and 0.6.7 (inclusive), **unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] Check Constructor Payment**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-check-payable-constructor).

Solidity compiler version 0.4.5 introduced a check intended to result in contract creation reverting if value is passed to a constructor that is not explicitly marked as `payable`. If the constructor was inherited from a base instead of explicitly defined in the contract, this check did not function properly until Solidity compiler version 0.6.8, meaning the creation would not revert as expected.

**\[S\] Compiler Bug SOL-2020-4 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-4)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes assignments to tuples that

*   have nested tuples, **or**
*   include a pointer to an external function, **or**
*   reference a dynamically sized `calldata` array

_MUST NOT_ use a Solidity compiler version older than 0.6.5.

Solidity compiler version 0.1.6 introduced a bug, fixed in Solidity compiler version 0.6.5, that meant tuple assignments involving nested tuples, pointers to external functions, or references to dynamically sized `calldata` arrays, were corrupted due to incorrectly calculating the number of stack slots.

**\[S\] Compiler Bug SOL-2020-3 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that declares arrays of size larger than 2^256-1 _MUST NOT_ use a Solidity compiler version older than 0.6.5.

Solidity compiler version 0.2.0 introduced a bug, fixed in Solidity compiler version 0.6.5, that meant no overflow check was performed for the creation of very large arrays, meaning in some cases an overflow error would occur that would result in consuming all gas in a transaction due to the memory handling error introduced in compiling the contract.

**\[S\] Compiler Bug SOL-2020-1 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that declares variables inside a `for` loop that contains a `break` or `continue` statement _MUST NOT_ use the Yul Optimizer with Solidity compiler version 0.6.0 nor a Solidity compiler version between 0.5.8 and 0.5.15 (inclusive).

A bug in the Yul Optimiser in Solidity compiler versions from 0.5.8 to 0.5.15 and in Solidity compiler version 0.6.0 meant assignments for variables declared inside a `for` loop that contained a `break` or `continue` statement could be removed.

There are a number of known compiler bugs that affect Solidity Compiler Versions older than 0.6.0, but research into compiler bugs tends to focus on those that affect relatively modern Solidity Compiler versions, so any further bugs in older Solidity Compiler versions are only likely to be discovered and generally known as a result of being exploited.

It is a good practice to use a modern Solidity Compiler Version. In the rare cases where it is not possible to use a Solidity Compiler Version later than 0.6.0, it is possible to achieve [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) by conforming to the relevant [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) that were defined in version 1 of this specification \[[EthTrust-sl-v1](https://entethalliance.org/specs/ethtrust-sl/#bib-ethtrust-sl-v1 "EEA EthTrust Security Levels Specification. Version 1")\].

See also the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Use a Modern Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-060), covering Solidity Compiler bugs that require review for [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m).

**\[S\] No Ancient Compilers [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-ancient-compilers)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use a Solidity compiler version older than 0.3.

Compiler bugs are not tracked for compiler Solidity compiler versions older than 0.3. There is therefore a risk that unknown bugs create unexpected problems.

See also "SOL-2016-1" in \[[solidity-bugs-json](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-bugs-json "A JSON-formatted list of some known security-relevant Solidity bugs")\].

### 4.2 Security Level \[M\][](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-two)

[EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at Security Level \[M\] means that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) has been carefully reviewed by a human auditor or team, doing a manual analysis, and important security issues have been addressed to their satisfaction.

This level includes a number of [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for cases when [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) does not meet a [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirement directly, because it uses an uncommon feature that introduces higher risk, or because in certain circumstsances testing that the requirement has been met requires human judgement. Passing the relevant [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) tests that the feature has been implemented sufficiently well to satisfy the auditor that it does not expose the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) to the known vulnerabilities identified in this Security Level.

**\[M\] Pass Security Level \[S\] [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-pass-l1)**  
To be eligible for [EEA EthTrust certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m), [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ meet the requirements for [§ 4.1 Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-one).

**\[M\] Explicitly Disambiguate Evaluation Order [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-enforce-eval-order)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain statements where variable evaluation order can result in different outcomes

The evaluation order of functions is not entirely deterministic in Solidity, and is not guaranteed to be consistent across Solidity compiler versions. This means that the outcome of a statement calling multiple functions that each have side effects on shared stateful objects can lead to different outcomes if the order that the called functions were evaluated varies.

Also, the evaluation order in events and the instructions `addmod` and `modmul` generally does not follow the **usual** pattern, meaning that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) using those instructions could produce unexpected outcomes.

Warning

A common approach to addressing this vulnerability is the use of temporary results, to ensure evaluation order will be the same.

See also \[[richards2022](https://entethalliance.org/specs/ethtrust-sl/#bib-richards2022 "Solidity Underhanded Contest 2022. Submission 9 - Tynan Richards")\], \[[solidity-cheatsheet](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-cheatsheet "Solidity Documentation: Cheatsheet - Order Of Precedence Of Operators")\], and the [19 July 2023 Solidity Compiler Security Bug notification](https://blog.soliditylang.org/2023/07/19/full-inliner-non-expression-split-argument-evaluation-order-bug/) for Solidity Compiler Security Bug 2023-2, noted in \[[solidity-bugs-json](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-bugs-json "A JSON-formatted list of some known security-relevant Solidity bugs")\].

**\[M\] No Failing `assert()` Statements [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-no-failing-asserts)**  
`assert()` statements in [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ fail.

`assert()` statements are meant for invariants, not as a generic error-handling mechanism. If an `assert()` statement fails because it is being used as a mechanism to catch errors, it is better to replace it with a `require()` statement or similar mechanism designed for the use case. If it fails due to a coding bug, that needs to be fixed.

This requirement is based on \[[CWE-670](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-670 "CWE-670: Always-Incorrect Control Flow Implementation")\] Always-Incorrect Control Flow Implementation.

**\[M\] Verify Exact Balance Checks [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-verify-exact-balance-check)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that checks whether the balance of an account is exactly equal to (i.e. `==`) a specified amount or the value of a variable. _MUST_ protect itself against transfers affecting the balance tested.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Exact Balance Check**](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check).

If a Smart Contract checks that an account balance is some particular exact value at some point during its execution, it is potentially vulnerable to an attack, where a transfer to the account can be used to change the balance of the account causing unexpected results such as a transaction reverting. If such checks are used it is important that they are protected against this possibility.

#### 4.2.1 Text and homoglyph attacks[](https://entethalliance.org/specs/ethtrust-sl/#sec-2-unicode)

The requirements in this section are related to the security advisory \[[CVE-2021-42574](https://entethalliance.org/specs/ethtrust-sl/#bib-cve-2021-42574 "National Vulnerability Database CVE-2021-42574")\] and \[[CWE-94](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-94 "CWE-94: Improper Control of Generation of Code ('Code Injection')")\], "Improper Control of Generation of Code", also called "Code Injection".

**\[M\] No Unnecessary Unicode Controls [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-unicode-bdo)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use [Unicode direction control characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters) **unless** they are necessary to render text appropriately, and the resulting text does not mislead readers.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Unicode Direction Control Characters**](https://entethalliance.org/specs/ethtrust-sl/#req-1-unicode-bdo).

[Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m) permits the use of [Unicode direction control characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters) in text strings, subject to analysis of whether they are necessary.

**\[M\] No Homoglyph-style Attack [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-no-homoglyph-attack)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use homoglyphs, Unicode control characters, combining characters, or characters from multiple Unicode blocks, if the impact is misleading.

Techniques such as substituting characters from different alphabets (e.g. Latin "a" and Cyrillic "а" are not the same) can be used to mask malicious code, for example by presenting variables or function names designed to mislead auditors. These attacks are known as Homoglyph Attacks. Several approaches to successfully exploiting this issue are described in \[[Ivanov](https://entethalliance.org/specs/ethtrust-sl/#bib-ivanov "Targeting the Weakest Link: Social Engineering Attacks in Ethereum Smart Contracts")\].

In the rare case when there is a valid use of characters from multiple Unicode blocks (see \[[unicode-blocks](https://entethalliance.org/specs/ethtrust-sl/#bib-unicode-blocks "Blocks-14.0.0.txt")\]) in a variable name or label (most likely to be mixing two languages in a name), requirements at this level allow them to pass [EEA EthTrust certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) so long as they do not mislead or confuse.

This level requires checking for homoglyph attacks including those within a single character set, such as the use of "í" in place of "i" or "ì", "ت" for "ث", or "1" for "l". When the reviewer judges that the result is misleading or confusing, the relevant code does not meet the [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m) requirements.

See also the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements): [**\[S\] No Unicode Direction Control Characters**](https://entethalliance.org/specs/ethtrust-sl/#req-1-unicode-bdo).

#### 4.2.2 External Calls[](https://entethalliance.org/specs/ethtrust-sl/#sec-2-external-calls)

**\[M\] Protect External Calls [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls)**  
For [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls:

*   all addresses called by the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ correspond to the exact code of the [Set of Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts) tested, **and**
*   all contracts called _MUST_ be within the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), **and**
*   all contracts called _MUST_ be controlled by the same entity, **and**
*   the protection against [Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-re-entrancy-attacks) for the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be equivalent to what the [Checks-Effects-Interactions](https://entethalliance.org/specs/ethtrust-sl/#dfn-checks-effects-interactions) pattern offers,

**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls),
*   [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented),
*   [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), **and**
*   [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented).

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i).

[EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m) allows calling within a [set of contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts) that form part of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code). This ensures all contracts called are audited together at this Security Level.

If a contract calls a well-known external contract that is not audited as part of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), it is possible to certify conformance to this requirement through the [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement), which allow the certifier to claim on their own judgement that the contracts called provide appropriate security. The extended requirements around documentation of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that apply when claiming conformance through implementation of the [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) in this case reflect the potential for very high risk if the external contracts are simply assumed by a reviewer to be secure because they have been widely used.

Unless the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) deploys contracts, and retrieves their address accurately for calling, it is necessary to check that the contracts are really deployed at the addresses assumed in the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

The same level of protection against [Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-re-entrancy-attacks) has to be provided to the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) overall as for the [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s) requirement.

**\[M\] Avoid Read-only Re-entrancy Attacks [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-avoid-readonly-reentrancy)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls _MUST_ protect itself against [Read-only Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-read-only-re-entrancy-attack).

As described in [§ 3.4 External Interactions and Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#sec-reentrancy-considerations), code that reads information from a function can end up reading inconsistent or incorrect information. When the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) calls a function in which this possibility arises, the calling code needs an appropriate mechanism to avoid it happening.

One potential mechanism is for view functions to have a modifier that checks whether the data is currently in an inconsistent state, in the manner of a lock function. This enables calling code to explicitly avoid viewing inconsistent data.

Warning

**\[M\] Handle External Call Returns [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-handle-return)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls _MUST_ reasonably handle possible errors.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] Check External Calls Return**](https://entethalliance.org/specs/ethtrust-sl/#req-1-check-return).

It is important that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) works as expected, to the satisfaction of the auditor, when the return value is the result of a possible error, such as if a call to a non-existent function triggers a fallback function instead of simply reverting, or an external call using a low-level function does not revert.

See also the [related requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements): [**\[Q\] Process All Inputs**](https://entethalliance.org/specs/ethtrust-sl/#req-3-all-valid-inputs).

#### 4.2.3 Documented Defensive Coding[](https://entethalliance.org/specs/ethtrust-sl/#sec-2-special-code)

**\[M\] Document Special Code Use [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ document the need for each instance of:

*   `CREATE2`,
*   `assembly {}`,
*   `selfdestruct()` or its deprecated alias `suicide()`,
*   external calls,
*   `delegatecall()`,
*   code that can cause an overflow or underflow,
*   `block.number` or `block.timestamp`, **or**
*   Use of oracles and pseudo-randomness,

**and** _MUST_ describe how the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) protects against misuse or errors in these cases, **and** the documentation _MUST_ be available to anyone who can call the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

This is part of several [Sets of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements), one for each of

*   [**\[S\] No `CREATE2`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-create2),
*   [**\[S\] No `selfdestruct()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-self-destruct),
*   [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly),
*   [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i),
*   [**\[S\] No Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-1-overflow-underflow), and
*   [**\[S\] No `delegatecall()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-delegatecall).

There are legitimate uses for all of these coding patterns, but they are also potential causes of security vulnerabilities. [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m) therefore requires testing that the use of these patterns is explained and justified, and that they are used in a manner that does not introduce known vulnerabilities.

The requirement to document the use of external calls applies to **all** external calls in the tested code, whether or not they meet the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i).

See also the [Related requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements): [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented), [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented), [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls), [**\[M\] Avoid Common `assembly {}` Attack Vectors**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-assembly), [**\[M\] Compiler Bug SOL-2022-5 in `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly), [**\[M\] Compiler Bug SOL-2022-4**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-4), and [**\[M\] Compiler Bug SOL-2021-3**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2021-3).

**\[M\] Ensure Proper Rounding of Computations Affecting Value [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-check-rounding)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ identify and protect against exploiting rounding errors:

*   The possible range of error introduced by such rounding _MUST_ be documented.
*   [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ unintentionally create or lose value through rounding.
*   [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ apply rounding in a way that does not allow round-trips "creating" value to repeat causing unexpectedly large transfers.

Smart Contracts typically implement mathematical formulas over real numbers using integer arithmetic. Such code can introduce rounding errors because integers and rational numbers whose size is bounded cannot precisely represent all real numbers in the same range.

If a procedure that uses rounding results in a predictable amount of error, that increases the value produced by the round-trip, it is possible to exploit that difference by repeating the procedure to cumulatively siphon a large sum.

Warning

To protect against this vulnerability, the "Keep the Change" approach ensures that any difference created does not provide an advantage to an attacker repeatedly calling a smart contract. It is important to note that differences do still accrue. A contract could use "over-servicing", repeatedly calling a swap protected by the "Keep the Change" approach, to steal from a user.

This vulnerability has been discovered in practice in DeFi protocol Smart Contracts that could have put hundreds of millions of dollars at risk. Further explanation is available in the [presentation slides](https://archive.devcon.org/resources/6/tackling-rounding-errors-with-precision-analysis.pdf) for the DevCon 2023 talk \[[DevCon-rounding](https://entethalliance.org/specs/ethtrust-sl/#bib-devcon-rounding "Tackling Rounding Errors with Precision Analysis")\]. An example of a thorough mathematical analysis of integer rounding for an automated market maker is available in \[[rounding-errors](https://entethalliance.org/specs/ethtrust-sl/#bib-rounding-errors "Formal Specification of Constant Product (x × y = k) Market Maker Model and Implementation")\].

This requirement is based on \[[CWE-1339](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-1339 "CWE-1339: Insufficient Precision or Accuracy of a Real Number")\] Insufficient Precision or Accuracy of a Real Number.

**\[M\] Protect Self-destruction [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that contains the `selfdestruct()` or `suicide()` instructions _MUST_

*   ensure that only authorised parties can call the method, **and**
*   _MUST_ protect those calls in a way that is fully compatible with the claims of the contract author,

**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[Q\] Enforce Least Privilege**](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control).

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No `selfdestruct()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-self-destruct).

If the `selfdestruct()` instruction (or its deprecated alternative `suicide()`) is not carefully protected, malicious code can call it and destroy a contract, and potentially steal any Ether held by the contract. In addition, this can disrupt other users of the contract since once the contract has been destroyed any Ether sent is simply lost, unlike when a contract is disabled which causes a transaction sending Ether to revert.

See also [SWC-106](https://swcregistry.io/docs/SWC-106) in \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\].

This vulnerability led to the [Parity MultiSig Wallet Failure](https://www.parity.io/blog/parity-technologies-multi-sig-wallet-issue-update/) that blocked around 1/2 Million Ether on mainnet in 2017.

**\[M\] Avoid Common `assembly {}` Attack Vectors [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-assembly)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use the `assembly {}` instruction to change a variable **unless** the code cannot:

*   create storage pointer collisions, **nor**
*   allow arbitrary values to be assigned to variables of type `function`.

This is part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

The `assembly {}` instruction provides a low-level method for developers to produce code in smart contracts. Using this approach provides great flexibility and control, for example to reduce gas cost. However it also exposes some possible attack surfaces where a malicious coder could introduce attacks that are hard to detect. This requirement ensures that two such attack surfaces that are well-known are not exposed.

See also [SWC-124](https://swcregistry.io/docs/SWC-124) and [SWC-127](https://swcregistry.io/docs/SWC-127) \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\], and the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented), [**\[M\] Compiler Bug SOL-2022-7**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-7), [**\[M\] Compiler Bug SOL-2022-5 in `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly), [**\[M\] Compiler Bug SOL-2022-4**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-4), and [**\[M\] Compiler Bug SOL-2021-3**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2021-3).

**\[M\] Protect `CREATE2` Calls [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-protect-create2)**  
For [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses the `CREATE2` instruction, any contract to be deployed using `CREATE2`

*   _MUST_ be within the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), **and**
*   _MUST NOT_ use any `selfdestruct()`, `delegatecall()` nor `callcode()` instructions, **and**
*   _MUST_ be fully compatible with the claims of the contract author,

**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls),
*   [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented),
*   [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), **and**
*   [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented).

This is part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `CREATE2`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-create2).

The `CREATE2` opcode's ability to interact with addresses whose code does not yet exist on-chain makes it important to prevent external calls to malicous or insecure contract code that is not yet known.

The [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) needs to include any code that can be deployed using `CREATE2`, to verify protections are in place and the code behaves as the contract author claims. This includes ensuring that opcodes that can change the immutability or forward calls in the contracts deployed with `CREATE2`, such as `selfdestruct()`, `delegatecall()` and `callcode()`, are not present.

If any of these opcodes are present, the additional protections and documentation required by the [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) are necessary.

**\[M\] No Overflow/Underflow [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-overflow-underflow)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain calculations that can overflow or underflow **unless**

*   there is a demonstrated need (e.g. for use in a modulo operation) and
*   there are guards around any calculations, if necessary, to ensure behavior consistent with the claims of the contract author.

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-1-overflow-underflow).

There are a few rare use cases where arithmetic overflow or underflow is intended, or expected behaviour. It is important such cases are protected appropriately. Note that these are harder to implement since Solidity compiler version 0.8.0 which introduced overflow protection that causes transactions to revert.

See also [SWC-101](https://swcregistry.io/docs/SWC-101) in \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\].

**\[M\] Document Name Conflicts [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-inheritance-order)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ clearly document the order of inheritance for each function or variable that shares a name with another function or variable.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Conflicting Names**](https://entethalliance.org/specs/ethtrust-sl/#req-1-inheritance-conflict).

As noted in [**\[S\] No Conflicting Names**](https://entethalliance.org/specs/ethtrust-sl/#req-1-inheritance-conflict). using the same name for different functions or variables can lead to reviewers misunderstanding code, either inadvertently or due to deliberately malicious code. Explicitly documenting any occurrences of doing this helps security audits, and makes it clear to others using the code where they need to pay close attention to the scope of variable or function declarations.

See also the [related requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Compiler Bug SOL-2020-2**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2020-2), and the [documentation of function inheritance](https://docs.soliditylang.org/en/latest/contracts.html#inheritance) in \[[solidity-functions](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-functions "Solidity Documentation: Contracts - Functions")\]

**\[M\] Sources of Randomness [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-random-enough)**  
Sources of randomness used in [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be sufficiently resistant to prediction that their purpose is met.

This requirement involves careful evaluation for each specific contract and case. Some uses of randomness rely on no prediction being more accurate than any other. For such cases, values that can be guessed at with some accuracy or controlled by miners or validators, like block difficulty, timestamps, and/or block numbers, introduces a vulnerability. Thus a "strong" source of randomness like an oracle service is necessary.

Other uses are resistant to "good guesses" because using something that is close but wrong provides no more likelihood of gaining an advantage than any other guess.

Warning

See also the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[S\] No Exact Balance Check**](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check), [**\[M\] Don't Misuse Block Data**](https://entethalliance.org/specs/ethtrust-sl/#req-2-block-data-misuse), and [**\[Q\] Protect against MEV Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev).

**\[M\] Don't Misuse Block Data [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-block-data-misuse)**  
Block numbers and timestamps used in [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ introduce vulnerabilities to [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) or similar attacks.

Block numbers are vulnerable to approximate prediction, although they are generally not reliably precise indicators of elapsed time. `block.timestamp` is subject to manipulation by malicious actors. It is therefore important that these data are not trusted by [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) to function as if they were highly reliable or random information.

The description of [SWC-116](https://swcregistry.io/docs/SWC-116) in \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\] includes some code examples for techniques to avoid, for example using `block.number / 14` as a proxy for elapsed seconds, or relying on `block.timestamp` to indicate a precise time has passed.

For low precision, such as "a few minutes", `block.number / 14 > 1000` can be sufficient on main net, or a blockchain with a similar regular block period of around 14 seconds. But using it to determine that e.g. "exactly 36 seconds" have elapsed fails the requirement. A contract that relies on a specific block period can introduce serious risks if it is deployed on another blockchain with a very different block frequency.

Likewise, because block.timestamp depends on settings that can be manipulated by a malicious node operator, in cases likes Ethereum mainnet it is suitable for use as a coarse-grained approximation (on a scale of minutes) but the same code on a different blockchain can be vulnerable to [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) attacks.

Note that this is related to the use of [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles), which can also provide inaccurate information.

See also the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[S\] No Exact Balance Check**](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check), [**\[M\] Sources of Randomness**](https://entethalliance.org/specs/ethtrust-sl/#req-2-random-enough), and [**\[Q\] Protect against MEV Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev).

#### 4.2.4 Signature Management[](https://entethalliance.org/specs/ethtrust-sl/#sec-2-signature-requirements)

**\[M\] Proper Signature Verification [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-signature-verification)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ properly verify signatures to ensure authenticity of messages that were signed off-chain.

Some smart contracts process messages that were signed off-chain to increase flexibility, while maintaining authenticity. Smart contracts performing their own signature verification need to verify such messages' authenticity.

Using `ecrecover()` for signature verification, it is important to validate the address returned against the expected outcome. In particular, a return value of `address(0)` represents a failure to provide a valid signature.

See also [SWC-122](https://swcregistry.io/docs/SWC-122) \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\].

For code that does use `ecrecover()`, see the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Use a Modern Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-060).

**\[M\] No Improper Usage of Signatures for Replay Attack Protection [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-malleable-signatures-for-replay)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) using signatures to prevent replay attacks _MUST_ ensure that signatures cannot be reused:

*   In the same function to verify the same message,
*   In more than one function to verify the same message within the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code),
*   In more than one contract address to verify the same message, in which the same account(s) may be signing messages, **and**
*   In the same contract address across multiple chains.

**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[Q\] Intended Replay**](https://entethalliance.org/specs/ethtrust-sl/#req-3-intended-replay). Additionally, [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ verify that multiple signatures cannot be created for the same message, as is the case with [Malleable Signatures](https://entethalliance.org/specs/ethtrust-sl/#dfn-malleable-signatures).

In Replay Attacks, an attacker replays correctly signed messages to exploit a system. The signed message needs to include enough identifying information so that its intended setting is well-defined.

[Malleable Signatures](https://entethalliance.org/specs/ethtrust-sl/#dfn-malleable-signatures) allow an attacker to create a new signature for the same message. Smart contracts that check against hashes of signatures to ensure that a message has only been processed once could be vulnerable to replay attacks if malleable signatures are used.

#### 4.2.5 Security Level \[M\] Compiler Bugs and Overriding Requirements[](https://entethalliance.org/specs/ethtrust-sl/#sec-level-2-compiler-bugs)

Some solidity compiler bugs described in [§ 4.1.4 Compiler Bugs](https://entethalliance.org/specs/ethtrust-sl/#sec-1-compiler-bugs) have [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) at [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m), and some have trigger conditions that are not readily detectable in software.

Note

Implementing the Recommended Good Practice [**\[GP\] Use Latest Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-R-use-latest-compiler) means that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) passes all requirements in this subsection.

**\[M\] Solidity Compiler Bug 2023-1 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2023-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that contains a compound expression with side effects that uses `.selector` _MUST_ use the viaIR option with Solidity compiler versions between 0.6.2 and 0.8.20 inclusive.

A bug introduced in Solidity compiler version 0.6.2 and fixed in Solidity compiler version 0.8.21 meant that when compound expressions accessed the `.selector` member, the expression would not be evaluated, unless the viaIR pipeline was used. Thus any side effects caused by the expression would not occur.

See also the [19 July 2023 security alert](https://blog.soliditylang.org/2023/07/19/missing-side-effects-on-selector-access-bug/).

**\[M\] Compiler Bug SOL-2022-7 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-7)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that has storage writes followed by conditional early terminations from inline assembly functions containing `return()` or `stop()` instructions _MUST NOT_ use a Solidity compiler version between 0.8.13 and 0.8.17 inclusive.  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

A bug fixed in Solidity compiler version 0.8.17 meant that storage writes followed by conditional early terminations from inline assembly functions would sometimes be erroneously dropped during optimization.

See also the [5 September 2022 security alert](https://blog.soliditylang.org/2022/09/08/storage-write-removal-before-conditional-termination/).

**\[M\] Compiler Bug SOL-2022-5 in `assembly {}` [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies `bytes` arrays from calldata or memory whose size is not a multiple of 32 bytes, and has an `assembly {}` instruction that reads that data without explicitly matching the length that was copied, _MUST NOT_ use a Solidity compiler version older than 0.8.15.  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

Until Solidity compiler version 0.8.15 copying `memory` or `calldata` whose length is not a multiple of 32 bytes could expose data beyond the data copied, which could be observable using `assembly {}`.

See also the [15 June 2022 security alert](https://blog.soliditylang.org/2022/06/15/dirty-bytes-array-to-storage-bug/) and [related requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[S\] Compiler Bug SOL-2022-5 with `.push()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-5-push), [**\[M\] Avoid Common `assembly {}` Attack Vectors**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-assembly), [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented), [**\[M\] Compiler Bug SOL-2022-4**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-4), and [**\[M\] Compiler Bug SOL-2021-3**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2021-3).

**\[M\] Compiler Bug SOL-2022-4 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-4)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that has at least two `assembly {}` instructions, such that one writes to memory e.g. by storing a value in a variable, but does not access that memory again, and code in a another `assembly {}` instruction refers to that memory, _MUST NOT_ use the yulOptimizer with Solidity compiler versions 0.8.13 or 0.8.14.  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

Solidity compiler version 0.8.13 introduced a yulOptimizer bug, fixed in Solidity compiler version 0.8.15, where memory created in an `assembly {}` instruction but only read in a different `assembly {}` instruction was discarded.

See also the [17 June 2022 security alert](https://blog.soliditylang.org/2022/06/15/inline-assembly-memory-side-effects-bug/) and [related requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Avoid Common `assembly {}` Attack Vectors**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-assembly), [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented), [**\[M\] Compiler Bug SOL-2022-7**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-7), [**\[M\] Compiler Bug SOL-2022-5 in `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly), and [**\[M\] Compiler Bug SOL-2021-3**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2021-3).

**\[M\] Compiler Bug SOL-2021-3 [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2021-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that reads an `immutable` signed integer of a `type` shorter than 256 bits within an `assembly {}` instruction _MUST NOT_ use a Solidity compiler version between 0.6.5 and 0.8.8 (inclusive).  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

Solidity compiler version 0.6.8 introduced a bug, fixed in Solidity compiler version 0.8.9, that meant immutable signed integer types shorter than 256 bits could be read incorrectly in inline `assembly {}` instructions.

See also the [29 September 2021 security alert](https://blog.soliditylang.org/2021/09/29/signed-immutables-bug/), and the [related requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[M\] Safe Use of `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-assembly), [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented), [**\[M\] Compiler Bug SOL-2022-5 in `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly), and [**\[M\] Compiler Bug SOL-2022-4**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-4).

**\[M\] Compiler Bug Check Constructor Payment [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-check-payable-constructor)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that allows payment to a constructor function that is

*   defined in a base contract, **and**
*   used by default in another contract without an explicit constructor, **and**
*   not explicity marked `payable`,

_MUST NOT_ use a Solidity compiler version between 0.4.5 and 0.6.7 (inclusive).  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] Compiler Bug SOL-2020-5**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-5).

Solidity compiler versions from 0.4.5 set the expectation that payments to a constructor that was not expicitly denoted as `payable` would revert. But when the constructor is inherited from a base contract, this reversion does not happen using Solidity compiler versions before 0.6.8.

See also the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[S\] Use a Modern Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-060), covering Solidity Compiler bugs that require review for [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s).

### 4.3 Security Level \[Q\][](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-three)

In addition to automatable static testing verification ([Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s)), and a manual audit ([Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m)), [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at Security Level \[Q\] means checking that the intended functionality of [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) is sufficiently well documented that its functional correctness can be verified, that the code and documentation has been thoroughly reviewed by a human auditor or audit team to ensure that they are both internally coherent and consistent with each other, carefully enough to identify complex security vulnerabilities.

This level of review is especially relevant for tokens using ERC20 \[[ERC20](https://entethalliance.org/specs/ethtrust-sl/#bib-erc20 "EIP-20: Token Standard")\], ERC721 \[[ERC721](https://entethalliance.org/specs/ethtrust-sl/#bib-erc721 "ERC 721: Non-fungible Token Standard")\], and others; \[[token-standards](https://entethalliance.org/specs/ethtrust-sl/#bib-token-standards "Ethereum Development Documentation - Token Standards")\] identifies a number of other standards that can define tokens.

At this Security Level there are also checks to ensure the code does not contain errors that do not directly impact security, but do impact code quality. Code is often copied, so [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q) requires code to be as well-written as possible. The risk being addressed is that it is easy, and not uncommon, to introduce weaknesses by copying existing code as a starting point.

**\[Q\] Pass Security Level \[M\] [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-pass-l2)**  
To be eligible for [EEA EthTrust certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q), [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ meet the requirements for [§ 4.2 Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-two).

**\[Q\] Code Linting [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-linted)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code)

*   _MUST NOT_ create unnecessary variables, **and**
*   _MUST NOT_ include code that cannot be reached in execution  
    **except** for code explicitly intended to manage unexpected errors, such as `assert()` statements, **and**
*   _MUST NOT_ contain a function that has the same name as the smart contract **unless** it is explicitly declared as a constructor using the `constructor` keyword, **and**
*   _MUST_ explicitly declare the visibility of all functions and variables.

Code is often copied from "good examples" as a starting point for development. Code that has achieved [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q) [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) is meant to be high quality, so it is important to ensure that copying it does not encourage bad habits. It is also helpful for review to remove pointless code.

Code designed to trap unexpected errors, such as `assert()` instructions, is explicitly allowed, because it would be very unfortunate if defensively written code that successfully eliminates the possibility of triggering a particular error could not achieve [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified).

**\[Q\] Manage Gas Use Increases [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-enough-gas)**  
Sufficient Gas _MUST_ be available to work with data structures in the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that grow over time, in accordance with descriptions provided for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented).

Some structures such as arrays can grow, and the value of variables is (by design) variable. Iterating over a structure whose size is not clear in advance, whether an array that grows, a bound that changes, or something determined by an external value, can result in significant increases in gas usage.

What is reasonable growth to expect needs to be considered in the context of the business logic intended, and how the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) protects against [Gas Griefing](https://entethalliance.org/specs/ethtrust-sl/#dfn-gas-griefing) attacks, where malicious actors or errors result in values occurring beyond the expected reasonable range(s).

See also [SWC-126](https://swcregistry.io/docs/SWC-126), [SWC-128](https://swcregistry.io/docs/SWC-128) \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\] and the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) in [§ 4.3.1 Documentation requirements](https://entethalliance.org/specs/ethtrust-sl/#sec-3-documentation).

**\[Q\] Protect Gas Usage [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-gas)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ protect against malicious actors stealing or wasting gas.

Smart contracts allowing "gasless" transactions enable users to submit transactions without having to supply their own gas. They need to be carefully implemented to prevent Denial of Service from [Gas Griefing](https://entethalliance.org/specs/ethtrust-sl/#dfn-gas-griefing) and [Gas Siphoning](https://entethalliance.org/specs/ethtrust-sl/#dfn-gas-siphoning) attacks.

See also [The Gas Siphon Attack: How it Happened and How to Protect Yourself](https://archive.devcon.org/archive/watch/5/the-gas-siphon-attack-how-it-happened-and-how-to-protect-yourself/) from the DevCon 2019 talk \[[DevCon-siphoning](https://entethalliance.org/specs/ethtrust-sl/#bib-devcon-siphoning "The Gas Siphon Attack: How it Happened and How to Protect Yourself")\].

**\[Q\] Protect against Oracle Failure [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-check-oracles)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ protect itself against malfunctions in [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) it relies on.

Some [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) are known to be vulnerable to manipulation, for example because they derive the information they provide from information vulnerable to [Read-only Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-read-only-re-entrancy-attack), or manipulation of prices through the use of flashloans to enable an [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) attack, among other well-known attacks.

In addition, as networked software [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) can potentially suffer problems ranging from latency issues to outright failure, or being discontinued.

It is important to check the mechanism used by an [Oracle](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) to generate the information it provides, and the potential exposure of [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that relies on that [Oracle](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) to the effects of it failing, or of malicious actors manipulating its inputs or code to enable attacks.

See also the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[Q\] Protect against Front-running**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-front-running), and [**\[Q\] Protect against MEV Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev).

**\[Q\] Protect against Front-Running [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-front-running)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ require information in a form that can be used to enable a [Front-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running) attack.

In [Front-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running) attacks, an attacker places their transaction in front of a victim's. This can be done by a malicious miner or by an attacker monitoring the mempool, and preempting susceptible transactions by broadcasting their own transactions with higher transaction fees. Removing incentives to front-run generally means applying mitigations such as hash commitment schemes \[[hash-commit](https://entethalliance.org/specs/ethtrust-sl/#bib-hash-commit "Commitment scheme - WikiPedia")\] or batch execution.

See also the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[Q\] Protect against Front-running**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-front-running).

**\[Q\] Protect against MEV Attacks [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that is susceptible to [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) attacks _MUST_ follow appropriate design patterns to mitigate this risk.

[MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) refers to the potential that a block producer can maliciously reorder or suppress transactions, or another participant in a blockchain can propose a transaction or take other action to gain a benefit that was not intended to be available to them.

This requirement entails a careful judgement by the auditor, of how the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) is vulnerable to [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) attacks, and what mitigation strategies are appropriate. Some approaches are discussed further in [§ 3.7 MEV (Maliciously Extracted Value)](https://entethalliance.org/specs/ethtrust-sl/#sec-mev-considerations).

Many attack types need to be considered, including at least [Censorship Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-censorship-attacks), [Future Block Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-future-block-attacks), and [Timing Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-timing-attacks) ([Front-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running), [Back-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-back-running), and [Sandwich Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-sandwich-attacks)).

See also the [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[S\] No Exact Balance Check**](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check), [**\[M\] Sources of Randomness**](https://entethalliance.org/specs/ethtrust-sl/#req-2-random-enough), [**\[M\] Don't Misuse Block Data**](https://entethalliance.org/specs/ethtrust-sl/#req-2-block-data-misuse), and [**\[Q\] Protect against Oracle Failure**](https://entethalliance.org/specs/ethtrust-sl/#req-3-check-oracles), and [**\[Q\] Protect against Front-running**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-front-running).

**\[Q\] Protect Against Governance Takeovers [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-governance)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) which includes a governance system _MUST_ protect against one external entity taking control via exploit of the governance design.

Governance attacks are specific to the system that is exploited. Depending on the governance proposal system, some areas of vulnerability may include:

*   The issued governance token;
*   The method of distribution for the governance token;
*   The design of the acceptance and execution of governance proposals.

For example, if a staking contract is used to distribute governance tokens as a reward, it is important that the staking contract is not vulnerable to a Flash Loan Attack, where a large amount of tokens are borrowed in a very short-term flash loan, then staked atomically to gain a temporary majority of governance tokens, that are then used to make a governance decision, such as draining all the funds held to an attacker's wallet.

**\[Q\] Process All Inputs [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-all-valid-inputs)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ validate inputs, and function correctly whether the input is as designed or malformed.

Code that fails to validate inputs runs the risk of being subverted through maliciously crafted input that can trigger a bug, or behaviour the authors did not anticipate.

See also [SWC-123](https://swcregistry.io/docs/SWC-123) \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\] which notes that it is important to consider whether input requirements are too strict, as well as too lax, \[[CWE-573](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-573 "CWE-573: Improper Following of Specification by Caller")\] Improper Following of Specification by Caller, and note that there are several [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) that are specific to particular Solidity compiler versions in [§ 4.1.4 Compiler Bugs](https://entethalliance.org/specs/ethtrust-sl/#sec-1-compiler-bugs).

**\[Q\] State Changes Trigger Events [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-event-on-state-change)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ emit a contract event for all transactions that cause state changes.

Events are convenience interfaces that give an abstraction on top of the EVM's logging functionality. Applications can subscribe and listen to these events through the RPC interface of an Ethereum client. See more at \[[solidity-events](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-events "Solidity Documentation: Contracts - Events")\].

Events are generally expected to be used for logging all state changes as they are not just useful for off-chain applications but also security monitoring and debugging. Logging all state changes in a contract ensures that any developers interacting with the contract are made aware of every state change as part of the ABI and can understand expected behavior through event annotations, as per [**\[Q\] Annotate Code with NatSpec**](https://entethalliance.org/specs/ethtrust-sl/#req-3-annotate).

**\[Q\] No Private Data [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-no-private-data)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ store [Private Data](https://entethalliance.org/specs/ethtrust-sl/#dfn-private-data) on the blockchain.

This is a [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q) requirement primarily because the question of what is private data often requires careful and thoughtful assessment and a reasoned understanding of context. In general, this is likely to include an assessment of how the data is gathered, and what the providers of data are told about the usage of the information.

Private Data is used in this specification to refer to information that is not intended to be generally available to the public. For example, an individual's home telephone number is generally private data, while a business' customer enquiries telephone number is generally not private data. Similarly, information identifying a person's account is normally private data, but there are circumstances where it is public data. In such cases, that public data can be recorded on-chain in conformance with this requirement.

Warning

PLEASE NOTE: In some cases regulation such as the \[[GDPR](https://entethalliance.org/specs/ethtrust-sl/#bib-gdpr "Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016         on the protection of natural persons with regard to the processing of personal data         and on the free movement of such data, and repealing Directive 95/46/EC (General Data Protection Regulation)         (Text with EEA relevance)")\] imposes formal legal requirements on some private data. However, performing a test for this requirement results in an expert technical opinion on whether data that the auditor considers private is exposed. A statement about whether [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) meets this requirement does not represent any form of legal advice or opinion, attorney representation, or the like.

**\[Q\] Intended Replay [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-intended-replay)**  
If a signature within the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) can be reused, the replay instance _MUST_ be intended, documented, **and** safe for re-use.

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[M\] No Improper Usage of Signatures for Replay Attack Protection**](https://entethalliance.org/specs/ethtrust-sl/#req-2-malleable-signatures-for-replay).

In some rare instances, it may be the intention of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) to allow signatures to be replayed. For example, a signature may be used as permission to participate in a whitelist for a given period of time. In these exceptional cases, the replay must be included in documentation as a known allowance. Further, it must be verified that the reuse cannot be exploited.

#### 4.3.1 Documentation requirements[](https://entethalliance.org/specs/ethtrust-sl/#sec-3-documentation)

[Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q) conformance requires a detailed description of how the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) is **intended** to behave. Alongside detailed testing requirements to check that it does behave as described wth regard to specific known vulnerabililies, it is important that the claims made for it are accurate. This requirement helps ensure that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) fulfils claims made for it outside audit-specific documentation.

The combination of these requirements helps ensure there is no malicious code, such as malicious "back doors" or "time bombs" hidden in the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code). Since there are legitimate use cases for code that behaves as e.g. a time bomb, or "phones home", this combination helps ensure that testing focuses on real problems.

The requirements in this section extend the coverage required to meet the [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m) requirement [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented). As with that requirement, there are multiple requirements at this level that require the documentation mandated in this subsection.

**\[Q\] Document Contract Logic [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented)**  
A specification of the business logic that the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) functionality is intended to implement _MUST_ be available to anyone who can call the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

Contract Logic documented in a human-readable format and with enough detail that functional correctness and safety assumptions for special code use can be validated by auditors helps them assess complex code more efficiently and with higher confidence.

It is important to document how the logic protects against potential attacks such as Flash Loan attacks (especially on governance or price manipulation), MEV, and other complex attacks that take advantage of ecosystem features or tokenomics.

**\[Q\] Document System Architecture [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system)**  
Documentation of the system architecture for the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be provided that conveys the overrall system design, privileged roles, security assumptions and intended usage.

System documentation provides auditor(s) information to understand security assumptions and ensure functional correctness. It is helpful if system documentation is included or referenced in the README file of the code repository, alongside documentation for how the source code can be tested, built and deployed.

See also the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[Q\] Annotate Code with NatSpec**](https://entethalliance.org/specs/ethtrust-sl/req-3-annotate).

**\[Q\] Annotate Code with NatSpec [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-annotate)**  
All [Public Interfaces](https://entethalliance.org/specs/ethtrust-sl/#dfn-public-interfaces) contained in the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be annotated with inline comments according to the \[[NatSpec](https://entethalliance.org/specs/ethtrust-sl/#bib-natspec "NatSpec Format - Solidity Documentation")\] format that explain the intent behind each function, parameter, event, and return variable, along with developer notes for safe usage.

Inline comments are important to ensure that developers and auditors understand the intent behind each function and other code components. Public Interfaces means anything that would be contained in the ABI of the compiled [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code). It is also recommended to use inline comments for private or internal functions that implement sensitive and/or complex logic.

Following the \[[NatSpec](https://entethalliance.org/specs/ethtrust-sl/#bib-natspec "NatSpec Format - Solidity Documentation")\] format allows these inline comments to be understood by the Solidity compiler for extracting them into a machine-readable format that could be used by other third-party tools for security assessments and automatic documentation, including documentation shown to users by wallets that integrate with source code verification tools like [Sourcify](https://sourcify.dev/). This could also be used to generate specifications that fully or partially satisfy the Requirement to [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented).

**\[Q\] Implement as Documented [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented)**  
The [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ behave as described in the documentation provided for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented), **and** [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system).

The requirements at [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q) to provide documentation are important. However, it is also crucial that the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) actually behaves as documented. If it does not, it is possible that this reflects insufficient care and that the code is also vulnerable due to bugs that were missed in implementation. It is also possible that the difference is an attempt to hide malicious code in the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

#### 4.3.2 Access Control[](https://entethalliance.org/specs/ethtrust-sl/#sec-3-access-control)

**\[Q\] Enforce Least Privilege [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that enables privileged access _MUST_ implement appropriate access control mechanisms that provide the least privilege necessary for those interactions, based on the documentation provided for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented).  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[M\] Protect Self-destruction**](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct).

There are several common methods to implement access control, such as Role-Based Access Control \[[RBAC](https://entethalliance.org/specs/ethtrust-sl/#bib-rbac "INCITS 359-2012: Information Technology - Role Based Access Control")\] and \[[Ownable](https://entethalliance.org/specs/ethtrust-sl/#bib-ownable "ERC-173: Contract Ownership Standard")\], and bespoke access control is often implemented for a given use case. Using industry-standard methods can help simplify the process of auditing, but is not sufficient to determine that there are no risks arising either from errors in implementation or due to a maliciously-crafted contract.

It is important to consider access control at both the protocol operation and deployment levels. If a protocol is deployed in a deterministic manner, for example allowing a multi-chain deployment to have the same address across all chains, it is important to explicitly set an owner rather than defaulting to `msg.sender`, as that may leave a simple factory deployment contract as the insufficent new admin of your protocol.

It is particularly important that appropriate access control applies to payments, as noted in [SWC-105](https://swcregistry.io/docs/SWC-105), but other actions such as overwriting data as described in [SWC-124](https://swcregistry.io/docs/SWC-126), or changing specific access controls, also need to be appropriately protected \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\]. This requirement matches \[[CWE-284](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-284 "CWE-284: Improper Access Control")\] Improper Access Control.

See also "[Access Restriction](https://fravoll.github.io/solidity-patterns/access_restriction.html)" in \[[solidity-patterns](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-patterns "Solidity Patterns")\].

**\[Q\] Use Revocable and Transferable Access Control Permissions [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-revocable-permisions)**  
If the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) makes uses of Access Control for privileged actions, it _MUST_ implement a mechanism to revoke and transfer those permissions.

Privileged Accounts can perform administrative tasks on the [Set of Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts). If those accounts are compromised or responsibility to perform those tasks is assigned to different people, it is important to have a mechanism to revoke and transfer those permissions.

**\[Q\] No Single Admin EOA for Privileged Actions [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-no-single-admin-eoa)**  
If the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) makes uses of Access Control for privileged actions, it _MUST_ ensure that all critical administrative tasks require multiple signatures to be executed, unless there is a multisg admin that has greater privileges and can revoke permissions in case of a compromised or rogue EOA and reverse any adverse action the EOA has taken.

Privileged accounts can perform administrative tasks on the [Set of Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts). If a single EOA can perform these actions, and that permission cannot be revoked, the risks to a Smart Contract posed by a compromised or lost private key can be existential.

**\[Q\] Verify External Calls [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that contains external calls

*   _MUST_ document the need for them, **and**
*   _MUST_ protect them in a way that is fully compatible with the claims of the contract author.

This is part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i), and for [**\[M\] Protect External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls).

At [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q) auditors have a lot of flexibility to offer [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) for different uses of External Calls.

This requirement effectively allows a reviewer to declare that the destination of an external call is not a security risk. It is important to note that any such declaration reflects very closely on the reputation of a reviewer.

It is inappropriate to assume that a smart contract is secure just because it is widely used, and it is unacceptable to assume that a smart contract provided by a user in the future will be secure - this is a known vector that has been used for many serious security breaches.

It is also important to consider how any code referenced and declared safe by the reviewer could be vulnerable to attacks based on its use of external calls.

To take a common example, swap contracts that allow a user to provide any pair of token contracts are potentially at risk if one of those contracts is malicious, or simply vulnerable, in a way the swap contract does not anticipate and protect against.

See also the related requirements [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented), [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), **and** [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented).

**\[Q\] Verify `tx.origin` Usage [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-verify-tx.origin)**  
For [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses `tx.origin`, each instance

*   _MUST_ be consistent with the stated security and functionality objectives of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), **and**
*   _MUST NOT_ allow assertions about contract functionality made for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented) or [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system) to be violated by another contract, even where that contract is called by a user authorized to interact directly with the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No `tx.origin`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-tx.origin).

`tx.origin` can be used to enable phishing attacks, tricking a user into interacting with a contract that gains access to all the funds in their account. It is generally the wrong choice for authorization of a caller for which `msg.sender` is the safer choice.

See also [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented), [**\[Q\] Enforce Least Privilege**](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control), the [section "`tx.origin`"](https://docs.soliditylang.org/en/latest/security-considerations.html?highlight=tx.origin) in Solidity Security Considerations \[[solidity-security](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-security "Security Considerations - Solidity Documentation.")\], and CWE 284: Improper Access Control \[[CWE-284](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe-284 "CWE-284: Improper Access Control")\].

### 4.4 Recommended Good Practices[](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations)

This section describes good practices that require substantial human judgement to evaluate. Testing for, and meeting these requirements does not directly affect conformance to this document. Note however that meeting the Recommended Good Practice [**\[GP\] Meet as Many Requirements as Possible**](https://entethalliance.org/specs/ethtrust-sl/#req-R-meet-all-possible) will in practice mean that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) meets all the Requirements based on Compiler Bugs, including the majority of Requirements for [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s).

**\[GP\] Check For and Address New Security Bugs [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-check-new-bugs)**  
Check \[[solidity-bugs-json](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-bugs-json "A JSON-formatted list of some known security-relevant Solidity bugs")\] and other sources for bugs announced after 1 November 2023 and address them.

This version of the specification was finalized late in 2023. New vulnerabilities are discovered from time to time, on an unpredictable schedule. The latest solidity compiler bug accounted for in this version is SOL-2023-3.

Checking for security alerts published too late to be incorporated into the current version of this document is an important technique for maintaining the highest possible security.

There are other sources of information on new security vulnerabilities, from \[[CWE](https://entethalliance.org/specs/ethtrust-sl/#bib-cwe "Common Weakness Enumeration")\] to following the blogs of many security-oriented organizations such as those that contributed to this specification.

**\[GP\] Meet as Many Requirements as Possible [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-meet-all-possible)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ meet as many requirements of this specification as possible at Security Levels above the Security Level for which it is certified.

While meeting some requirements for a higher [EEA EthTrust certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) Security Level makes no change to the formal conformance level of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), each requirement is specified because meeting it provides protection against specific known attacks. If it is possible to meet a particular requirement, even if it is not necessary for conformance at the [Security Level](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-levels) being tested, meeting that requirement will improve the security of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) and is therefore worth doing.

**\[GP\] Use Latest Compiler [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-use-latest-compiler)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ use the latest available stable Solidity compiler version.

The Solidity compiler is regularly updated to improve performance but also specifically to fix security vulnerabilities that are discovered. There are many requirements in [§ 4.1.4 Compiler Bugs](https://entethalliance.org/specs/ethtrust-sl/#sec-1-compiler-bugs) that are related to vulnerabilities known at the time this specification was written, as well as enhancements made to provide better security by default. In general, newer Solidity compiler versions improve security, so unless there is a specific known reason not to do so, using the latest Solidity compiler version available will result in better security.

**\[GP\] Write Clear, Legible Solidity Code [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-clean-code)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ be written for easy understanding.

There are no strict rules defining how to write clear code. It is important to use sufficiently descriptive names, comment code appropriately, and use structures that are easy to understand without causing the code to become excessively large, because that also makes it difficult to read and understand.

Excessive nesting, unstructured comments, complex looping structures, and the use of very terse names for variables and functions are examples of coding styles that can also make code harder to understand.

It is important to note that in some cases, developers can sacrifice easy reading for other benefits such as reducing gas costs - this can be mitigated somewhat by comments in the code.

Likewise, for complex code involving multiple individual smart contracts, the way source is organised into files can help clarify or obscure what's happening. In particular, naming source code files to match the names of smart contracts they define is a common pattern that eases understanding.

This Good Practice extends somewhat the [Related Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements) [**\[Q\] Code Linting**](https://entethalliance.org/specs/ethtrust-sl/#req-3-linted), but judgements about how to meet it are necessarily more subjective than in the specifics that requirement establishes. Those looking for additional guidance on code styling can refer to the \[[Solidity-Style-Guide](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-style-guide "Solidity Style Guide - Solidity Documentation")\].

**\[GP\] Follow Accepted ERC Standards [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-follow-erc-standards)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ conform to finalized \[[ERC](https://entethalliance.org/specs/ethtrust-sl/#bib-erc "ERC Final - Ethereum Improvement Proposals")\] standards when it is reasonably capable of doing so for its use-case.

An ERC is a category of \[[EIP](https://entethalliance.org/specs/ethtrust-sl/#bib-eip "EIP-1: EIP Purpose and Guidelines")\] (Ethereum Improvement Proposal) that defines application-level standards and conventions, including smart contract standards such as token standards \[[ERC20](https://entethalliance.org/specs/ethtrust-sl/#bib-erc20 "EIP-20: Token Standard")\] and name registries \[[ERC137](https://entethalliance.org/specs/ethtrust-sl/#bib-erc137 "ERC-137: Ethereum Domain Name Service - Specification")\].

While following ERC standards will not inherently make Solidity code secure, they do enable developers to integrate with common interfaces and follow known conventions for expected behavior. If the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) does claim to follow a given ERC, its functional correctness in conforming to that standard can be verified by auditors.

**\[GP\] Define a Software License [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-define-license)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ define a software license

A software license provides legal guidance on how contributors and users can interact with the code, including auditors and whitehats. Because bytecode deployed to public networks can be read by anyone, it is common practice to use an Open-Source license for the Solidity code used to generate it.

It is important to choose a \[[software-license](https://entethalliance.org/specs/ethtrust-sl/#bib-software-license "Choosing an Open Source License")\] that best addresses the needs of the project, and clearly link to it throughout the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) and documentation, e.g. using a prominent LICENSE file in the code repository and referencing it from each source file.

**\[GP\] Disclose New Vulnerabilities Responsibly [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-notify-news)**  
Security vulnerabilities that are not addressed by this specification _SHOULD_ be brought to the attention of the Working Group and others through responsible disclosure as described in [§ 1.4 Feedback and new vulnerabilities](https://entethalliance.org/specs/ethtrust-sl/#sec-notifying-new-vulnerabilities).

New security vulnerabilities are discovered from time to time. It helps the efforts to revise this specification to ensure the Working Group is aware of new vulnerabilities, or new knowledge regarding existing known vulnerabilities.

The EEA has agreed to manage the specific email address security-notices@entethalliance.org for such notifications.

**\[GP\] Use Fuzzing [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-fuzzing-in-testing)**  
[Fuzzing](https://entethalliance.org/specs/ethtrust-sl/#dfn-fuzzing) _SHOULD_ be used to probe [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) for errors.

Fuzzing is an automated software testing method that repeatedly activates a contract, using a variety of invalid, malformed, or unexpected inputs, to reveal defects and potential security vulnerabilities.

Fuzzing can take days or even weeks: it is better to be patient than to stop it prematurely.

Fuzzing relies on a Corpus - A set of inputs for a fuzzing target. It is important to maintain the Corpus to maximise code coverage, and helpful to prune unnecessary or duplicate inputs for efficiency.

Many tools and input mutation methods can help to build the [Corpus](https://entethalliance.org/specs/ethtrust-sl/#dfn-corpus) for fuzzing. Good practice is to build on and leverage community resources where possible, always checking licensing restrictions.

Another important part of fuzzing is the set of specification rules that is checked throughout the fuzzing processes. While [Corpus](https://entethalliance.org/specs/ethtrust-sl/#dfn-corpus) is the set of inputs for fuzzing targets, the specification rules are business logic checks created specifically for fuzzing and are evaluated for each fuzzing input.

For a meaningful and efficient fuzzing campaign, it is not enough to send a large amount of random input to the contracts. This additional set of rules around the contracts should be present, so it gets triggered if fuzzing finds an edge case. The process shouldn't rely on the checks and reverts already within the contracts and the compiler.

As shown above, fuzzing rules and properties can be complex and may depend on specific contracts, functions, variables, their values before and/or after execution, and potentially many other things depending on the fuzzing technology and specification language of choice. If any vulnerabilities are discovered in the Solidity compiler by [Fuzzing](https://entethalliance.org/specs/ethtrust-sl/#dfn-fuzzing) please [disclose them responsibly](https://entethalliance.org/specs/ethtrust-sl/#sec-notifying-new-vulnerabilities).

**\[GP\] Use Formal Verification [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-formal-verification)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ undergo formal verification.

Formal verification is a family of techniques that can mathematically prove functional correctness of smart contracts. It has been used in other applications such as embedded systems. There are many uses for formal verification in smart contracts, such as testing liveness, protocol invariants for safety at a high level, or proving narrower, more specific properties of a program's execution.

In formal verification, a formal (symbolic or mathematical) specification of the expected or desired outcome of a smart contract is created, enabling a formal mathematical proof of a protocol's correctness. The smart contract itself is often translated into a formal language for this purpose.

Several languages and programs exist for creating fromal verification proofs, some with the explicit aim of making formal verification more accessible to casual users and non-mathematicians. Please see \[[EF-SL](https://entethalliance.org/specs/ethtrust-sl/#bib-ef-sl "Specification languages for creating formal specifications")\] for some examples.

When implemented correctly by a practitioner with experience and skill, formal verification can make guarantees that fuzzing and testing cannot provide. However, that is often difficult to achieve in practice. Formal verification requires substantial manual labor and expertise.

A comprehensive formal verification most likely has a much a higher cost and complexity than unit or integration testing, fuzzing, or other methods. The immutable nature of many smart contracts, and the complexity of upgrading contracts when it is possible, makes formal verification appealing to administrators and stakeholders of protocols.

**\[GP\] Select an Appropriate Threshold for Multisig Wallets [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-multisig-threshold)**  
Multisignature requirements for privileged actions _SHOULD_ have a sufficient number of signers, and NOT require "1 of N" nor all signatures.

Requiring multiple signatures for administrative actions has become the standard for many teams. When not managed carefully, they can become a source of attack even if the smart contract code is secure.

The problem with "1 of N" setups, that enable a single account to execute transactions, is that it is relatively easy to exploit. "N of N" setups meanwhile mean that if even one signer loses access to their account or will not approve an action, there is no possibility for approval. This can affect necessary operations such as the replacement of one signer with another, for example to ensure operational continuity, which can have a very serious impact.

Choosing a lower number of signatures to meet the requirement allows for quicker response, while a higher value requires stronger majority support. Consider using an "M of N" multisignature where M = (N/2) + 1, in other words, the smallest possible majority of signatures are necessary for approval, as a starting point. However it is important to consider how many potential signers there are, and the specific situations where signatures are needed, to determine a reasonably good value for M in a given case.

**\[GP\] Use TimeLock Delays for Sensitive Operations [🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-timelock-for-privileged-actions)**  
Sensitive operations that affect all or a majority of users _SHOULD_ use \[[TimeLock](https://entethalliance.org/specs/ethtrust-sl/#bib-timelock "Protect Your Users With Smart Contract Timelocks")\] delays.

Sensitive operations, such as upgrades and \[[RBAC](https://entethalliance.org/specs/ethtrust-sl/#bib-rbac "INCITS 359-2012: Information Technology - Role Based Access Control")\] changes impact all or a majority of users in the protocol. A \[[TimeLock](https://entethalliance.org/specs/ethtrust-sl/#bib-timelock "Protect Your Users With Smart Contract Timelocks")\] delay allows users to exit the system if they disagree with the proposed change, and allows developers to react if they detect a suspicious change.

A. Additional Information[](https://entethalliance.org/specs/ethtrust-sl/#sec-additional-information)
-----------------------------------------------------------------------------------------------------

### A.1 Defined Terms[](https://entethalliance.org/specs/ethtrust-sl/#sec-definitions)

The following is a list of terms defined in this Specification.

*   [Back-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-back-running)
*   [Censorship Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-censorship-attacks)
*   [Checks-Effects-Interactions](https://entethalliance.org/specs/ethtrust-sl/#dfn-checks-effects-interactions)
*   [Corpus](https://entethalliance.org/specs/ethtrust-sl/#dfn-corpus)
*   [EEA EthTrust Certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified)
*   [EVM](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm)
*   [EVM versions](https://entethalliance.org/specs/ethtrust-sl/#dfn-evm-version)
*   [Execution Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-execution-contract)
*   [Fixed-length Variable](https://entethalliance.org/specs/ethtrust-sl/#dfn-fixed-length-variable)
*   [Flash Loan Attack](https://entethalliance.org/specs/ethtrust-sl/#dfn-flash-loan-attack)
*   [Free Functions](https://entethalliance.org/specs/ethtrust-sl/#dfn-free-functions)
*   [Front-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running)
*   [Future Block Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-future-block-attacks)
*   [Fuzzing](https://entethalliance.org/specs/ethtrust-sl/#dfn-fuzzing)
*   [Gas Griefing](https://entethalliance.org/specs/ethtrust-sl/#dfn-gas-griefing)
*   [Gas Siphoning](https://entethalliance.org/specs/ethtrust-sl/#dfn-gas-siphoning)
*   [Gas Tokens](https://entethalliance.org/specs/ethtrust-sl/#dfn-gas-tokens)
*   [Hash Collisions](https://entethalliance.org/specs/ethtrust-sl/#dfn-hash-collisions)
*   [Homoglyph Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-homoglyph-attacks)
*   [Logic Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-logic-contract)
*   [Low-level Call Functions](https://entethalliance.org/specs/ethtrust-sl/#dfn-low-level-call-functions)
*   [Malleable Signatures](https://entethalliance.org/specs/ethtrust-sl/#dfn-malleable-signatures)
*   [Metamorphic Upgrade](https://entethalliance.org/specs/ethtrust-sl/#dfn-metamorphic-upgrade)
*   [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev)
*   [Network Upgrade](https://entethalliance.org/specs/ethtrust-sl/#dfn-hard-fork)
*   [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles)
*   [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement)
*   [Private Data](https://entethalliance.org/specs/ethtrust-sl/#dfn-private-data)
*   [Privileged Accounts](https://entethalliance.org/specs/ethtrust-sl/#dfn-privileged-accounts)
*   [Proxy Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-proxy-contract)
*   [Public Interfaces](https://entethalliance.org/specs/ethtrust-sl/#dfn-public-interfaces)
*   [Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-re-entrancy-attacks)
*   [Read-only Re-entrancy Attack](https://entethalliance.org/specs/ethtrust-sl/#dfn-read-only-re-entrancy-attack)
*   [Related Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-related-requirements)
*   [Sandwich Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-sandwich-attacks)
*   [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m)
*   [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q)
*   [Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-s)
*   [Security Levels](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-levels)
*   [Set Of Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts)
*   [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)
*   [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code)
*   [Timing Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-timing-attacks)
*   [TWAP](https://entethalliance.org/specs/ethtrust-sl/#dfn-twap)
*   [Unicode Direction Control Characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters)
*   [Upgradable Contract](https://entethalliance.org/specs/ethtrust-sl/#dfn-upgradable-contract)
*   [Valid Conformance Claim](https://entethalliance.org/specs/ethtrust-sl/#dfn-valid-conformance-claim)

### A.2 Summary of Requirements[](https://entethalliance.org/specs/ethtrust-sl/#sec-summary-of-requirements)

This section provides a summary of all requirements and recommended good practices in this Specification.

[**\[S\] Encode Hashes with `chainid`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-eip155-chainid) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-eip155-chainid)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ create hashes for transactions that incorporate `chainid` values following the recommendation described in \[[EIP-155](https://entethalliance.org/specs/ethtrust-sl/#bib-eip-155 "Simple Replay Attack Protection")\].

[**\[S\] No `CREATE2`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-create2) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-create2)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain a `CREATE2` instruction,  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[M\] Protect `CREATE2` Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-protect-create2), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

[**\[S\] No `tx.origin`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-tx.origin) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-tx.origin)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain a `tx.origin` instruction  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[Q\] Verify `tx.origin` Usage**](https://entethalliance.org/specs/ethtrust-sl/#req-3-verify-tx.origin)

[**\[S\] No Exact Balance Check**](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ test that the balance of an account is exactly equal to (i.e. `==`) a specified amount or the value of a variable  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] Verify Exact Balance Checks**](https://entethalliance.org/specs/ethtrust-sl/#req-2-verify-exact-balance-check).

[**\[S\] No Conflicting Names**](https://entethalliance.org/specs/ethtrust-sl/#req-1-inheritance-conflict) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-inheritance-conflict)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ include more than one variable, or operative function with different code, with the same name  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement): [**\[M\] Document Name Conflicts**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-inheritance-order).

[**\[S\] No Hashing Consecutive Variable Length Arguments**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-hashing-consecutive-variable-length-args) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-hashing-consecutive-variable-length-args)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use `abi.encodePacked()` with consecutive variable length arguments.

[**\[S\] No `selfdestruct()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-self-destruct) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-self-destruct)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain the `selfdestruct()` instruction or its now-deprecated alias `suicide()`  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[M\] Protect Self-destruction**](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

[**\[S\] No Unicode Direction Control Characters**](https://entethalliance.org/specs/ethtrust-sl/#req-1-unicode-bdo) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-unicode-bdo)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain any of the [Unicode Direction Control Characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters) `U+2066`, `U+2067`, `U+2068`, `U+2029`, `U+202A`, `U+202B`, `U+202C`, `U+202D`, or `U+202E`  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] No Unnecessary Unicode Controls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-unicode-bdo).

[**\[S\] Check External Calls Return**](https://entethalliance.org/specs/ethtrust-sl/#req-1-check-return) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-check-return)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls using the [Low-level Call Functions](https://entethalliance.org/specs/ethtrust-sl/#dfn-low-level-call-functions) (i.e. `call()`, `delegatecall()`, `staticcall()`, `send()`, and `transfer()`) _MUST_ check the returned value from each usage to determine whether the call failed,  
**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] Handle External Call Returns**](https://entethalliance.org/specs/ethtrust-sl/#req-2-handle-return).

[**\[S\] No Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-1-overflow-underflow) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-overflow-underflow)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use a Solidity compiler version older than 0.8.0  
**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[M\] Safe Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-2-overflow-underflow), **and**
*   [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented).

[**\[S\] Compiler Bug SOL-2023-3**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2023-3) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2023-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that includes Yul code and uses the `verbatim` instruction twice, in each case surrounded identical code, _MUST_ disable the Block Deduplicator when using a Solidity compiler version between 0.8.5 and 0.8.22 (inclusive).

[**\[S\] Compiler Bug SOL-2022-6**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-6) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-6)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that ABI-encodes a tuple (including a `struct`, `return` value, or a parameter list) that includes a dynamic component with the ABIEncoderV2, and whose last element is a `calldata` static array of base type `uint` or `bytes32`, _MUST NOT_ use a Solidity compiler version between 0.5.8 and 0.8.15 (inclusive).

[**\[S\] Compiler Bug SOL-2022-5 with `.push()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-5-push) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-5-push)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies `bytes` arrays from `calldata` or `memory` whose size is not a multiple of 32 bytes, and has an empty `.push()` instruction that writes to the resulting array, _MUST NOT_ use a Solidity compiler version older than 0.8.15.

[**\[S\] Compiler Bug SOL-2022-3**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-3) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that

*   uses `memory` and `calldata` pointers for the same function, **and**
*   changes the data location of a function during inheritance, **and**
*   performs an internal call at a location that is only aware of the original function signature from the base contract

_MUST NOT_ use a Solidity compiler version between 0.6.9 and 0.8.13 (inclusive).

[**\[S\] Compiler Bug SOL-2022-2**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-2) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-2)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) with a nested array that

*   passes it to an external function, **or**
*   passes it as input to `abi.encode()`, **or**
*   uses it in an event

_MUST NOT_ use a Solidity compiler version between 0.6.9 and 0.8.13 (inclusive).

[**\[S\] Compiler Bug SOL-2022-1**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-1) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that

*   uses Number literals for a [`bytesNN`](https://entethalliance.org/specs/ethtrust-sl/#dfn-bytesnn) type shorter than 32 bytes, **or**
*   uses String literals for any [`bytesNN`](https://entethalliance.org/specs/ethtrust-sl/#dfn-bytesnn) type,

**and** passes such literals to `abi.encodeCall()` as the first parameter, _MUST NOT_ use Solidity compiler version 0.8.11 nor 0.8.12.

[**\[S\] Compiler Bug SOL-2021-4**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-sol-2021-4) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-sol-2021-4)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses custom value types shorter than 32 bytes _MUST NOT_ use Solidity compiler version 0.8.8.

[**\[S\] Compiler Bug SOL-2021-2**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2021-2) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2021-2)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses `abi.decode()` on byte arrays as `memory` _MUST NOT_ use the ABIEncoderV2 with a Solidity compiler version between 0.4.16 and 0.8.3 (inclusive).

[**\[S\] Compiler Bug SOL-2021-1**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2021-1) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2021-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that has 2 or more occurrences of an instruction `keccak(mem,length)` where

*   the values of mem are equal, **and**
*   the values of length are unequal, **and**
*   the values of length are not multiples of 32,

_MUST NOT_ use the Optimizer with a Solidity compiler version older than 0.8.3.

[**\[S\] Compiler Bug SOL-2020-11-push**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-11-push) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-11-push)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies an empty byte array to storage, and subsequently increases the size of the array using `push()` _MUST NOT_ use a Solidity compiler version older than 0.7.4.

[**\[S\] Compiler Bug SOL-2020-10**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-10) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-10)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies an array of types shorter than 16 bytes to a longer array _MUST NOT_ use a Solidity compiler version older than 0.7.3.

[**\[S\] Compiler Bug SOL-2020-9**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-9) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-9)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that defines [Free Functions](https://entethalliance.org/specs/ethtrust-sl/#dfn-free-functions) _MUST NOT_ use Solidity compiler version 0.7.1.

[**\[S\] Compiler Bug SOL-2020-8**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-8) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-8)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that calls internal library functions with `calldata` parameters called via `using for` _MUST NOT_ use Solidity compiler version 0.6.9.

[**\[S\] Compiler Bug SOL-2020-6**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-6) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-6)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that accesses an array slice using an expression for the starting index that can evaluate to a value other than zero _MUST NOT_ use the ABIEncoderV2 with a Solidity compiler version between 0.6.0 and 0.6.7 (inclusive).

[**\[S\] Compiler Bug SOL-2020-7**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-7) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-7)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that passes a string literal containing two consecutive backslash ("\\") characters to an encoding function or an external call _MUST NOT_ use the ABIEncoderV2 with a Solidity compiler version between 0.5.14 and 0.6.7 (inclusive).

[**\[S\] Compiler Bug SOL-2020-5**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-5) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-5)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that defines a contract that does not include a constructor, but has a base contract that defines a constructor not defined as `payable` _MUST NOT_ use a Solidity compiler version between 0.4.5 and 0.6.7 (inclusive), **unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[M\] Check Constructor Payment**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-check-payable-constructor).

[**\[S\] Compiler Bug SOL-2020-4**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-4) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-4)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes assignments to tuples that

*   have nested tuples, **or**
*   include a pointer to an external function, **or**
*   reference a dynamically sized `calldata` array

_MUST NOT_ use a Solidity compiler version older than 0.6.4.

[**\[S\] Compiler Bug SOL-2020-3**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-3) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that declares arrays of size larger than 2^256-1 _MUST NOT_ use a Solidity compiler version older than 0.6.5.

[**\[S\] Compiler Bug SOL-2020-1**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-1) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that declares variables inside a `for` loop that contains a `break` or `continue` statement _MUST NOT_ use the Yul Optimizer with Solidity compiler version 0.6.0 nor a Solidity compiler version between 0.5.8 and 0.5.15 (inclusive).

[**\[S\] No Ancient Compilers**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-ancient-compilers) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-ancient-compilers)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use a Solidity compiler version older than 0.3.

[**\[M\] Pass Security Level \[S\]**](https://entethalliance.org/specs/ethtrust-sl/#req-2-pass-l1) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-pass-l1)**  
To be eligible for [EEA EthTrust certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at [Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-m), [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ meet the requirements for [§ 4.1 Security Level \[S\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-one).

[**\[M\] Explicitly Disambiguate Evaluation Order**](https://entethalliance.org/specs/ethtrust-sl/#req-2-enforce-eval-order) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-enforce-eval-order)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain statements where variable evaluation order can result in different outcomes

[**\[M\] No Failing `assert()` Statements**](https://entethalliance.org/specs/ethtrust-sl/#req-2-no-failing-asserts) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-no-failing-asserts)**  
`assert()` statements in [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ fail.

[**\[M\] Verify Exact Balance Checks**](https://entethalliance.org/specs/ethtrust-sl/#req-2-verify-exact-balance-check) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-verify-exact-balance-check)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that checks whether the balance of an account is exactly equal to (i.e. `==`) a specified amount or the value of a variable. _MUST_ protect itself against transfers affecting the balance tested.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Exact Balance Check**](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check).

[**\[M\] No Unnecessary Unicode Controls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-unicode-bdo) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-unicode-bdo)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use [Unicode direction control characters](https://entethalliance.org/specs/ethtrust-sl/#dfn-unicode-direction-control-characters) **unless** they are necessary to render text appropriately, and the resulting text does not mislead readers.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Unicode Direction Control Characters**](https://entethalliance.org/specs/ethtrust-sl/#req-1-unicode-bdo).

[**\[M\] No Homoglyph-style Attack**](https://entethalliance.org/specs/ethtrust-sl/#req-2-no-homoglyph-attack) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-no-homoglyph-attack)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use homoglyphs, Unicode control characters, combining characters, or characters from multiple Unicode blocks, if the impact is misleading.

[**\[M\] Protect External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls)**  
For [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls:

*   all addresses called by the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ correspond to the exact code of the [Set of Contracts](https://entethalliance.org/specs/ethtrust-sl/#dfn-set-of-contracts) tested, **and**
*   all contracts called _MUST_ be within the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), **and**
*   all contracts called _MUST_ be controlled by the same entity, **and**
*   the protection against [Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-re-entrancy-attacks) for the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be equivalent to what the [Checks-Effects-Interactions](https://entethalliance.org/specs/ethtrust-sl/#dfn-checks-effects-interactions) pattern offers,

**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls),
*   [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented),
*   [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), **and**
*   [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented).

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i).

[**\[M\] Avoid Read-only Re-entrancy Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-2-avoid-readonly-reentrancy) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-avoid-readonly-reentrancy)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls _MUST_ protect itself against [Read-only Re-entrancy Attacks](https://entethalliance.org/specs/ethtrust-sl/#dfn-read-only-re-entrancy-attack).

[**\[M\] Handle External Call Returns**](https://entethalliance.org/specs/ethtrust-sl/#req-2-handle-return) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-handle-return)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that makes external calls _MUST_ reasonably handle possible errors.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] Check External Calls Return**](https://entethalliance.org/specs/ethtrust-sl/#req-1-check-return).

[**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ document the need for each instance of:

*   `CREATE2`,
*   `assembly {}`,
*   `selfdestruct()` or its deprecated alias `suicide()`,
*   external calls,
*   `delegatecall()`,
*   code that can cause an overflow or underflow,
*   `block.number` or `block.timestamp`, **or**
*   Use of oracles and pseudo-randomness,

**and** _MUST_ describe how the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) protects against misuse or errors in these cases, **and** the documentation _MUST_ be available to anyone who can call the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

This is part of several [Sets of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements), one for each of

*   [**\[S\] No `CREATE2`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-create2),
*   [**\[S\] No `selfdestruct()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-self-destruct),
*   [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly),
*   [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i),
*   [**\[S\] No Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-1-overflow-underflow), and
*   [**\[S\] No `delegatecall()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-delegatecall).

[**\[M\] Ensure Proper Rounding of Computations Affecting Value**](https://entethalliance.org/specs/ethtrust-sl/#req-2-check-rounding) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-check-rounding)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ identify and protect against exploiting rounding errors:

*   The possible range of error introduced by such rounding _MUST_ be documented.
*   [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ unintentionally create or lose value through rounding.
*   [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ apply rounding in a way that does not allow round-trips "creating" value to repeat causing unexpectedly large transfers.

[**\[M\] Protect Self-destruction**](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that contains the `selfdestruct()` or `suicide()` instructions _MUST_

*   ensure that only authorised parties can call the method, **and**
*   _MUST_ protect those calls in a way that is fully compatible with the claims of the contract author,

**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[Q\] Enforce Least Privilege**](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control).

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No `selfdestruct()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-self-destruct).

[**\[M\] Avoid Common `assembly {}` Attack Vectors**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-assembly) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-assembly)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ use the `assembly {}` instruction to change a variable **unless** the code cannot:

*   create storage pointer collisions, **nor**
*   allow arbitrary values to be assigned to variables of type `function`.

This is part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

[**\[M\] Protect `CREATE2` Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-protect-create2) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-protect-create2)**  
For [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses the `CREATE2` instruction, any contract to be deployed using `CREATE2`

*   _MUST_ be within the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), **and**
*   _MUST NOT_ use any `selfdestruct()`, `delegatecall()` nor `callcode()` instructions, **and**
*   _MUST_ be fully compatible with the claims of the contract author,

**unless** it meets the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements)

*   [**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls),
*   [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented),
*   [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system), **and**
*   [**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented).

This is part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `CREATE2`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-create2).

[**\[M\] No Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-2-overflow-underflow) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-overflow-underflow)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ contain calculations that can overflow or underflow **unless**

*   there is a demonstrated need (e.g. for use in a modulo operation) and
*   there are guards around any calculations, if necessary, to ensure behavior consistent with the claims of the contract author.

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Overflow/Underflow**](https://entethalliance.org/specs/ethtrust-sl/#req-1-overflow-underflow).

[**\[M\] Document Name Conflicts**](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-inheritance-order) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-safe-inheritance-order)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ clearly document the order of inheritance for each function or variable that shares a name with another function or variable.  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No Conflicting Names**](https://entethalliance.org/specs/ethtrust-sl/#req-1-inheritance-conflict).

[**\[M\] Sources of Randomness**](https://entethalliance.org/specs/ethtrust-sl/#req-2-random-enough) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-random-enough)**  
Sources of randomness used in [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be sufficiently resistant to prediction that their purpose is met.

[**\[M\] Don't Misuse Block Data**](https://entethalliance.org/specs/ethtrust-sl/#req-2-block-data-misuse) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-block-data-misuse)**  
Block numbers and timestamps used in [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ introduce vulnerabilities to [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) or similar attacks.

[**\[M\] Proper Signature Verification**](https://entethalliance.org/specs/ethtrust-sl/#req-2-signature-verification) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-signature-verification)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ use proper signature verification to ensure authenticity of messages that were signed off-chain, e.g. by using `ecrecover()`.

[**\[M\] No Improper Usage of Signatures for Replay Attack Protection**](https://entethalliance.org/specs/ethtrust-sl/#req-2-malleable-signatures-for-replay) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-malleable-signatures-for-replay)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) using signatures to prevent replay attacks _MUST_ ensure that signatures cannot be reused:

*   In the same function to verify the same message,
*   In more than one function to verify the same message within the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code),
*   In more than one contract address to verify the same message, in which the same account(s) may be signing messages, **and**
*   In the same contract address across multiple chains.

**unless** it meets the [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) [**\[Q\] Intended Replay**](https://entethalliance.org/specs/ethtrust-sl/#req-3-intended-replay). Additionally, [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ verify that multiple signatures cannot be created for the same message, as is the case with [Malleable Signatures](https://entethalliance.org/specs/ethtrust-sl/#dfn-malleable-signatures).

[**\[M\] Solidity Compiler Bug 2023-1**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2023-1) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2023-1)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that contains a compound expression with side effects that uses `.selector` _MUST_ use the viaIR option with Solidity compiler versions between 0.6.2 and 0.8.20 inclusive.

[**\[M\] Compiler Bug SOL-2022-7**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-7) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-7)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that has storage writes followed by conditional early terminations from inline assembly functions containing `return()` or `stop()` instructions _MUST NOT_ use a Solidity compiler version between 0.8.13 and 0.8.17 inclusive.  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

[**\[M\] Compiler Bug SOL-2022-5 in `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-5-assembly)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that copies `bytes` arrays from calldata or memory whose size is not a multiple of 32 bytes, and has an `assembly {}` instruction that reads that data without explicitly matching the length that was copied, _MUST NOT_ use a Solidity compiler version older than 0.8.15.  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

[**\[M\] Compiler Bug SOL-2022-4**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-4) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-4)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that has at least two `assembly {}` instructions, such that one writes to memory e.g. by storing a value in a variable, but does not access that memory again, and code in a another `assembly {}` instruction refers to that memory, _MUST NOT_ use the yulOptimizer with Solidity compiler versions 0.8.13 or 0.8.14.  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

[**\[M\] Compiler Bug SOL-2021-3**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2021-3) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2021-3)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that reads an `immutable` signed integer of a `type` shorter than 256 bits within an `assembly {}` instruction _MUST NOT_ use a Solidity compiler version between 0.6.5 and 0.8.8 (inclusive).  
This is part of the [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] No `assembly {}`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-assembly).

[**\[M\] Compiler Bug Check Constructor Payment**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-check-payable-constructor) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-check-payable-constructor)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that allows payment to a constructor function that is

*   defined in a base contract, **and**
*   used by default in another contract without an explicit constructor, **and**
*   not explicity marked `payable`,

_MUST NOT_ use a Solidity compiler version between 0.4.5 and 0.6.7 (inclusive).  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] Compiler Bug SOL-2020-5**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-5).

[**\[Q\] Pass Security Level \[M\]**](https://entethalliance.org/specs/ethtrust-sl/#req-3-pass-l2) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-pass-l2)**  
To be eligible for [EEA EthTrust certification](https://entethalliance.org/specs/ethtrust-sl/#dfn-ethtrust-certified) at [Security Level \[Q\]](https://entethalliance.org/specs/ethtrust-sl/#dfn-security-level-q), [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ meet the requirements for [§ 4.2 Security Level \[M\]](https://entethalliance.org/specs/ethtrust-sl/#sec-levels-two).

[**\[Q\] Code Linting**](https://entethalliance.org/specs/ethtrust-sl/#req-3-linted) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-linted)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code)

*   _MUST NOT_ create unnecessary variables, **and**
*   _MUST NOT_ include code that cannot be reached in execution  
    **except** for code explicitly intended to manage unexpected errors, such as `assert()` statements, **and**
*   _MUST NOT_ contain a function that has the same name as the smart contract **unless** it is explicitly declared as a constructor using the `constructor` keyword, **and**
*   _MUST_ explicitly declare the visibility of all functions and variables.

[**\[Q\] Manage Gas Use Increases**](https://entethalliance.org/specs/ethtrust-sl/#req-3-enough-gas) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-enough-gas)**  
Sufficient Gas _MUST_ be available to work with data structures in the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that grow over time, in accordance with descriptions provided for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented).

[**\[Q\] Protect Gas Usage**](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-gas) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-gas)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ protect against malicious actors stealing or wasting gas.

[**\[Q\] Protect against Oracle Failure**](https://entethalliance.org/specs/ethtrust-sl/#req-3-check-oracles) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-check-oracles)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ protect itself against malfunctions in [Oracles](https://entethalliance.org/specs/ethtrust-sl/#dfn-oracles) it relies on.

[**\[Q\] Protect against Front-Running**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-front-running) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-front-running)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ require information in a form that can be used to enable a [Front-Running](https://entethalliance.org/specs/ethtrust-sl/#dfn-front-running) attack.

[**\[Q\] Protect against MEV Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that is susceptible to [MEV](https://entethalliance.org/specs/ethtrust-sl/#dfn-mev) attacks _MUST_ follow appropriate design patterns to mitigate this risk.

[**\[Q\] Protect Against Governance Takeovers**](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-governance) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-governance)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) which includes a governance system _MUST_ protect against one external entity taking control via exploit of the governance design.

[**\[Q\] Process All Inputs**](https://entethalliance.org/specs/ethtrust-sl/#req-3-all-valid-inputs) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-all-valid-inputs)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ validate inputs, and function correctly whether the input is as designed or malformed.

[**\[Q\] State Changes Trigger Events**](https://entethalliance.org/specs/ethtrust-sl/#req-3-event-on-state-change) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-event-on-state-change)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ emit a contract event for all transactions that cause state changes.

[**\[Q\] No Private Data**](https://entethalliance.org/specs/ethtrust-sl/#req-3-no-private-data) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-no-private-data)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST NOT_ store [Private Data](https://entethalliance.org/specs/ethtrust-sl/#dfn-private-data) on the blockchain.

[**\[Q\] Intended Replay**](https://entethalliance.org/specs/ethtrust-sl/#req-3-intended-replay) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-intended-replay)**  
If a signature within the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) can be reused, the replay instance _MUST_ be intended, documented, **and** safe for re-use.

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[M\] No Improper Usage of Signatures for Replay Attack Protection**](https://entethalliance.org/specs/ethtrust-sl/#req-2-malleable-signatures-for-replay).

[**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented)**  
A specification of the business logic that the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) functionality is intended to implement _MUST_ be available to anyone who can call the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

[**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system)**  
Documentation of the system architecture for the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be provided that conveys the overrall system design, privileged roles, security assumptions and intended usage.

[**\[Q\] Annotate Code with NatSpec**](https://entethalliance.org/specs/ethtrust-sl/#req-3-annotate) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-annotate)**  
All [Public Interfaces](https://entethalliance.org/specs/ethtrust-sl/#dfn-public-interfaces) contained in the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ be annotated with inline comments according to the \[[NatSpec](https://entethalliance.org/specs/ethtrust-sl/#bib-natspec "NatSpec Format - Solidity Documentation")\] format that explain the intent behind each function, parameter, event, and return variable, along with developer notes for safe usage.

[**\[Q\] Implement as Documented**](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-implement-as-documented)**  
The [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _MUST_ behave as described in the documentation provided for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented), **and** [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system).

[**\[Q\] Enforce Least Privilege**](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control)**  
[Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that enables privileged access _MUST_ implement appropriate access control mechanisms that provide the least privilege necessary for those interactions, based on the documentation provided for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented).  
This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[M\] Protect Self-destruction**](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct).

[**\[Q\] Use Revocable and Transferable Access Control Permissions**](https://entethalliance.org/specs/ethtrust-sl/#req-3-revocable-permisions) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-revocable-permisions)**  
If the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) makes uses of Access Control for privileged actions, it _MUST_ implement a mechanism to revoke and transfer those permissions.

[**\[Q\] No Single Admin EOA for Privileged Actions**](https://entethalliance.org/specs/ethtrust-sl/#req-3-no-single-admin-eoa) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-no-single-admin-eoa)**  
If the [Tested code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) makes uses of Access Control for privileged actions, it _MUST_ ensure that all critical administrative tasks require multiple signatures to be executed, unless there is a multisg admin that has greater privileges and can revoke permissions in case of a compromised or rogue EOA and reverse any adverse action the EOA has taken.

[**\[Q\] Verify External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-external-calls)**  
[Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that contains external calls

*   _MUST_ document the need for them, **and**
*   _MUST_ protect them in a way that is fully compatible with the claims of the contract author.

This is part of a [Set of Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-sets-of-overriding-requirements) for [**\[S\] Use Check-Effects-Interaction**](https://entethalliance.org/specs/ethtrust-sl/#req-1-use-c-e-i), and for [**\[M\] Protect External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls).

[**\[Q\] Verify `tx.origin` Usage**](https://entethalliance.org/specs/ethtrust-sl/#req-3-verify-tx.origin) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-3-verify-tx.origin)**  
For [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) that uses `tx.origin`, each instance

*   _MUST_ be consistent with the stated security and functionality objectives of the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code), **and**
*   _MUST NOT_ allow assertions about contract functionality made for [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented) or [**\[Q\] Document System Architecture**](https://entethalliance.org/specs/ethtrust-sl/#req-3-document-system) to be violated by another contract, even where that contract is called by a user authorized to interact directly with the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code).

This is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[S\] No `tx.origin`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-no-tx.origin).

[**\[GP\] Check For and Address New Security Bugs**](https://entethalliance.org/specs/ethtrust-sl/#req-R-check-new-bugs) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-check-new-bugs)**  
Check \[[solidity-bugs-json](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-bugs-json "A JSON-formatted list of some known security-relevant Solidity bugs")\] and other sources for bugs announced after 1 November 2023 and address them.

[**\[GP\] Meet as Many Requirements as Possible**](https://entethalliance.org/specs/ethtrust-sl/#req-R-meet-all-possible) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-meet-all-possible)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ meet as many requirements of this specification as possible at Security Levels above the Security Level for which it is certified.

[**\[GP\] Use Latest Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-R-use-latest-compiler) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-use-latest-compiler)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ use the latest available stable Solidity compiler version.

[**\[GP\] Write Clear, Legible Solidity Code**](https://entethalliance.org/specs/ethtrust-sl/#req-R-clean-code) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-clean-code)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ be written for easy understanding.

[**\[GP\] Follow Accepted ERC Standards**](https://entethalliance.org/specs/ethtrust-sl/#req-R-follow-erc-standards) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-follow-erc-standards)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ conform to finalized \[[ERC](https://entethalliance.org/specs/ethtrust-sl/#bib-erc "ERC Final - Ethereum Improvement Proposals")\] standards when it is reasonably capable of doing so for its use-case.

[**\[GP\] Define a Software License**](https://entethalliance.org/specs/ethtrust-sl/#req-R-define-license) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-define-license)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ define a software license

[**\[GP\] Disclose New Vulnerabilities Responsibly**](https://entethalliance.org/specs/ethtrust-sl/#req-R-notify-news) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-notify-news)**  
Security vulnerabilities that are not addressed by this specification _SHOULD_ be brought to the attention of the Working Group and others through responsible disclosure as described in [§ 1.4 Feedback and new vulnerabilities](https://entethalliance.org/specs/ethtrust-sl/#sec-notifying-new-vulnerabilities).

[**\[GP\] Use Fuzzing**](https://entethalliance.org/specs/ethtrust-sl/#req-R-fuzzing-in-testing) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-fuzzing-in-testing)**  
[Fuzzing](https://entethalliance.org/specs/ethtrust-sl/#dfn-fuzzing) _SHOULD_ be used to probe [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) for errors.

[**\[GP\] Use Formal Verification**](https://entethalliance.org/specs/ethtrust-sl/#req-R-formal-verification) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-formal-verification)**  
The [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) _SHOULD_ undergo formal verification.

[**\[GP\] Select an Appropriate Threshold for Multisig Wallets**](https://entethalliance.org/specs/ethtrust-sl/#req-R-multisig-threshold) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-multisig-threshold)**  
Multisignature requirements for privileged actions _SHOULD_ have a sufficient number of signers, and NOT require "1 of N" nor all signatures.

[**\[GP\] Use TimeLock Delays for Sensitive Operations**](https://entethalliance.org/specs/ethtrust-sl/#req-R-timelock-for-privileged-actions) **[🔗](https://entethalliance.org/specs/ethtrust-sl/#req-R-timelock-for-privileged-actions)**  
Sensitive operations that affect all or a majority of users _SHOULD_ use \[[TimeLock](https://entethalliance.org/specs/ethtrust-sl/#bib-timelock "Protect Your Users With Smart Contract Timelocks")\] delays.

### A.3 Acknowledgments[](https://entethalliance.org/specs/ethtrust-sl/#sec-acknowledgments)

The EEA acknowledges and thanks the many people who contributed to the development of this version of the specification. Please advise us of any errors or omissions.

We are grateful to the entire community who develops Ethereum, for their work and their ongoing collaboration.

In particular we would like to thank the contributors to the [previous version of this specification](https://entethalliance.org/specs/ethtrust-sl/v1/), Co-chairs Christopher Cordi and Opal Graham as well as previous co-chairs David Tarditi and Jaye Herrell the maintainers of the Solidity Compiler and those who write Solidity Security Alerts \[[solidity-alerts](https://entethalliance.org/specs/ethtrust-sl/#bib-solidity-alerts "Solidity Blog - Security Alerts")\], the community who developed and maintained the Smart Contract Weakness Classification \[[swcregistry](https://entethalliance.org/specs/ethtrust-sl/#bib-swcregistry "Smart Contract Weakness Classification Registry")\], the Machine Consultancy for publishing the TMIO Best Practices \[[tmio-bp](https://entethalliance.org/specs/ethtrust-sl/#bib-tmio-bp "Best Practices for Smart Contracts (privately made available to EEA members)")\], and judges and participants in the [Underhanded Solidity](https://underhanded.soliditylang.org/) competitions that have taken place. They have all been very important sources of information and inspiration to the broader community as well as to us in developing this specification.

Security principles have also been developed over many years by many individuals, far too numerous to individually thank for contributions that have helped us to write the present specification. We are grateful to the many people on whose work we build.

### A.4 Changes[](https://entethalliance.org/specs/ethtrust-sl/#sec-changes)

This section outlines substantive changes made to the specification since version 1:

#### A.4.1 New Requirements[](https://entethalliance.org/specs/ethtrust-sl/#new-requirements)

The following requirements have been added to the specification since the previous release:

*   [**\[S\] Encode hashes with `chainid`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-eip155-chainid),
*   [**\[S\] Compiler Bug SOL-2023-3**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2023-3),
*   [**\[S\] Compiler Bug SOL-2022-6**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2022-6),
*   [**\[S\] Use a modern Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-060),
*   [**\[M\] Explicitly Disambiguate Evaluation Order**](https://entethalliance.org/specs/ethtrust-sl/#req-2-enforce-eval-order),
*   [**\[M\] Verify Exact Balance Checks**](https://entethalliance.org/specs/ethtrust-sl/#req-2-verify-exact-balance-check) as an Overriding Requirement for [**\[S\] No Exact Balance Check**](https://entethalliance.org/specs/ethtrust-sl/#req-1-exact-balance-check),
*   [**\[M\] Avoid Read-only Re-entrancy Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-2-avoid-readonly-reentrancy)
*   [**\[M\] Ensure Proper Rounding Of Computations Affecting Value**](https://entethalliance.org/specs/ethtrust-sl/#req-2-check-rounding),
*   [**\[M\] Compiler Bug SOL-2022-7**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2022-7),
*   [**\[M\] Solidity Compiler Bug 2023-1**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-SOL-2023-1),
*   [**\[M\] Use a modern Compiler**](https://entethalliance.org/specs/ethtrust-sl/#req-2-compiler-060),
*   [**\[Q\] Protect Gas Usage**](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-gas),
*   [**\[Q\] Protect against Oracle Failure**](https://entethalliance.org/specs/ethtrust-sl/#req-3-check-oracles),
*   [**\[Q\] Protect Against Governance Takeovers**](https://entethalliance.org/specs/ethtrust-sl/#req-3-protect-governance),
*   [**\[Q\] Intended Replay**](https://entethalliance.org/specs/ethtrust-sl/#req-3-intended-replay),
*   [**\[Q\] Access control permissions must be both revocable and transferable**](https://entethalliance.org/specs/ethtrust-sl/#req-3-revocable-permisions), and
*   [**\[Q\] No single Admin EOA for privileged actions**](https://entethalliance.org/specs/ethtrust-sl/#req-3-no-single-admin-eoa).

The following [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations) have also been added

*   [**\[GP\] Use Fuzzing As Part Of Testing**](https://entethalliance.org/specs/ethtrust-sl/#req-R-fuzzing-in-testing),
*   [**\[GP\] Select an appropiate threshold for multisig wallets**](https://entethalliance.org/specs/ethtrust-sl/#req-R-multisig-threshold), and
*   [**\[GP\] Use TimeLock delays for sensitive operations**](https://entethalliance.org/specs/ethtrust-sl/#req-R-timelock-for-privileged-actions).

#### A.4.2 Updated Requirements[](https://entethalliance.org/specs/ethtrust-sl/#updated-requirements)

The following requirements have been changed in some way since the previous release:

*   update [**\[S\] Check External Calls Return**](https://entethalliance.org/specs/ethtrust-sl/#req-1-check-return) to allow [**\[M\] Handle External Call Returns**](https://entethalliance.org/specs/ethtrust-sl/#req-2-handle-return) as an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement),
*   Rename **\[S\] No Conflicting Inheritance** to [**\[S\] No Conflicting Names**](https://entethalliance.org/specs/ethtrust-sl/#req-1-inheritance-conflict),
*   update [**\[S\] No `delegatecall()`**](https://entethalliance.org/specs/ethtrust-sl/#req-1-delegatecall) to require [**\[M\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented) as an additional [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) at Level \[M\],
*   Make [**\[S\] Compiler Bug SOL-2020-4** also apply to Solidity compiler version 0.6.5,](https://entethalliance.org/specs/ethtrust-sl/#req-1-compiler-SOL-2020-4)
*   Add a requirement to document use of `delegatecall()` to [**\[Q\] Document Special Code Use**](https://entethalliance.org/specs/ethtrust-sl/#req-2-documented),
*   Explicitly require checking that contract addresses match assumptions in [**\[M\] Protect External Calls**](https://entethalliance.org/specs/ethtrust-sl/#req-2-external-calls),
*   **\[Q\] Implement Access Control** renamed to [**\[Q\] Enforce Least Privilege**](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control) clarifying that it requires providing least privilege, when the [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) enables privileged access,
*   [**\[Q\] Protect against MEV Attacks**](https://entethalliance.org/specs/ethtrust-sl/#req-3-block-mev) lists in the explanatory text a minimum set of attack types that need consideration,
*   [**\[Q\] Annotate Code with NatSpec**](https://entethalliance.org/specs/ethtrust-sl/#req-3-annotate) describes an additional use case,
*   Clarify that as part of [**\[Q\] Document Contract Logic**](https://entethalliance.org/specs/ethtrust-sl/#req-3-documented) documentation is expected to cover tokenomics, protection against MEV and flashloan attacks, and the like,
*   [**\[Q\] Code Linting**](https://entethalliance.org/specs/ethtrust-sl/#req-3-linted) includes an additional requirement to check that [Tested Code](https://entethalliance.org/specs/ethtrust-sl/#dfn-tested-code) uses explicitly labeled constructors. Formerly the requirements for this were at lower levels, but the potential security impact does not justify the lower level requirements, and
*   Explicitly state that [**\[Q\] Enforce Least Privilege**](https://entethalliance.org/specs/ethtrust-sl/#req-3-access-control) is an [Overriding Requirement](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) for [**\[M\] Protect Self-destruction**](https://entethalliance.org/specs/ethtrust-sl/#req-2-self-destruct).

The following [§ 4.4 Recommended Good Practices](https://entethalliance.org/specs/ethtrust-sl/#sec-good-practice-recommendations) have also been updated

*   [**\[GP\] Check For and Address New Security Bugs**](https://entethalliance.org/specs/ethtrust-sl/req-R-check-new-bugs) updated because this specification accounts for Solidity Compiler Bugs up to and including SOL-2023-2,
*   [**\[GP\] Follow Accepted ERC Standards**](https://entethalliance.org/specs/ethtrust-sl/req-R-follow-erc-standards) edited for clarity, and
*   [**\[GP\] Define a Software License**](https://entethalliance.org/specs/ethtrust-sl/req-R-define-license) edited for clarity and better explanation.

#### A.4.3 Requirements removed[](https://entethalliance.org/specs/ethtrust-sl/#requirements-removed)

*   The requirement to check usage of `transfer()` was removed from [\[S\] Check External Calls Return](https://entethalliance.org/specs/ethtrust-sl/#req-1-check-return) because it isn't one of the low-level functions: It reverts on failure.
*   The statements of Requirement **\[S\] Explicit Constructors**, and **\[M\] Declare Explicit Constructors**, were removed, but the checks remain, moved into [**\[Q\] Code Linting**](https://entethalliance.org/specs/ethtrust-sl/#req-3-linted).
*   Many Compiler bugs for old Solidity Compiler versions, instead using the [version 1 specification](https://entethalliance.org/specs/ethtrust-sl/v1) to provide them as [Overriding Requirements](https://entethalliance.org/specs/ethtrust-sl/#dfn-overriding-requirement) in the rare cases they are necessary and applicable:
    *   **\[S\] Explicit Storage** and its overriding requirement **\[M\] Declare `storage` Explicitly**,
    *   **\[S\] Compiler Bug SOL-2020-11-length**,
    *   **\[S\] Compiler Bug SOL-2019-10**,
    *   **\[S\] Compiler Bugs SOL-2019-3,6,7,9**,
    *   **\[S\] Compiler Bug SOL-2019-8**,
    *   **\[S\] Compiler Bug SOL-2019-5**,
    *   **\[S\] Compiler Bug SOL-2019-4**,
    *   **\[S\] Compiler Bug SOL-2019-2**,
    *   **\[S\] Compiler Bug SOL-2019-1**,
    *   **\[S\] Compiler Bug SOL-2018-4**,
    *   **\[S\] Compiler Bug SOL-2018-3**,
    *   **\[S\] Compiler Bug SOL-2018-2**,
    *   **\[S\] Compiler Bug SOL-2018-1**,
    *   **\[S\] Compiler Bug SOL-2017-5**,
    *   **\[S\] Compiler Bug SOL-2017-4**,
    *   **\[S\] Compiler Bug SOL-2017-3**,
    *   **\[S\] Compiler Bug SOL-2017-2**,
    *   **\[S\] Compiler Bug SOL-2017-1**,
    *   **\[S\] Compiler Bug SOL-2016-11**,
    *   **\[S\] Compiler Bug SOL-2016-10**,
    *   **\[S\] Compiler Bug SOL-2016-9**,
    *   **\[S\] Compiler Bug SOL-2016-8**,
    *   **\[S\] Compiler Bug SOL-2016-7**,
    *   **\[S\] Compiler Bug SOL-2016-6**,
    *   **\[S\] Compiler Bug SOL-2016-5**,
    *   **\[S\] Compiler Bug SOL-2016-4**,
    *   **\[S\] Compiler Bug SOL-2016-3**,
    *   **\[S\] Compiler Bug SOL-2016-2**,
    *   **\[M\] Compiler Bug SOL-2020-2**,
    *   **\[M\] Compiler Bug SOL-2019-2 in `assembly {}`**,
    *   **\[M\] Compiler Bug Check Identity Calls**,
    *   **\[M\] Validate `ecrecover()` input**, and
    *   **\[M\] Compiler Bug No Zero Ether Send**.

B. References[](https://entethalliance.org/specs/ethtrust-sl/#references)
-------------------------------------------------------------------------

### B.1 Normative references[](https://entethalliance.org/specs/ethtrust-sl/#normative-references)

\[c-e-i\]

[Security Considerations - Solidity Documentation. Section 'Use the Checks-Effects-Interactions Pattern'](https://docs.soliditylang.org/en/latest/security-considerations.html#use-the-checks-effects-interactions-pattern). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/latest/security-considerations.html#use-the-checks-effects-interactions-pattern](https://docs.soliditylang.org/en/latest/security-considerations.html#use-the-checks-effects-interactions-pattern)

\[CVE-2021-42574\]

[National Vulnerability Database CVE-2021-42574](https://nvd.nist.gov/vuln/detail/CVE-2021-42574). The National Institute of Standards (US Department of Commerce). URL: [https://nvd.nist.gov/vuln/detail/CVE-2021-42574](https://nvd.nist.gov/vuln/detail/CVE-2021-42574)

\[CWE\]

[Common Weakness Enumeration](https://cwe.mitre.org/index.html). MITRE. URL: [https://cwe.mitre.org/index.html](https://cwe.mitre.org/index.html)

\[CWE-1339\]

[CWE-1339: Insufficient Precision or Accuracy of a Real Number](https://cwe.mitre.org/data/definitions/1339.html). MITRE. URL: [https://cwe.mitre.org/data/definitions/1339.html](https://cwe.mitre.org/data/definitions/1339.html)

\[CWE-252\]

[CWE-252: Unchecked Return Value](https://cwe.mitre.org/data/definitions/252.html). MITRE. URL: [https://cwe.mitre.org/data/definitions/252.html](https://cwe.mitre.org/data/definitions/252.html)

\[CWE-284\]

[CWE-284: Improper Access Control](https://cwe.mitre.org/data/definitions/284.html). MITRE. URL: [https://cwe.mitre.org/data/definitions/284.html](https://cwe.mitre.org/data/definitions/284.html)

\[CWE-573\]

[CWE-573: Improper Following of Specification by Caller](https://cwe.mitre.org/data/definitions/573.html). MITRE. URL: [https://cwe.mitre.org/data/definitions/573.html](https://cwe.mitre.org/data/definitions/573.html)

\[CWE-667\]

[CWE-667: Improper Locking](https://cwe.mitre.org/data/definitions/667.html). MITRE. URL: [https://cwe.mitre.org/data/definitions/667.html](https://cwe.mitre.org/data/definitions/667.html)

\[CWE-670\]

[CWE-670: Always-Incorrect Control Flow Implementation](https://cwe.mitre.org/data/definitions/670.html). MITRE. URL: [https://cwe.mitre.org/data/definitions/670.html](https://cwe.mitre.org/data/definitions/670.html)

\[CWE-94\]

[CWE-94: Improper Control of Generation of Code ('Code Injection')](https://cwe.mitre.org/data/definitions/94.html). MITRE. URL: [https://cwe.mitre.org/data/definitions/94.html](https://cwe.mitre.org/data/definitions/94.html)

\[DevCon-rounding\]

[Tackling Rounding Errors with Precision Analysis](https://archive.devcon.org/archive/watch/6/tackling-rounding-errors-with-precision-analysis/?tab=YouTube). Raoul Schaffranek. Ethereum Foundation. URL: [https://archive.devcon.org/archive/watch/6/tackling-rounding-errors-with-precision-analysis/?tab=YouTube](https://archive.devcon.org/archive/watch/6/tackling-rounding-errors-with-precision-analysis/?tab=YouTube)

\[DevCon-siphoning\]

[The Gas Siphon Attack: How it Happened and How to Protect Yourself](https://archive.devcon.org/archive/watch/5/the-gas-siphon-attack-how-it-happened-and-how-to-protect-yourself/?tab=YouTube). Shane Fontaine. Ethereum Foundation. URL: [https://archive.devcon.org/archive/watch/5/the-gas-siphon-attack-how-it-happened-and-how-to-protect-yourself/?tab=YouTube](https://archive.devcon.org/archive/watch/5/the-gas-siphon-attack-how-it-happened-and-how-to-protect-yourself/?tab=YouTube)

\[EF-SL\]

[Specification languages for creating formal specifications](https://ethereum.org/en/developers/docs/smart-contracts/formal-verification/#specification-languages). Ethereum Foundation. URL: [https://ethereum.org/en/developers/docs/smart-contracts/formal-verification/#specification-languages](https://ethereum.org/en/developers/docs/smart-contracts/formal-verification/#specification-languages)

\[EIP\]

[EIP-1: EIP Purpose and Guidelines](https://eips.ethereum.org/EIPS/eip-1). Ethereum Foundation. URL: [https://eips.ethereum.org/EIPS/eip-1](https://eips.ethereum.org/EIPS/eip-1)

\[EIP-155\]

[Simple Replay Attack Protection](https://eips.ethereum.org/EIPS/eip-155). Vitalik Buterin. Ethereum Foundation. URL: [https://eips.ethereum.org/EIPS/eip-155](https://eips.ethereum.org/EIPS/eip-155)

\[EIP-6049\]

[Deprecate SELFDESTRUCT](https://eips.ethereum.org/EIPS/eip-6049). William Entriken. Ethereum Foundation. URL: [https://eips.ethereum.org/EIPS/eip-6049](https://eips.ethereum.org/EIPS/eip-6049)

\[ERC\]

[ERC Final - Ethereum Improvement Proposals](https://eips.ethereum.org/erc). Ethereum Foundation. URL: [https://eips.ethereum.org/erc](https://eips.ethereum.org/erc)

\[ERC137\]

[ERC-137: Ethereum Domain Name Service - Specification](https://eips.ethereum.org/EIPS/eip-137). Ethereum Foundation. URL: [https://eips.ethereum.org/EIPS/eip-137](https://eips.ethereum.org/EIPS/eip-137)

\[ERC20\]

[EIP-20: Token Standard](https://eips.ethereum.org/EIPS/eip-20). Ethereum Foundation. URL: [https://eips.ethereum.org/EIPS/eip-20](https://eips.ethereum.org/EIPS/eip-20)

\[ERC721\]

[ERC 721: Non-fungible Token Standard](https://eips.ethereum.org/EIPS/eip-721/). Ethereum Foundation. URL: [https://eips.ethereum.org/EIPS/eip-721/](https://eips.ethereum.org/EIPS/eip-721/)

\[error-handling\]

[Control Structures - Solidity Documentation. Section 'Error handling: Assert, Require, Revert and Exceptions'](https://docs.soliditylang.org/en/v0.8.14/control-structures.html#error-handling-assert-require-revert-and-exceptions). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/v0.8.14/control-structures.html#error-handling-assert-require-revert-and-exceptions](https://docs.soliditylang.org/en/v0.8.14/control-structures.html#error-handling-assert-require-revert-and-exceptions)

\[EthTrust-sl-v1\]

[EEA EthTrust Security Levels Specification. Version 1](https://entethalliance.org/specs/ethtrust-sl/v1/). Enterprise Ethereum Alliance. URL: [https://entethalliance.org/specs/ethtrust-sl/v1/](https://entethalliance.org/specs/ethtrust-sl/v1/)

\[EVM-version\]

[Using the Compiler - Solidity Documentation. (§Targets)](https://docs.soliditylang.org/en/latest/using-the-compiler.html#target-options). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/latest/using-the-compiler.html#target-options](https://docs.soliditylang.org/en/latest/using-the-compiler.html#target-options)

\[freipi\]

[You're writing require statements wrong](https://www.nascent.xyz/idea/youre-writing-require-statements-wrong). Brock Elmore. Nascent. URL: [https://www.nascent.xyz/idea/youre-writing-require-statements-wrong](https://www.nascent.xyz/idea/youre-writing-require-statements-wrong)

[Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data, and repealing Directive 95/46/EC (General Data Protection Regulation) (Text with EEA relevance)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679). The European Union. URL: [https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679)

\[hash-commit\]

[Commitment scheme - WikiPedia](https://en.wikipedia.org/wiki/Commitment_scheme). WikiMedia Foundation. URL: [https://en.wikipedia.org/wiki/Commitment\_scheme](https://en.wikipedia.org/wiki/Commitment_scheme)

\[Ivanov\]

[Targeting the Weakest Link: Social Engineering Attacks in Ethereum Smart Contracts](https://arxiv.org/pdf/2105.00132.pdf#subsection.4.2). Nikolay Ivanov; Jianzhi Lou; Ting Chen; Jin Li; Qiben Yan. URL: [https://arxiv.org/pdf/2105.00132.pdf#subsection.4.2](https://arxiv.org/pdf/2105.00132.pdf#subsection.4.2)

\[NatSpec\]

[NatSpec Format - Solidity Documentation](https://docs.soliditylang.org/en/latest/natspec-format.html). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/latest/natspec-format.html](https://docs.soliditylang.org/en/latest/natspec-format.html)

\[Ownable\]

[ERC-173: Contract Ownership Standard](https://eips.ethereum.org/EIPS/eip-173). Ethereum Foundation. URL: [https://eips.ethereum.org/EIPS/eip-173](https://eips.ethereum.org/EIPS/eip-173)

\[RBAC\]

[INCITS 359-2012: Information Technology - Role Based Access Control](http://www.techstreet.com/products/1837530). InterNational Committee for Information Technology Standards. URL: [http://www.techstreet.com/products/1837530](http://www.techstreet.com/products/1837530)

\[RFC2119\]

[Key words for use in RFCs to Indicate Requirement Levels](https://www.rfc-editor.org/rfc/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: [https://www.rfc-editor.org/rfc/rfc2119](https://www.rfc-editor.org/rfc/rfc2119)

\[RFC8174\]

[Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words](https://www.rfc-editor.org/rfc/rfc8174). B. Leiba. IETF. May 2017. Best Current Practice. URL: [https://www.rfc-editor.org/rfc/rfc8174](https://www.rfc-editor.org/rfc/rfc8174)

\[rounding-errors\]

[Formal Specification of Constant Product (x × y = k) Market Maker Model and Implementation](https://github.com/runtimeverification/verified-smart-contracts/blob/uniswap/uniswap/x-y-k.pdf). Runtime Verification. URL: [https://github.com/runtimeverification/verified-smart-contracts/blob/uniswap/uniswap/x-y-k.pdf](https://github.com/runtimeverification/verified-smart-contracts/blob/uniswap/uniswap/x-y-k.pdf)

\[SHA3-256\]

[FIPS 202 - SHA-3 Standard: Permutation-Based Hash and Extendable-Output Functions](http://dx.doi.org/10.6028/NIST.FIPS.202). The National Institute of Standards (US Department of Commerce). URL: [http://dx.doi.org/10.6028/NIST.FIPS.202](http://dx.doi.org/10.6028/NIST.FIPS.202)

\[software-license\]

[Choosing an Open Source License](https://choosealicense.com/). GitHub. URL: [https://choosealicense.com/](https://choosealicense.com/)

\[solidity-alerts\]

[Solidity Blog - Security Alerts](https://blog.soliditylang.org/category/security-alerts/). Ethereum Foundation. URL: [https://blog.soliditylang.org/category/security-alerts/](https://blog.soliditylang.org/category/security-alerts/)

\[solidity-bugs\]

[List of Known Bugs](https://github.com/ethereum/solidity/blob/develop/docs/bugs.rst). Ethereum Foundation. URL: [https://github.com/ethereum/solidity/blob/develop/docs/bugs.rst](https://github.com/ethereum/solidity/blob/develop/docs/bugs.rst)

\[solidity-bugs-json\]

[A JSON-formatted list of some known security-relevant Solidity bugs](https://github.com/ethereum/solidity/blob/develop/docs/bugs.json). Ethereum Foundation. URL: [https://github.com/ethereum/solidity/blob/develop/docs/bugs.json](https://github.com/ethereum/solidity/blob/develop/docs/bugs.json)

\[solidity-cheatsheet\]

[Solidity Documentation: Cheatsheet - Order Of Precedence Of Operators](https://docs.soliditylang.org/en/latest/cheatsheet.html#order-of-precedence-of-operators). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/latest/cheatsheet.html#order-of-precedence-of-operators](https://docs.soliditylang.org/en/latest/cheatsheet.html#order-of-precedence-of-operators)

\[solidity-events\]

[Solidity Documentation: Contracts - Events](https://docs.soliditylang.org/en/latest/contracts.html#events). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/latest/contracts.html#events](https://docs.soliditylang.org/en/latest/contracts.html#events)

\[solidity-functions\]

[Solidity Documentation: Contracts - Functions](https://docs.soliditylang.org/en/latest/contracts.html#functions). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/latest/contracts.html#functions](https://docs.soliditylang.org/en/latest/contracts.html#functions)

\[solidity-patterns\]

[Solidity Patterns](https://fravoll.github.io/solidity-patterns/). Franz Volland. URL: [https://fravoll.github.io/solidity-patterns/](https://fravoll.github.io/solidity-patterns/)

\[solidity-release-818\]

[Solidity 0.8.18 Release Announcement](https://soliditylang.org/blog/2023/02/01/solidity-0.8.18-release-announcement/). Ethereum Foundation. 2023-02-01. URL: [https://soliditylang.org/blog/2023/02/01/solidity-0.8.18-release-announcement/](https://soliditylang.org/blog/2023/02/01/solidity-0.8.18-release-announcement/)

\[solidity-security\]

[Security Considerations - Solidity Documentation.](https://docs.soliditylang.org/en/latest/security-considerations.html). Ethereum Foundation. URL: [https://docs.soliditylang.org/en/latest/security-considerations.html](https://docs.soliditylang.org/en/latest/security-considerations.html)

\[Solidity-Style-Guide\]

[Solidity Style Guide - Solidity Documentation](https://docs.soliditylang.org/en/latest/style-guide.html). URL: [https://docs.soliditylang.org/en/latest/style-guide.html](https://docs.soliditylang.org/en/latest/style-guide.html)

\[richards2022\]

[Solidity Underhanded Contest 2022. Submission 9 - Tynan Richards](https://github.com/ethereum/solidity-underhanded-contest/tree/master/2022/submissions_2022/submission9_TynanRichards). Ethereum Foundation. URL: [https://github.com/ethereum/solidity-underhanded-contest/tree/master/2022/submissions\_2022/submission9\_TynanRichards](https://github.com/ethereum/solidity-underhanded-contest/tree/master/2022/submissions_2022/submission9_TynanRichards)

\[swcregistry\]

[Smart Contract Weakness Classification Registry](https://swcregistry.io/). ConsenSys Diligence. URL: [https://swcregistry.io](https://swcregistry.io/)

\[TimeLock\]

[Protect Your Users With Smart Contract Timelocks](https://blog.openzeppelin.com/protect-your-users-with-smart-contract-timelocks/). OpenZeppelin. URL: [https://blog.openzeppelin.com/protect-your-users-with-smart-contract-timelocks/](https://blog.openzeppelin.com/protect-your-users-with-smart-contract-timelocks/)

\[tmio-bp\]

[Best Practices for Smart Contracts (privately made available to EEA members)](https://github.com/EntEthAlliance/eta-registry/blob/master/working-docs/tmio-bp.md). TMIO. URL: [https://github.com/EntEthAlliance/eta-registry/blob/master/working-docs/tmio-bp.md](https://github.com/EntEthAlliance/eta-registry/blob/master/working-docs/tmio-bp.md)

\[token-standards\]

[Ethereum Development Documentation - Token Standards](https://ethereum.org/en/developers/docs/standards/tokens/). Ethereum Foundation. URL: [https://ethereum.org/en/developers/docs/standards/tokens/](https://ethereum.org/en/developers/docs/standards/tokens/)

\[unicode-bdo\]

[How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls). W3C Internationalization. 10 March 2016. URL: [https://www.w3.org/International/questions/qa-bidi-unicode-controls](https://www.w3.org/International/questions/qa-bidi-unicode-controls)

\[unicode-blocks\]

[Blocks-14.0.0.txt](https://www.unicode.org/Public/UNIDATA/Blocks.txt). Unicode®, Inc. 22 January 2021. URL: [https://www.unicode.org/Public/UNIDATA/Blocks.txt](https://www.unicode.org/Public/UNIDATA/Blocks.txt)

### B.2 Informative references[](https://entethalliance.org/specs/ethtrust-sl/#informative-references)

\[ASVS\]

[OWASP Application Security Verification Standard](https://github.com/OWASP/ASVS). The OWASP Foundation. URL: [https://github.com/OWASP/ASVS](https://github.com/OWASP/ASVS)

\[chase\]

[Malleable Signatures: New Definitions and Delegatable Anonymous Credentials](https://smeiklej.com/files/csf14.pdf). Melissa Chase; Markulf Kohlweiss; Anna Lysyanskaya; Sarah Meiklejohn. URL: [https://smeiklej.com/files/csf14.pdf](https://smeiklej.com/files/csf14.pdf)

\[EEA-clients\]

[Enterprise Ethereum Client Specification - Editors' draft](https://entethalliance.github.io/client-spec/spec.html). Enterprise Ethereum Alliance, Inc. URL: [https://entethalliance.github.io/client-spec/spec.html](https://entethalliance.github.io/client-spec/spec.html)

\[EEA-L2\]

[Introduction to Ethereum Layer 2](https://entethalliance.org/eea-primers/entry/5696/). Enterprise Ethereum Alliance, Inc. URL: [https://entethalliance.org/eea-primers/entry/5696/](https://entethalliance.org/eea-primers/entry/5696/)

\[EF-MEV\]

[Maximal Extractable Value (MEV)](https://ethereum.org/en/developers/docs/mev/). Ethereum Foundation. URL: [https://ethereum.org/en/developers/docs/mev/](https://ethereum.org/en/developers/docs/mev/)

\[futureblock\]

[Future-block MEV in Proof of Stake](https://archive.devcon.org/archive/watch/6/future-block-mev-in-proof-of-stake/?tab=YouTube). Ethereum Foundation. URL: [https://archive.devcon.org/archive/watch/6/future-block-mev-in-proof-of-stake/?tab=YouTube](https://archive.devcon.org/archive/watch/6/future-block-mev-in-proof-of-stake/?tab=YouTube)

\[License\]

[Apache license version 2.0](http://www.apache.org/licenses/LICENSE-2.0). The Apache Software Foundation. URL: [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

\[postmerge-mev\]

[Why is Oracle Manipulation after the Merge so cheap? Multi-Block MEV](https://chainsecurity.com/oracle-manipulation-after-merge/). ChainSecurity. URL: [https://chainsecurity.com/oracle-manipulation-after-merge/](https://chainsecurity.com/oracle-manipulation-after-merge/)

\[solidity-reports\]

[Reporting a Vulnerability, in Security Policy](https://github.com/ethereum/solidity/security/policy#reporting-a-vulnerability). Ethereum Foundation. URL: [https://github.com/ethereum/solidity/security/policy#reporting-a-vulnerability](https://github.com/ethereum/solidity/security/policy#reporting-a-vulnerability)