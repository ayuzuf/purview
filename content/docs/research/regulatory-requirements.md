---
title: "Regulatory Requirements"
weight: 3
---

# Financial Services Regulatory Requirements Analysis

## Overview
This document analyzes key regulatory requirements relevant to implementing Microsoft Purview DLP and Sensitivity Labels in a FTSE 100 financial services organization. Understanding these regulations is essential for designing a compliant information protection framework.

## UK GDPR and Data Protection Act 2018

### Key Requirements
1. **Lawful Basis for Processing**
   - Financial institutions must ensure they have a valid legal basis for data collection and processing
   - Options include: consent, legal obligation, legitimate interest, performance of a contract, public task
   - Consent must be freely given, specific, informed, and unambiguous

2. **Data Processing Principles**
   - Lawfulness, Fairness, and Transparency: Clear privacy notices explaining data usage
   - Purpose Limitation: Data collected only for specified, explicit, and legitimate purposes
   - Data Minimization: Only necessary data should be collected
   - Accuracy: Financial institutions must implement measures to ensure data accuracy
   - Storage Limitation: Data should not be kept longer than necessary
   - Integrity and Confidentiality: Appropriate security measures must be implemented

3. **Data Subject Rights**
   - Right to access personal data
   - Right to rectification of inaccurate data
   - Right to erasure ("right to be forgotten")
   - Right to restrict processing
   - Right to data portability
   - Right to object to processing

4. **Data Protection Impact Assessments**
   - Required for high-risk processing activities
   - Must be conducted before implementing new technologies

5. **Data Breach Notification**
   - Obligation to report breaches to the ICO within 72 hours
   - Affected individuals must be notified if breach poses high risk

## Financial Conduct Authority (FCA) Requirements

### Key Requirements
1. **Record Keeping**
   - Financial firms must record phone calls for training and monitoring purposes
   - Records must be maintained to prevent, detect, and deter market abuse

2. **Customer Data Protection**
   - Safeguarding customer data is a primary obligation
   - Data includes onboarding information, suitability checks, and personal details

3. **Risk-Based Approach**
   - FCA favors proportionate data collection and verification practices
   - Customer due diligence process must match risk level of individuals/entities

4. **Money Laundering Regulations**
   - Identifying and verifying customer identities through reliable documentation
   - Assessing purpose and nature of business relationships
   - Conducting ongoing monitoring for high-risk accounts
   - Leveraging digital tools for identity verification

## Payment Card Industry Data Security Standard (PCI DSS)

### Key Requirements
1. **Scope and Applicability**
   - Applies specifically to organizations handling payment card data
   - Created by major credit card brands (Visa, Mastercard, American Express, etc.)
   - Focuses on protecting cardholder data during payment transactions

2. **12 Core Requirements**
   - Install and maintain a firewall configuration
   - Change vendor-supplied defaults
   - Protect stored cardholder data
   - Encrypt transmission of cardholder data
   - Use and regularly update anti-virus software
   - Develop and maintain secure systems and applications
   - Restrict access to cardholder data
   - Assign unique ID to each person with computer access
   - Restrict physical access to cardholder data
   - Track and monitor all access to network resources and cardholder data
   - Regularly test security systems and processes
   - Maintain an information security policy

3. **Compliance Validation**
   - Annual assessment by qualified security assessor
   - Different validation requirements based on merchant level

4. **Descoping Strategies**
   - Reducing scope by outsourcing payment processing
   - Using third-party providers for handling card data

5. **FCA Intersection**
   - FCA regulations require call recording, while PCI DSS prohibits storing sensitive card data
   - Solutions like DTMF masking can help comply with both requirements

## Comparison and Overlaps Between Regulations

### PCI DSS vs GDPR
1. **Differences**
   - Scope: PCI DSS is specific to payment card data; GDPR covers all personal data
   - Legal basis: PCI DSS is an industry standard; GDPR is law
   - Focus: PCI DSS focuses on security; GDPR on privacy rights
   - Penalties: Different enforcement mechanisms and fine structures

2. **Overlaps**
   - Data security requirements
   - Breach notification obligations
   - Access controls and user authentication
   - Regular security assessments

## Implications for Microsoft Purview Implementation

### DLP Policy Requirements
1. **Content Detection**
   - Must identify and protect various types of regulated data:
     - Personal data under GDPR
     - Financial information under FCA rules
     - Payment card data under PCI DSS
     - Customer due diligence information under MLR

2. **Policy Actions**
   - Encryption requirements for sensitive data
   - Blocking unauthorized sharing of regulated information
   - Warning users about potential compliance violations
   - Implementing appropriate access controls

3. **Monitoring and Reporting**
   - Audit trails for regulatory compliance
   - Breach detection and notification capabilities
   - Regular compliance reporting

### Sensitivity Label Requirements
1. **Classification Taxonomy**
   - Must align with regulatory categories
   - Should distinguish between different types of regulated data
   - Need to reflect varying levels of sensitivity

2. **Protection Settings**
   - Encryption controls for different data types
   - Access restrictions based on regulatory requirements
   - Visual markings to indicate compliance status

3. **Automation Requirements**
   - Auto-labeling for regulated content
   - Integration with compliance workflows
   - Consistent application across all systems

## Implementation Considerations

1. **Cross-Regulation Compliance**
   - Design policies that satisfy multiple regulatory requirements
   - Address potential conflicts between regulations
   - Implement technical solutions for special cases (e.g., call recording with PCI compliance)

2. **Documentation and Evidence**
   - Maintain records of compliance measures
   - Document risk assessments and mitigation strategies
   - Prepare for regulatory audits and examinations

3. **User Training and Awareness**
   - Educate staff on regulatory requirements
   - Train users on proper handling of regulated information
   - Create awareness of compliance obligations

4. **Continuous Compliance**
   - Regular policy reviews and updates
   - Monitoring of regulatory changes
   - Periodic compliance assessments
