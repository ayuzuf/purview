---
title: "DLP Policy Rules Matrix"
weight: 3
---

# Microsoft Purview DLP Policy Rules Matrix

## 1. Introduction

This document provides a comprehensive matrix of Data Loss Prevention (DLP) policy rules designed for a FTSE 100 financial services organization. The matrix maps specific rules to policy categories, sensitive information types, conditions, actions, and regulatory requirements.

## 2. Rule Structure

Each DLP rule consists of the following components:

1. **Rule Name**: Unique identifier for the rule
2. **Parent Policy**: The policy to which the rule belongs
3. **Description**: Brief description of the rule's purpose
4. **Conditions**: Criteria that trigger the rule
5. **Actions**: Actions taken when the rule is triggered
6. **Exceptions**: Conditions under which the rule is not applied
7. **Regulatory Alignment**: Specific regulatory requirements addressed by the rule

## 3. Regulatory Compliance Rules

### 3.1 GDPR Compliance Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| External-PII-Protection | GDPR-Compliance-Policy | Prevents sharing PII with external recipients | Content contains PII (UK NIN, Drivers License, etc.) AND Recipient is external | Block, Notify user, Generate incident report | Approved external domains, Encrypted content | GDPR Art. 5, 25, 32, 44-50 |
| EU-Resident-Data-Protection | GDPR-Compliance-Policy | Protects EU resident data | Content contains EU resident data AND Recipient is external to EU | Block, Notify user, Generate incident report | EU adequacy decision countries, SCCs in place | GDPR Art. 44-50 |
| Data-Subject-Rights-Support | GDPR-Compliance-Policy | Identifies content for data subject requests | Content contains specific individual's PII | Apply label, Log location | None | GDPR Art. 15-22 |
| Data-Minimization-Enforcement | GDPR-Compliance-Policy | Enforces data minimization principle | Content contains excessive PII | Notify user, Generate incident report | Approved business processes | GDPR Art. 5(1)(c) |
| Breach-Notification-Support | GDPR-Compliance-Policy | Supports breach notification requirements | High volume of PII accessed/shared | Generate high-priority incident report | None | GDPR Art. 33-34 |

### 3.2 PCI-DSS Compliance Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| Block-High-Volume-PCI | PCI-DSS-Compliance-Policy | Blocks content with high volume of payment card data | Content contains ≥10 credit card numbers | Block, Notify user, Generate incident report | None | PCI-DSS Req. 3.4, 4.1, 4.2 |
| Encrypt-Low-Volume-PCI | PCI-DSS-Compliance-Policy | Encrypts content with low volume of payment card data | Content contains 1-9 credit card numbers | Encrypt, Notify user, Generate incident report | Already encrypted content | PCI-DSS Req. 3.4, 4.1, 4.2 |
| Prevent-Unencrypted-Storage | PCI-DSS-Compliance-Policy | Prevents unencrypted storage of PCI data | Content contains credit card data AND Location is storage | Block, Notify user, Generate incident report | Encrypted storage | PCI-DSS Req. 3.4 |
| Block-CVV-Storage | PCI-DSS-Compliance-Policy | Prevents storage of CVV data | Content contains CVV/CVC codes | Block, Notify user, Generate incident report | None | PCI-DSS Req. 3.2 |
| Restrict-PCI-Access | PCI-DSS-Compliance-Policy | Restricts access to PCI data | Content contains credit card data AND User not in PCI-Authorized group | Block access, Notify user, Generate incident report | None | PCI-DSS Req. 7.1, 7.2 |

### 3.3 FCA Compliance Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| Trading-Information-Protection | FCA-Compliance-Policy | Protects trading information | Content contains trading account references OR trading terms | Block external sharing, Encrypt, Notify user | Approved regulatory recipients | FCA Principles 3, 11 |
| Client-Financial-Data-Protection | FCA-Compliance-Policy | Protects client financial data | Content contains client financial data | Block external sharing, Encrypt, Notify user | Approved client communication | FCA COBS 4, 9 |
| Market-Sensitive-Information | FCA-Compliance-Policy | Protects market-sensitive information | Content contains market analysis, trading strategies | Block external sharing, Encrypt, Notify user | Approved regulatory reporting | FCA MAR, SYSC |
| Financial-Promotion-Control | FCA-Compliance-Policy | Controls financial promotions | Content contains promotional language AND financial products | Notify compliance, Generate incident report | Approved marketing materials | FCA COBS 4 |
| Record-Keeping-Enforcement | FCA-Compliance-Policy | Enforces record-keeping requirements | Attempts to delete/modify regulated communications | Block, Notify user, Generate incident report | Outside retention period | FCA SYSC 9 |

### 3.4 AML Compliance Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| SAR-Protection | AML-Compliance-Policy | Protects Suspicious Activity Reports | Content contains SAR terms/templates | Block sharing, Encrypt, Notify user | AML team members | MLR 2017, POCA 2002 |
| AML-Investigation-Protection | AML-Compliance-Policy | Protects AML investigation data | Content contains AML investigation terms | Block sharing, Encrypt, Notify user | AML team members | MLR 2017, POCA 2002 |
| Tipping-Off-Prevention | AML-Compliance-Policy | Prevents tipping off | Content contains SAR terms AND Recipient is subject | Block, Notify MLRO, Generate incident report | None | POCA 2002 s.333A |
| High-Risk-Transaction-Monitoring | AML-Compliance-Policy | Monitors high-risk transaction documentation | Content contains high-risk transaction indicators | Notify AML team, Generate incident report | None | MLR 2017 Reg. 28 |
| KYC-Documentation-Protection | AML-Compliance-Policy | Protects KYC documentation | Content contains KYC documentation | Encrypt, Restrict access, Notify user | Onboarding team | MLR 2017 Reg. 28 |

## 4. Data Protection Rules

### 4.1 PII Protection Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| PII-External-Sharing | PII-Protection-Policy | Controls external sharing of PII | Content contains PII AND Recipient is external | Block/Encrypt, Notify user, Generate incident report | Approved external sharing | GDPR, DPA 2018 |
| PII-Encryption | PII-Protection-Policy | Enforces encryption of PII | Content contains PII | Apply encryption, Apply label | HR team, Compliance team | GDPR Art. 32 |
| PII-Volume-Detection | PII-Protection-Policy | Detects high volumes of PII | Content contains ≥10 instances of PII | Notify user, Generate incident report | HR approved processes | GDPR Art. 5, 32 |
| PII-Unauthorized-Access | PII-Protection-Policy | Prevents unauthorized access to PII | Content contains PII AND User not authorized | Block access, Notify user, Generate incident report | None | GDPR Art. 5, 32 |
| PII-Retention-Enforcement | PII-Protection-Policy | Enforces PII retention policies | Content contains PII AND Age > retention period | Notify user, Generate incident report | Legal hold data | GDPR Art. 5(1)(e) |

### 4.2 Financial Data Protection Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| Financial-Data-External-Sharing | Financial-Data-Protection-Policy | Controls external sharing of financial data | Content contains financial data AND Recipient is external | Block/Encrypt, Notify user, Generate incident report | Approved external sharing | FCA Principles |
| Financial-Data-Encryption | Financial-Data-Protection-Policy | Enforces encryption of financial data | Content contains financial data | Apply encryption, Apply label | Financial team | FCA Principles |
| Financial-Statement-Protection | Financial-Data-Protection-Policy | Protects financial statements | Content contains financial statement terms | Block external sharing, Encrypt, Notify user | Approved external sharing | FCA Principles, Companies Act |
| Treasury-Data-Protection | Financial-Data-Protection-Policy | Protects treasury data | Content contains treasury data | Block external sharing, Encrypt, Notify user | Treasury team | FCA Principles |
| Investment-Data-Protection | Financial-Data-Protection-Policy | Protects investment data | Content contains investment data | Block external sharing, Encrypt, Notify user | Investment team | FCA Principles |

### 4.3 Intellectual Property Protection Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| IP-External-Sharing | IP-Protection-Policy | Controls external sharing of IP | Content contains IP markers AND Recipient is external | Block, Notify user, Generate incident report | Approved external sharing | Trade Secrets Regulations |
| IP-Classification | IP-Protection-Policy | Enforces classification of IP | Content contains IP indicators | Apply label, Notify user | Legal team | Internal policy |
| Algorithm-Protection | IP-Protection-Policy | Protects proprietary algorithms | Content contains algorithm code/documentation | Block external sharing, Encrypt, Notify user | R&D team | Trade Secrets Regulations |
| Product-Development-Protection | IP-Protection-Policy | Protects product development information | Content contains product development terms | Block external sharing, Encrypt, Notify user | Product team | Trade Secrets Regulations |
| Trading-Strategy-Protection | IP-Protection-Policy | Protects trading strategies | Content contains trading strategy terms | Block external sharing, Encrypt, Notify user | Trading team | Trade Secrets Regulations |

## 5. Business Process Rules

### 5.1 Client Onboarding Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| Client-Data-Protection | Client-Onboarding-Policy | Protects client onboarding data | Content contains client personal data | Encrypt, Notify user | Onboarding team | GDPR, FCA COBS |
| KYC-Information-Protection | Client-Onboarding-Policy | Protects KYC information | Content contains KYC documentation | Encrypt, Restrict access | Onboarding team, Compliance | MLR 2017 |
| Due-Diligence-Protection | Client-Onboarding-Policy | Protects due diligence reports | Content contains due diligence terms | Encrypt, Restrict access | Onboarding team, Compliance | MLR 2017 |
| Client-Agreement-Protection | Client-Onboarding-Policy | Protects client agreements | Content contains agreement terms | Encrypt, Apply label | Client services team | FCA COBS |
| Prospect-Information-Protection | Client-Onboarding-Policy | Protects prospect information | Content contains prospect data | Encrypt, Apply label | Sales team | GDPR, FCA COBS |

### 5.2 Trading Operations Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| Trading-Position-Protection | Trading-Operations-Policy | Protects trading position information | Content contains trading position data | Block external sharing, Encrypt | Trading team | FCA MAR |
| Investment-Strategy-Protection | Trading-Operations-Policy | Protects investment strategies | Content contains investment strategy terms | Block external sharing, Encrypt | Investment team | FCA MAR |
| Market-Analysis-Protection | Trading-Operations-Policy | Protects market analysis | Content contains market analysis terms | Block external sharing, Encrypt | Research team | FCA MAR |
| Trade-Confirmation-Protection | Trading-Operations-Policy | Protects trade confirmations | Content contains trade confirmation terms | Encrypt, Apply label | Trading operations | FCA COBS |
| Trading-Limit-Protection | Trading-Operations-Policy | Protects trading limit information | Content contains trading limit terms | Block external sharing, Encrypt | Risk management team | FCA SYSC |

### 5.3 Financial Reporting Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| Financial-Statement-Protection | Financial-Reporting-Policy | Protects financial statements | Content contains financial statement terms | Block external sharing, Encrypt | Finance team | FCA, Companies Act |
| Earnings-Report-Protection | Financial-Reporting-Policy | Protects earnings reports | Content contains earnings report terms | Block external sharing, Encrypt | Finance team | FCA, Companies Act |
| Profit-Forecast-Protection | Financial-Reporting-Policy | Protects profit forecasts | Content contains profit forecast terms | Block external sharing, Encrypt | Finance team, Executive team | FCA, Companies Act |
| Audit-Report-Protection | Financial-Reporting-Policy | Protects audit reports | Content contains audit report terms | Block external sharing, Encrypt | Finance team, Audit committee | FCA, Companies Act |
| Regulatory-Filing-Protection | Financial-Reporting-Policy | Protects regulatory filings | Content contains regulatory filing terms | Block external sharing, Encrypt | Finance team, Compliance team | FCA, Companies Act |

## 6. Location-Specific Rules

### 6.1 Email Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|----------------------|
| External-Email-Protection | Email-Protection-Policy | Protects sensitive information in external emails | Content contains sensitive information AND Recipient is external | Block/Encrypt, Notify user | Approved external recipients | Multiple regulations |
| Attachment-Protection | Email-Protection-Policy | Protects sensitive attachments | Attachment contains sensitive information | Encrypt attachment, Notify user | Already encrypted attachments | Multiple regulations |
| Large-Volume-Detection | Email-Protection-Policy | Detects large volumes of sensitive information | Email contains ≥10 instances of sensitive information | Block, Notify user, Generate incident report | Approved bulk transfers | Multiple regulations |
| Distribution-List-Protection | Email-Protection-Policy | Prevents sensitive information sent to large distribution lists | Content contains sensitive information AND Recipient count ≥10 | Notify user, Generate incident report | Approved distribution lists | Multiple regulations |
| Auto-Forward-Prevention | Email-Protection-Policy | Prevents auto-forwarding of sensitive information | Auto-forward rule AND Content contains sensitive information | Block rule, Notify user | Approved auto-forward rules | Multiple regulations |

### 6.2 Endpoint Rules

| Rule Name | Parent Policy | Description | Conditions | Actions | Exceptions | Regulatory Alignment |
|-----------|---------------|-------------|------------|---------|------------|---------------<response clipped><NOTE>To save on context only part of this file has been shown to you. You should retry this tool after you have searched inside the file with `grep -n` in order to find the line numbers of what you are looking for.</NOTE>