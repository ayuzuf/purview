---
title: "Detailed Technical Design"
weight: 2
---

# Microsoft Purview DLP and Sensitivity Labels Detailed Technical Design

## 1. Introduction

This document provides the detailed technical design for implementing Microsoft Purview Data Loss Prevention (DLP) and Sensitivity Labels within a FTSE 100 financial services organization. It builds upon the high-level architectural design and provides specific technical configurations, implementation details, and operational procedures.

## 2. Technical Prerequisites

### 2.1 Licensing Requirements

| Component | Required License | Notes |
|-----------|-----------------|-------|
| Microsoft Purview DLP | Microsoft 365 E5/A5, Microsoft 365 E5/A5 Compliance, Microsoft 365 E5/A5 Information Protection and Governance | E3 licenses provide basic capabilities but lack advanced features |
| Sensitivity Labels | Microsoft 365 E5/A5, Microsoft 365 E5/A5 Compliance, Microsoft 365 E5/A5 Information Protection and Governance | E3 licenses provide basic labeling without encryption |
| Endpoint DLP | Microsoft 365 E5/A5, Microsoft 365 E5/A5 Compliance | Required for extending protection to Windows 10/11 devices |
| On-premises Scanner | Microsoft 365 E5/A5, Microsoft 365 E5/A5 Compliance | Required for scanning on-premises file repositories |
| Defender for Cloud Apps | Microsoft 365 E5/A5, Microsoft Defender for Cloud Apps | Required for third-party cloud app protection |

### 2.2 Infrastructure Requirements

#### 2.2.1 Microsoft 365 Tenant Configuration
- Tenant must be configured for Microsoft 365 Multi-Geo if operating in multiple regions
- Microsoft Entra ID P1/P2 for conditional access policies
- Exchange Online Protection for email DLP
- SharePoint Online and OneDrive for Business for document DLP

#### 2.2.2 Network Requirements
- Outbound connectivity to Microsoft 365 services
- Proxy server configuration for on-premises scanner
- Minimum bandwidth requirements as per Microsoft 365 network planning guidelines
- Firewall exceptions for Microsoft 365 endpoints

#### 2.2.3 Endpoint Requirements
- Windows 10 1809 or later / Windows 11 for Endpoint DLP
- Microsoft 365 Apps for Enterprise (Version 1908 or later)
- Microsoft Defender for Endpoint integration (recommended)

## 3. Sensitivity Labels Technical Design

### 3.1 Label Taxonomy

The following sensitivity label taxonomy is designed specifically for a financial services organization:

#### 3.1.1 Top-Level Labels

| Label Name | Description | Order | Parent |
|------------|-------------|-------|--------|
| Personal | Non-business information | 1 | None |
| Public | Information approved for public disclosure | 2 | None |
| General | General business information | 3 | None |
| Confidential | Sensitive business information | 4 | None |
| Highly Confidential | Highly sensitive regulated information | 5 | None |

#### 3.1.2 Sub-Labels

| Label Name | Description | Order | Parent |
|------------|-------------|-------|--------|
| Public\External | Information for external partners | 1 | Public |
| Public\Marketing | Approved marketing materials | 2 | Public |
| General\All Employees | Information for all employees | 1 | General |
| General\Internal Projects | Non-sensitive project information | 2 | General |
| Confidential\Internal Only | Sensitive internal information | 1 | Confidential |
| Confidential\Limited Sharing | Information for specific groups | 2 | Confidential |
| Confidential\Client Data | Non-regulated client information | 3 | Confidential |
| Highly Confidential\PII | Personal identifiable information | 1 | Highly Confidential |
| Highly Confidential\Financial | Financial records and data | 2 | Highly Confidential |
| Highly Confidential\Payment | Payment card and banking data | 3 | Highly Confidential |
| Highly Confidential\Strategic | Strategic business information | 4 | Highly Confidential |

### 3.2 Label Settings Configuration

#### 3.2.1 Personal Label

```json
{
  "LabelName": "Personal",
  "DisplayName": "Personal",
  "Description": "Non-business information that does not belong to the organization",
  "Tooltip": "Use for personal content not related to company business",
  "Priority": 1,
  "Settings": {
    "ContentMarkingHeaderEnabled": false,
    "ContentMarkingFooterEnabled": false,
    "WatermarkingEnabled": false,
    "EncryptionEnabled": false,
    "SiteAndGroupProtectionEnabled": false,
    "ApplyContentMarkingHeaderText": "",
    "ApplyContentMarkingFooterText": "",
    "ApplyWatermarkingText": ""
  }
}
```

#### 3.2.2 Highly Confidential\Financial Label

```json
{
  "LabelName": "Highly Confidential\\Financial",
  "DisplayName": "Highly Confidential - Financial",
  "Description": "Financial records and regulated financial data subject to FCA requirements",
  "Tooltip": "Use for financial records, trading data, and regulated financial information",
  "Priority": 5,
  "ParentLabelName": "Highly Confidential",
  "Settings": {
    "ContentMarkingHeaderEnabled": true,
    "ContentMarkingFooterEnabled": true,
    "WatermarkingEnabled": true,
    "EncryptionEnabled": true,
    "SiteAndGroupProtectionEnabled": true,
    "ApplyContentMarkingHeaderText": "HIGHLY CONFIDENTIAL - FINANCIAL",
    "ApplyContentMarkingHeaderFontSize": 12,
    "ApplyContentMarkingHeaderColor": "#FF0000",
    "ApplyContentMarkingHeaderAlignment": "Center",
    "ApplyContentMarkingFooterText": "Restricted access - Financial data - Unauthorized disclosure prohibited",
    "ApplyContentMarkingFooterFontSize": 10,
    "ApplyContentMarkingFooterColor": "#FF0000",
    "ApplyContentMarkingFooterAlignment": "Center",
    "ApplyWatermarkingText": "HIGHLY CONFIDENTIAL",
    "ApplyWatermarkingFontSize": 40,
    "ApplyWatermarkingColor": "#FF0000",
    "ApplyWatermarkingLayout": "Diagonal",
    "EncryptionProtectionType": "Template",
    "EncryptionTemplateId": "Financial-Data-Template",
    "EncryptionRightsDefinitions": [
      {
        "Role": "Financial-Team",
        "Rights": ["View", "Edit", "Print", "Extract"]
      },
      {
        "Role": "Compliance-Team",
        "Rights": ["View", "Print"]
      }
    ],
    "SiteAndGroupProtectionPrivacy": "Private",
    "SiteAndGroupProtectionAllowAccessFromUnmanagedDevices": false,
    "SiteAndGroupProtectionAllowExternalSharing": false
  }
}
```

### 3.3 Label Policies

#### 3.3.1 Global Label Policy

```json
{
  "PolicyName": "Global-Sensitivity-Label-Policy",
  "Description": "Global policy for all users in the organization",
  "Labels": [
    "Personal",
    "Public",
    "Public\\External",
    "Public\\Marketing",
    "General",
    "General\\All Employees",
    "General\\Internal Projects",
    "Confidential",
    "Confidential\\Internal Only",
    "Confidential\\Limited Sharing",
    "Confidential\\Client Data",
    "Highly Confidential",
    "Highly Confidential\\PII",
    "Highly Confidential\\Financial",
    "Highly Confidential\\Payment",
    "Highly Confidential\\Strategic"
  ],
  "Settings": {
    "ApplyLabelToExistingContent": true,
    "DefaultLabelForEmail": "General\\All Employees",
    "DefaultLabelForDocuments": "General\\All Employees",
    "RequireJustificationForRemoval": true,
    "RequireDowngradeJustification": true,
    "DisableMandatoryInOutlook": false,
    "HideLabelsInOutlook": false,
    "ApplyLabelInOutlook": true,
    "OutlookDefaultLabel": "General\\All Employees",
    "OutlookJustifyDowngrade": true,
    "OutlookDoNotForward": true,
    "OutlookRecommendedLabel": "General\\All Employees",
    "OutlookRecommendedLabelSet": true
  },
  "Scope": {
    "Users": ["All"],
    "Groups": [],
    "Sites": [],
    "ExcludedUsers": [],
    "ExcludedGroups": []
  }
}
```

#### 3.3.2 Financial Team Label Policy

```json
{
  "PolicyName": "Financial-Team-Sensitivity-Label-Policy",
  "Description": "Specialized policy for financial teams with additional controls",
  "Labels": [
    "Personal",
    "Public",
    "Public\\External",
    "Public\\Marketing",
    "General",
    "General\\All Employees",
    "General\\Internal Projects",
    "Confidential",
    "Confidential\\Internal Only",
    "Confidential\\Limited Sharing",
    "Confidential\\Client Data",
    "Highly Confidential",
    "Highly Confidential\\PII",
    "Highly Confidential\\Financial",
    "Highly Confidential\\Payment",
    "Highly Confidential\\Strategic"
  ],
  "Settings": {
    "ApplyLabelToExistingContent": true,
    "DefaultLabelForEmail": "Confidential\\Internal Only",
    "DefaultLabelForDocuments": "Confidential\\Internal Only",
    "RequireJustificationForRemoval": true,
    "RequireDowngradeJustification": true,
    "DisableMandatoryInOutlook": false,
    "HideLabelsInOutlook": false,
    "ApplyLabelInOutlook": true,
    "OutlookDefaultLabel": "Confidential\\Internal Only",
    "OutlookJustifyDowngrade": true,
    "OutlookDoNotForward": true,
    "OutlookRecommendedLabel": "Confidential\\Internal Only",
    "OutlookRecommendedLabelSet": true
  },
  "Scope": {
    "Users": [],
    "Groups": ["Financial-Team", "Treasury-Team", "Trading-Team"],
    "Sites": [],
    "ExcludedUsers": [],
    "ExcludedGroups": []
  }
}
```

### 3.4 Auto-Labeling Policies

#### 3.4.1 PII Auto-Labeling Policy

```json
{
  "PolicyName": "PII-Auto-Labeling-Policy",
  "Description": "Automatically label content containing PII",
  "Mode": "Simulate",
  "ApplyContentMarkingHeaderText": "HIGHLY CONFIDENTIAL - PII",
  "ApplyContentMarkingFooterText": "Contains personal information - Handle according to policy",
  "ApplyWatermarkingText": "CONTAINS PII",
  "EncryptionEnabled": true,
  "EncryptionRightsDefinitions": [
    {
      "Role": "Compliance-Team",
      "Rights": ["View", "Print"]
    }
  ],
  "Rules": [
    {
      "Name": "UK-PII-Detection",
      "ContentContainsSensitiveInformation": [
        {
          "SensitiveInformationType": "UK National Insurance Number",
          "MinCount": 1
        },
        {
          "SensitiveInformationType": "UK Drivers License Number",
          "MinCount": 1
        },
        {
          "SensitiveInformationType": "UK Electoral Roll Number",
          "MinCount": 1
        },
        {
          "SensitiveInformationType": "UK NINO",
          "MinCount": 1
        }
      ],
      "Actions": {
        "ApplySensitivityLabel": "Highly Confidential\\PII"
      }
    }
  ]
}
```

## 4. DLP Policy Technical Design

### 4.1 DLP Policy Framework

The DLP policy framework is structured to address specific regulatory and business requirements:

#### 4.1.1 Policy Categories

1. **Regulatory Compliance Policies**
   - GDPR Compliance
   - FCA Compliance
   - PCI-DSS Compliance

2. **Data Protection Policies**
   - PII Protection
   - Financial Data Protection
   - Client Data Protection
   - Strategic Information Protection

3. **Channel-Specific Policies**
   - Email Protection
   - Document Protection
   - Endpoint Protection
   - Teams Protection
   - Cloud App Protection

### 4.2 DLP Policy Configuration

#### 4.2.1 GDPR Compliance Policy

```json
{
  "PolicyName": "GDPR-Compliance-Policy",
  "Description": "Enforce GDPR compliance for personal data",
  "Mode": "Enable",
  "Priority": 1,
  "Locations": ["All"],
  "ExceptLocations": [],
  "Rules": [
    {
      "Name": "GDPR-High-Volume-Rule",
      "ContentContainsSensitiveInformation": [
        {
          "Groups": [
            {
              "Name": "GDPR-Sensitive-Types",
              "SensitiveTypes": [
                "EU Debit Card Number",
                "EU Passport Number",
                "EU SSN",
                "UK Electoral Roll Number",
                "UK NINO"
              ],
              "Operator": "OR",
              "MinCount": 1
            }
          ],
          "Operator": "AND",
          "MinCount": 10
        }
      ],
      "Actions": {
        "BlockAccess": true,
        "NotifyUser": true,
        "NotifyUserText": "This document contains a high volume of personal data protected under GDPR. Sharing has been blocked.",
        "NotifyAdmin": true,
        "NotifyAdminText": "High volume GDPR data detected and blocked from sharing.",
        "OverrideOption": "Override",
        "OverrideRequiresJustification": true,
        "OverrideRequiresBusinessJustification": true
      }
    },
    {
      "Name": "GDPR-Low-Volume-Rule",
      "ContentContainsSensitiveInformation": [
        {
          "Groups": [
            {
              "Name": "GDPR-Sensitive-Types",
              "SensitiveTypes": [
                "EU Debit Card Number",
                "EU Passport Number",
                "EU SSN",
                "UK Electoral Roll Number",
                "UK NINO"
              ],
              "Operator": "OR",
              "MinCount": 1
            }
          ],
          "Operator": "AND",
          "MinCount": 1,
          "MaxCount": 9
        }
      ],
      "Actions": {
        "NotifyUser": true,
        "NotifyUserText": "This document contains personal data protected under GDPR. Please ensure appropriate protection.",
        "GenerateIncidentReport": true,
        "EncryptContent": true
      }
    }
  ]
}
```

## 5. Implementation Procedures

### 5.1 Sensitivity Labels Implementation

#### 5.1.1 Label Creation Procedure

1. **Preparation**
   - Validate licensing requirements
   - Ensure administrative access to Microsoft Purview compliance portal
   - Prepare label taxonomy documentation

2. **Implementation Steps**
   - Create parent labels first, followed by sub-labels
   - Configure label settings according to specifications
   - Test label application in isolated environment
   - Create label policies with appropriate scoping
   - Deploy to pilot group before organization-wide deployment

3. **PowerShell Implementation**

```powershell
# Connect to Security & Compliance PowerShell
Connect-IPPSSession -UserPrincipalName admin@organization.com

# Create parent label
New-Label -Name "Highly Confidential" -DisplayName "Highly Confidential" -Tooltip "Highly sensitive regulated information" -AdvancedSettings @{Color="#FF0000"}

# Create sub-label
New-Label -Name "Highly Confidential/Financial" -DisplayName "Highly Confidential - Financial" -Tooltip "Financial records and regulated financial data" -ParentId "Highly Confidential" -EncryptionEnabled $true -EncryptionProtectionType "Template" -EncryptionTemplateId "Financial-Data-Template"

# Create label policy
New-LabelPolicy -Name "Global-Sensitivity-Label-Policy" -Labels "Personal","Public","General","Confidential","Highly Confidential" -ExchangeLocation All
```

### 5.2 DLP Policy Implementation

#### 5.2.1 DLP Policy Creation Procedure

1. **Preparation**
   - Inventory sensitive information types
   - Document regulatory requirements
   - Map business processes to data flows

2. **Implementation Steps**
   - Create custom sensitive information types if needed
   - Implement policies in simulation mode first
   - Review false positives and tune accordingly
   - Enable policies with user notifications before enforcement
   - Gradually increase enforcement levels

3. **PowerShell Implementation**

```powershell
# Connect to Security & Compliance PowerShell
Connect-IPPSSession -UserPrincipalName admin@organization.com

# Create DLP Policy
New-DlpCompliancePolicy -Name "GDPR-Compliance-Policy" -Mode Enforce -Comment "Enforce GDPR compliance for personal data" -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -TeamsLocation All

# Create DLP Rule
New-DlpComplianceRule -Name "GDPR-High-Volume-Rule" -Policy "GDPR-Compliance-Policy" -ContentContainsSensitiveInformation @{Name="EU Passport Number"; minCount="10"} -BlockAccess $true -NotifyUser $true -NotifyUserText "This document contains a high volume of personal data protected under GDPR. Sharing has been blocked."
```

## 6. Testing and Validation

### 6.1 Sensitivity Label Testing

#### 6.1.1 Test Cases

| Test ID | Description | Expected Result | Validation Method |
|---------|-------------|-----------------|-------------------|
| SL<response clipped><NOTE>To save on context only part of this file has been shown to you. You should retry this tool after you have searched inside the file with `grep -n` in order to find the line numbers of what you are looking for.</NOTE>