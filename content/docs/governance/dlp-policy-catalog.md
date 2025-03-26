---
title: "DLP Policy Catalog"
weight: 2
---

# Microsoft Purview DLP Policy Catalog

## 1. Introduction

This document provides a comprehensive catalog of Data Loss Prevention (DLP) policies designed for a FTSE 100 financial services organization. The policies are structured to address specific regulatory requirements, data protection needs, and business scenarios relevant to financial institutions.

## 2. Policy Categories

DLP policies are organized into the following categories:

1. **Regulatory Compliance Policies**: Policies specifically designed to meet regulatory requirements
2. **Data Protection Policies**: Policies focused on protecting specific types of sensitive data
3. **Business Process Policies**: Policies aligned with specific business processes and workflows
4. **Location-Specific Policies**: Policies targeting specific locations or channels
5. **User-Specific Policies**: Policies targeting specific user groups or departments

## 3. Regulatory Compliance Policies

### 3.1 GDPR Compliance Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | GDPR-Compliance-Policy |
| **Description** | Prevents unauthorized sharing of personal data to ensure GDPR compliance |
| **Priority** | High (2) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | All users |
| **Excluded Users** | GDPR-Exemption group |
| **Key Rules** | External-PII-Protection, EU-Resident-Data-Protection, Data-Subject-Rights-Support |
| **Sensitive Information Types** | UK National Insurance Number, UK Drivers License Number, EU Debit Card Number, EU Passport Number, EU National Identification Number |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Required to comply with GDPR Articles 5, 6, 25, 32, and 44-50 regarding data protection and cross-border transfers |
| **Exceptions Process** | Business justification required, approval by Data Protection Officer |
| **Review Frequency** | Quarterly |

### 3.2 PCI-DSS Compliance Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | PCI-DSS-Compliance-Policy |
| **Description** | Prevents sharing of payment card information to ensure PCI-DSS compliance |
| **Priority** | Highest (1) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices, ThirdPartyApps) |
| **Target Users** | All users |
| **Excluded Users** | PCI-DSS-Exemption group |
| **Key Rules** | Block-High-Volume-PCI, Encrypt-Low-Volume-PCI, Prevent-Unencrypted-Storage |
| **Sensitive Information Types** | Credit Card Number, Credit Card Magnetic Strip Data, Credit Card Security Code |
| **Actions** | Block, Encrypt, Notify user, Generate incident report |
| **Justification** | Required to comply with PCI-DSS Requirements 3, 4, and 9 regarding protection of cardholder data |
| **Exceptions Process** | Business justification required, approval by Security Officer and Compliance Officer |
| **Review Frequency** | Monthly |

### 3.3 FCA Compliance Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | FCA-Compliance-Policy |
| **Description** | Prevents unauthorized sharing of regulated financial information |
| **Priority** | High (3) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | All users |
| **Excluded Users** | FCA-Exemption group |
| **Key Rules** | Trading-Information-Protection, Client-Financial-Data-Protection, Market-Sensitive-Information |
| **Sensitive Information Types** | Trading Account Reference, Client Account Number, Market Analysis Data |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Required to comply with FCA Principles for Business, particularly Principles 3 and 11 |
| **Exceptions Process** | Business justification required, approval by Compliance Officer |
| **Review Frequency** | Quarterly |

### 3.4 Anti-Money Laundering (AML) Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | AML-Compliance-Policy |
| **Description** | Protects AML investigation data and suspicious activity reports |
| **Priority** | High (4) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | All users |
| **Excluded Users** | AML-Team group |
| **Key Rules** | SAR-Protection, AML-Investigation-Protection |
| **Sensitive Information Types** | Suspicious Activity Report, AML Investigation Data |
| **Actions** | Block sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Required to comply with Money Laundering Regulations 2017 and FCA requirements |
| **Exceptions Process** | Approval by Money Laundering Reporting Officer only |
| **Review Frequency** | Quarterly |

## 4. Data Protection Policies

### 4.1 Personal Identifiable Information (PII) Protection Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | PII-Protection-Policy |
| **Description** | Protects personal identifiable information across all systems |
| **Priority** | Medium (5) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | All users |
| **Excluded Users** | HR-Team, Compliance-Team |
| **Key Rules** | PII-External-Sharing, PII-Encryption, PII-Volume-Detection |
| **Sensitive Information Types** | UK National Insurance Number, UK Drivers License Number, Passport Number, Date of Birth, Address Information |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Protection of customer and employee personal data |
| **Exceptions Process** | Business justification required, approval by Data Protection Officer |
| **Review Frequency** | Quarterly |

### 4.2 Financial Data Protection Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Financial-Data-Protection-Policy |
| **Description** | Protects sensitive financial data across all systems |
| **Priority** | Medium (6) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | All users |
| **Excluded Users** | Financial-Team, Treasury-Team |
| **Key Rules** | Financial-Data-External-Sharing, Financial-Data-Encryption |
| **Sensitive Information Types** | SWIFT Code, IBAN, Account Numbers, Financial Statements, Balance Sheets |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Protection of sensitive financial information |
| **Exceptions Process** | Business justification required, approval by Financial Controller |
| **Review Frequency** | Quarterly |

### 4.3 Intellectual Property Protection Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | IP-Protection-Policy |
| **Description** | Protects intellectual property and trade secrets |
| **Priority** | Medium (7) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | All users |
| **Excluded Users** | Legal-Team, Executive-Team |
| **Key Rules** | IP-External-Sharing, IP-Classification |
| **Sensitive Information Types** | Product Development Plans, Proprietary Algorithms, Trading Strategies |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Protection of company intellectual property and competitive advantage |
| **Exceptions Process** | Business justification required, approval by Legal Department |
| **Review Frequency** | Quarterly |

## 5. Business Process Policies

### 5.1 Client Onboarding Process Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Client-Onboarding-Policy |
| **Description** | Protects sensitive information during client onboarding process |
| **Priority** | Medium (8) |
| **Scope** | Exchange, SharePoint, OneDrive, Teams |
| **Target Users** | Client Services Team, Onboarding Team |
| **Excluded Users** | None |
| **Key Rules** | Client-Data-Protection, KYC-Information-Protection |
| **Sensitive Information Types** | Client Personal Information, KYC Documentation, Due Diligence Reports |
| **Actions** | Encrypt, Notify user, Generate incident report |
| **Justification** | Protection of client information during onboarding process |
| **Exceptions Process** | Approval by Head of Client Services |
| **Review Frequency** | Semi-annually |

### 5.2 Trading Operations Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Trading-Operations-Policy |
| **Description** | Protects sensitive trading information and prevents market abuse |
| **Priority** | Medium (9) |
| **Scope** | Exchange, SharePoint, OneDrive, Teams, Devices |
| **Target Users** | Trading Team, Investment Team |
| **Excluded Users** | None |
| **Key Rules** | Trading-Information-Protection, Market-Sensitive-Information |
| **Sensitive Information Types** | Trading Positions, Investment Strategies, Market Analysis |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Prevention of market abuse and protection of trading information |
| **Exceptions Process** | Approval by Head of Trading and Compliance Officer |
| **Review Frequency** | Quarterly |

### 5.3 Financial Reporting Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Financial-Reporting-Policy |
| **Description** | Protects financial reporting information prior to public disclosure |
| **Priority** | Medium (10) |
| **Scope** | Exchange, SharePoint, OneDrive, Teams, Devices |
| **Target Users** | Finance Team, Accounting Team, Executive Team |
| **Excluded Users** | None |
| **Key Rules** | Financial-Statement-Protection, Earnings-Report-Protection |
| **Sensitive Information Types** | Financial Statements, Earnings Reports, Profit Forecasts |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Prevention of insider trading and compliance with disclosure regulations |
| **Exceptions Process** | Approval by CFO and Compliance Officer |
| **Review Frequency** | Quarterly |

## 6. Location-Specific Policies

### 6.1 Email Protection Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Email-Protection-Policy |
| **Description** | Protects sensitive information in email communications |
| **Priority** | Medium (11) |
| **Scope** | Exchange |
| **Target Users** | All users |
| **Excluded Users** | None |
| **Key Rules** | External-Email-Protection, Attachment-Protection, Large-Volume-Detection |
| **Sensitive Information Types** | All sensitive information types |
| **Actions** | Block, Encrypt, Notify user, Generate incident report |
| **Justification** | Email is a high-risk channel for data leakage |
| **Exceptions Process** | Business justification required, approval by Information Security |
| **Review Frequency** | Quarterly |

### 6.2 Endpoint Protection Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Endpoint-Protection-Policy |
| **Description** | Prevents data leakage from endpoint devices |
| **Priority** | Medium (12) |
| **Scope** | Devices (Windows 10/11) |
| **Target Users** | All users |
| **Excluded Users** | None |
| **Key Rules** | Endpoint-Copy-Protection, Removable-Media-Protection, Cloud-Upload-Protection |
| **Sensitive Information Types** | All sensitive information types |
| **Actions** | Block, Notify user, Generate incident report |
| **Justification** | Endpoints are a high-risk channel for data leakage |
| **Exceptions Process** | Business justification required, approval by Information Security |
| **Review Frequency** | Quarterly |

### 6.3 Cloud App Protection Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Cloud-App-Protection-Policy |
| **Description** | Prevents data leakage to unauthorized cloud applications |
| **Priority** | Medium (13) |
| **Scope** | ThirdPartyApps (via Microsoft Defender for Cloud Apps) |
| **Target Users** | All users |
| **Excluded Users** | None |
| **Key Rules** | Unauthorized-Cloud-Storage, Unauthorized-Collaboration-Tools |
| **Sensitive Information Types** | All sensitive information types |
| **Actions** | Block, Notify user, Generate incident report |
| **Justification** | Cloud applications are a high-risk channel for data leakage |
| **Exceptions Process** | Business justification required, approval by Information Security |
| **Review Frequency** | Quarterly |

## 7. User-Specific Policies

### 7.1 Executive Team Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Executive-Team-Policy |
| **Description** | Enhanced protection for executive communications and documents |
| **Priority** | High (14) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | Executive Team |
| **Excluded Users** | None |
| **Key Rules** | Executive-Communication-Protection, Strategic-Information-Protection |
| **Sensitive Information Types** | Strategic Plans, Board Communications, M&A Information |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Executive communications contain highly sensitive strategic information |
| **Exceptions Process** | Approval by CEO and CISO |
| **Review Frequency** | Quarterly |

### 7.2 Finance Team Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | Finance-Team-Policy |
| **Description** | Enhanced protection for finance team communications and documents |
| **Priority** | Medium (15) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | Finance Team |
| **Excluded Users** | None |
| **Key Rules** | Financial-Data-Protection, Financial-Report-Protection |
| **Sensitive Information Types** | Financial Statements, Earnings Reports, Financial Forecasts |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | Finance team handles sensitive financial information |
| **Exceptions Process** | Approval by CFO and CISO |
| **Review Frequency** | Quarterly |

### 7.3 HR Team Policy

| Policy Attribute | Description |
|------------------|-------------|
| **Policy Name** | HR-Team-Policy |
| **Description** | Enhanced protection for HR team communications and documents |
| **Priority** | Medium (16) |
| **Scope** | All locations (Exchange, SharePoint, OneDrive, Teams, Devices) |
| **Target Users** | HR Team |
| **Excluded Users** | None |
| **Key Rules** | Employee-Data-Protection, Compensation-Data-Protection |
| **Sensitive Information Types** | Employee Personal Information, Compensation Data, Performance Reviews |
| **Actions** | Block external sharing, Encrypt, Notify user, Generate incident report |
| **Justification** | HR team handles sensitive employee information |
| **Exceptions Process** | Approval by HR Director and CISO |
| **Review Frequency** | Quarterly |

## 8. Policy Implementation Guidelines

### 8.1 Policy Creation Process

1. **Requirements Gathering**: Identify regulatory requirements and business needs
2. **Policy Design**: Design policy based on requirements and best practices
3. **Testing**: Test policy in simulation mode to identify false positives
4. **Approval**: Obtain approval from relevant stakeholders
5. **Implementation**: Deploy policy in production environment
6. **Monitoring**: Monitor policy effectiveness and adjust as needed

### 8.2 Policy Deployment Phases

| Phase | Descript<response clipped><NOTE>To save on context only part of this file has been shown to you. You should retry this tool after you have searched inside the file with `grep -n` in order to find the line numbers of what you are looking for.</NOTE>