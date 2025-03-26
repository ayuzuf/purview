---
title: "Sensitivity Label Taxonomy"
weight: 1
---

# Microsoft Purview Sensitivity Label Taxonomy and Classification Schema

## 1. Introduction

This document defines the comprehensive sensitivity label taxonomy and classification schema for a FTSE 100 financial services organization implementing Microsoft Purview. The taxonomy is designed to address specific regulatory requirements, data protection needs, and business scenarios relevant to financial institutions.

## 2. Taxonomy Design Principles

The sensitivity label taxonomy is designed based on the following principles:

1. **Regulatory Alignment**: Labels align with GDPR, FCA, PCI-DSS, and other financial services regulatory requirements
2. **Business Relevance**: Labels reflect the organization's business processes and data types
3. **Usability**: Labels are intuitive and easy for users to understand and apply
4. **Scalability**: Taxonomy can scale to accommodate future requirements
5. **Consistency**: Labels provide consistent protection across all platforms and locations

## 3. Label Hierarchy Overview

The sensitivity label hierarchy consists of five top-level labels and multiple sub-labels organized in a hierarchical structure:

```
├── Personal
├── Public
│   ├── External
│   └── Marketing
├── General
│   ├── All Employees
│   └── Internal Projects
├── Confidential
│   ├── Internal Only
│   ├── Limited Sharing
│   ├── Client Data
│   ├── Financial
│   └── HR
├── Highly Confidential
    ├── PII
    ├── Financial
    ├── Payment
    ├── Strategic
    └── Legal
```

## 4. Detailed Label Definitions

### 4.1 Personal

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Personal |
| **Display Name** | Personal |
| **Description** | Non-business information that does not belong to the organization |
| **Tooltip** | Use for personal content not related to company business |
| **Order** | 1 |
| **Visual Marking** | None |
| **Protection** | None |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | For personal, non-work-related content that is permitted under acceptable use policy |

### 4.2 Public

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Public |
| **Display Name** | Public |
| **Description** | Information approved for public disclosure |
| **Tooltip** | Use for content that has been approved for public distribution |
| **Order** | 2 |
| **Visual Marking** | Header: "PUBLIC" (Green) |
| **Protection** | None |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | For content that has been formally approved for public distribution |

#### 4.2.1 Public\External

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Public\External |
| **Display Name** | Public - External |
| **Description** | Information for external partners and clients |
| **Tooltip** | Use for content that can be shared with external partners and clients |
| **Order** | 1 |
| **Parent** | Public |
| **Visual Marking** | Header: "PUBLIC - EXTERNAL" (Green) |
| **Protection** | None |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | For content that can be shared with external parties without additional approval |

#### 4.2.2 Public\Marketing

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Public\Marketing |
| **Display Name** | Public - Marketing |
| **Description** | Approved marketing materials |
| **Tooltip** | Use for approved marketing content and materials |
| **Order** | 2 |
| **Parent** | Public |
| **Visual Marking** | Header: "PUBLIC - MARKETING" (Green) |
| **Protection** | None |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | For marketing materials that have been approved for public distribution |

### 4.3 General

| Attribute | Description |
|-----------|-------------|
| **Label Name** | General |
| **Display Name** | General |
| **Description** | General business information |
| **Tooltip** | Use for general business content not requiring special protection |
| **Order** | 3 |
| **Visual Marking** | Header: "GENERAL" (Blue) |
| **Protection** | None |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | Default label for general business content that doesn't contain sensitive information |

#### 4.3.1 General\All Employees

| Attribute | Description |
|-----------|-------------|
| **Label Name** | General\All Employees |
| **Display Name** | General - All Employees |
| **Description** | Information for all employees |
| **Tooltip** | Use for content that should be accessible to all employees |
| **Order** | 1 |
| **Parent** | General |
| **Visual Marking** | Header: "GENERAL - ALL EMPLOYEES" (Blue) |
| **Protection** | None |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | Default label for internal communications and documents intended for all employees |

#### 4.3.2 General\Internal Projects

| Attribute | Description |
|-----------|-------------|
| **Label Name** | General\Internal Projects |
| **Display Name** | General - Internal Projects |
| **Description** | Non-sensitive project information |
| **Tooltip** | Use for non-sensitive project documentation and communications |
| **Order** | 2 |
| **Parent** | General |
| **Visual Marking** | Header: "GENERAL - INTERNAL PROJECTS" (Blue) |
| **Protection** | None |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | For project documentation that doesn't contain sensitive information but should remain internal |

### 4.4 Confidential

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Confidential |
| **Display Name** | Confidential |
| **Description** | Sensitive business information |
| **Tooltip** | Use for sensitive business content requiring protection |
| **Order** | 4 |
| **Visual Marking** | Header: "CONFIDENTIAL" (Orange), Footer: "Confidential - Internal Use Only" |
| **Protection** | Prevent copying to unauthorized locations |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | No |
| **Usage Guidance** | For sensitive business information that requires protection but not the highest level of security |

#### 4.4.1 Confidential\Internal Only

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Confidential\Internal Only |
| **Display Name** | Confidential - Internal Only |
| **Description** | Sensitive internal information |
| **Tooltip** | Use for sensitive content that must remain within the organization |
| **Order** | 1 |
| **Parent** | Confidential |
| **Visual Marking** | Header: "CONFIDENTIAL - INTERNAL ONLY" (Orange), Footer: "Do not share outside the organization" |
| **Protection** | Prevent external sharing |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | No |
| **Usage Guidance** | For sensitive internal documents that should never be shared externally |

#### 4.4.2 Confidential\Limited Sharing

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Confidential\Limited Sharing |
| **Display Name** | Confidential - Limited Sharing |
| **Description** | Information for specific groups |
| **Tooltip** | Use for content with restricted distribution to specific groups |
| **Order** | 2 |
| **Parent** | Confidential |
| **Visual Marking** | Header: "CONFIDENTIAL - LIMITED SHARING" (Orange), Footer: "Limited distribution - Do not share further" |
| **Protection** | Restrict to specific groups |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | For content that should only be shared with specific groups or departments |

#### 4.4.3 Confidential\Client Data

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Confidential\Client Data |
| **Display Name** | Confidential - Client Data |
| **Description** | Non-regulated client information |
| **Tooltip** | Use for client information that is not subject to specific regulations |
| **Order** | 3 |
| **Parent** | Confidential |
| **Visual Marking** | Header: "CONFIDENTIAL - CLIENT DATA" (Orange), Footer: "Client information - Handle according to policy" |
| **Protection** | Prevent external sharing except to approved domains |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | No |
| **Usage Guidance** | For client information that requires protection but is not subject to specific regulatory requirements |

#### 4.4.4 Confidential\Financial

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Confidential\Financial |
| **Display Name** | Confidential - Financial |
| **Description** | Sensitive financial information |
| **Tooltip** | Use for sensitive financial data and reports |
| **Order** | 4 |
| **Parent** | Confidential |
| **Visual Marking** | Header: "CONFIDENTIAL - FINANCIAL" (Orange), Footer: "Financial information - Handle according to policy" |
| **Protection** | Restrict to Finance group, prevent external sharing |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | No |
| **Usage Guidance** | For financial information that requires protection but is not subject to the highest regulatory requirements |

#### 4.4.5 Confidential\HR

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Confidential\HR |
| **Display Name** | Confidential - HR |
| **Description** | Sensitive HR information |
| **Tooltip** | Use for sensitive HR data and documents |
| **Order** | 5 |
| **Parent** | Confidential |
| **Visual Marking** | Header: "CONFIDENTIAL - HR" (Orange), Footer: "HR information - Handle according to policy" |
| **Protection** | Restrict to HR group, prevent external sharing |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | No |
| **Usage Guidance** | For HR information that requires protection but does not contain highly sensitive personal data |

### 4.5 Highly Confidential

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Highly Confidential |
| **Display Name** | Highly Confidential |
| **Description** | Highly sensitive regulated information |
| **Tooltip** | Use for highly sensitive content requiring the strongest protection |
| **Order** | 5 |
| **Visual Marking** | Header: "HIGHLY CONFIDENTIAL" (Red), Footer: "Highly Confidential - Unauthorized disclosure prohibited", Watermark: "HIGHLY CONFIDENTIAL" |
| **Protection** | Encrypt content, prevent external sharing, prevent printing |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | No |
| **Usage Guidance** | For the most sensitive information requiring the highest level of protection |

#### 4.5.1 Highly Confidential\PII

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Highly Confidential\PII |
| **Display Name** | Highly Confidential - PII |
| **Description** | Personal identifiable information |
| **Tooltip** | Use for content containing personal identifiable information subject to GDPR |
| **Order** | 1 |
| **Parent** | Highly Confidential |
| **Visual Marking** | Header: "HIGHLY CONFIDENTIAL - PII" (Red), Footer: "Contains personal information - Unauthorized disclosure prohibited", Watermark: "CONTAINS PII" |
| **Protection** | Encrypt content, prevent external sharing, prevent printing, prevent copying |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | Yes - for content with PII |
| **Usage Guidance** | For content containing personal identifiable information subject to GDPR and other privacy regulations |

#### 4.5.2 Highly Confidential\Financial

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Highly Confidential\Financial |
| **Display Name** | Highly Confidential - Financial |
| **Description** | Financial records and data |
| **Tooltip** | Use for financial records, trading data, and regulated financial information |
| **Order** | 2 |
| **Parent** | Highly Confidential |
| **Visual Marking** | Header: "HIGHLY CONFIDENTIAL - FINANCIAL" (Red), Footer: "Restricted access - Financial data - Unauthorized disclosure prohibited", Watermark: "HIGHLY CONFIDENTIAL" |
| **Protection** | Encrypt content, restrict to Financial Team, prevent external sharing, prevent printing |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | Yes - for regulated financial content |
| **Usage Guidance** | For financial records and data subject to FCA and other financial regulations |

#### 4.5.3 Highly Confidential\Payment

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Highly Confidential\Payment |
| **Display Name** | Highly Confidential - Payment |
| **Description** | Payment card and banking data |
| **Tooltip** | Use for payment card data, banking information, and other payment details |
| **Order** | 3 |
| **Parent** | Highly Confidential |
| **Visual Marking** | Header: "HIGHLY CONFIDENTIAL - PAYMENT" (Red), Footer: "Payment card data - Unauthorized disclosure prohibited", Watermark: "PAYMENT DATA" |
| **Protection** | Encrypt content, restrict to Payment Team, prevent external sharing, prevent printing, prevent copying |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | Yes - for payment card data |
| **Usage Guidance** | For payment card data and banking information subject to PCI-DSS and other payment regulations |

#### 4.5.4 Highly Confidential\Strategic

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Highly Confidential\Strategic |
| **Display Name** | Highly Confidential - Strategic |
| **Description** | Strategic business information |
| **Tooltip** | Use for strategic plans, M&A information, and other highly sensitive business information |
| **Order** | 4 |
| **Parent** | Highly Confidential |
| **Visual Marking** | Header: "HIGHLY CONFIDENTIAL - STRATEGIC" (Red), Footer: "Strategic information - Unauthorized disclosure prohibited", Watermark: "STRATEGIC" |
| **Protection** | Encrypt content, restrict to Executive Team, prevent external sharing, prevent printing |
| **Auto-labeling** | No |
| **Mandatory** | No |
| **Usage Guidance** | For strategic business information such as mergers and acquisitions, business plans, and other highly sensitive strategic content |

#### 4.5.5 Highly Confidential\Legal

| Attribute | Description |
|-----------|-------------|
| **Label Name** | Highly Confidential\Legal |
| **Display Name** | Highly Confidential - Legal |
| **Description** | Legally privileged information |
| **Tooltip** | Use for legally privileged content and sensitive legal matters |
| **Order** | 5 |
| **Parent** | Highly Confidential |
| **Visual Marking** | Header: "HIGHLY CONFIDENTIAL - LEGAL" (Red), Footer: "Legally privileged - Unauthorized disclosure prohibited", Watermark: "LEGALLY PRIVILEGED" |
| **Protection** | Encrypt content, restrict to Legal Team, prevent external sharing, prevent printing |
| **Auto-labeling** | Yes - based on content |
| **Mandatory** | Yes - for legally privileged content |
| **Usage Guidance** | For legally privileged information and sensitive legal matters requiring the highest level of protection |

## 5. Label Application Guidelines

### 5.1 Default Labels

The following default labels are configured for different content types:

| Content Type | Default Label | Rationale |
|--------------|---------------|-----------|
| Email | General\All Employees | Most emails are general business communications |
| Documents | General\All Employees | Most documents are general business content |
| Teams Messages | General\All Employees | Most Teams messages are general business communications |
| SharePoint Sites | General\All Employees | Most SharePoint sites contain general business content |
| Power BI Reports | Confidential\Internal Only | Most Power BI reports contain sensitive business data |

### 5.2 Mandatory Labeling

Mandatory labeling is configured for the following scenarios:

| Scenario | Requirement | Justification |
|----------|-------------|--------------<response clipped><NOTE>To save on context only part of this file has been shown to you. You should retry this tool after you have searched inside the file with `grep -n` in order to find the line numbers of what you are looking for.</NOTE>