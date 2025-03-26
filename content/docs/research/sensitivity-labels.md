---
title: "Sensitivity Labels"
weight: 2
---

# Microsoft Purview Sensitivity Labels Research

## Overview
Microsoft Purview Sensitivity Labels are a key component of Microsoft's Information Protection solution that allow organizations to classify and protect their data while ensuring user productivity and collaboration capabilities remain unhindered. Sensitivity labels provide a unified approach to data protection across Microsoft 365 services, endpoints, and beyond.

## Core Characteristics

### 1. Customizable
- Specific to organization and business needs
- Create categories for different levels of sensitive content (e.g., Personal, Public, General, Confidential, Highly Confidential)
- Tailored to match organizational classification taxonomy

### 2. Clear Text
- Labels are stored in clear text in metadata for files and emails
- Third-party apps and services can read the labels and apply their own protective actions
- Enables interoperability with broader security ecosystem

### 3. Persistent
- Labels stay with the content, no matter where it's saved or stored
- Stored in metadata for files and emails
- Organization-unique label identification becomes the basis for applying and enforcing policies

## Key Capabilities

### 1. Protection Settings
- Apply encryption and content markings (headers, footers, watermarks)
- Restrict what actions specified people can take on content
- Example: Apply "Confidential" label to encrypt content and apply a "Confidential" watermark

### 2. SharePoint Protection Extension
- Configure default sensitivity labels for SharePoint document libraries
- Extend protection for unencrypted files when downloaded
- Maintain SharePoint permissions with labeled files

### 3. Cross-Platform Protection
- Protect content in Office apps across different platforms and devices
- Support for Word, Excel, PowerPoint, and Outlook
- Compatible with Windows, macOS, iOS, and Android

### 4. Third-Party App Protection
- Integrate with Microsoft Defender for Cloud Apps
- Detect, classify, label, and protect content in third-party apps and services
- Support for services like SalesForce, Box, or DropBox
- Third-party apps can read sensitivity labels using Microsoft Information Protection SDK

### 5. eDiscovery Support
- Identify content for eDiscovery cases
- Build search queries based on sensitivity labels
- Include or exclude content based on applied labels

### 6. Container Protection
- Protect Teams, Microsoft 365 Groups, SharePoint sites, and Loop workspaces
- Set privacy settings and external user access
- Control external sharing and access from unmanaged devices
- Manage how channels can be shared with other teams

### 7. Meeting and Chat Protection
- Label and optionally encrypt meeting invites and responses
- Enforce Teams-specific options for meetings and chat
- Protect sensitive communications

### 8. Power BI Integration
- Apply and view labels in Power BI
- Protect data when saved outside the service

### 9. Microsoft Purview Data Map Integration
- Apply sensitivity labels to files and schematized data assets
- Support for SQL, Azure SQL, Azure Synapse, Azure Cosmos DB, and AWS RDS

### 10. Microsoft 365 Copilot Integration
- Copilot recognizes and integrates sensitivity labels into user interactions
- Helps keep labeled data protected during AI interactions

## Implementation Considerations

### 1. Label Creation and Configuration
- Create labels through Microsoft Purview portal or Microsoft Purview compliance portal
- Configure scope (Files & emails, Groups & sites, Meetings)
- Define protection settings, content marking, and encryption options
- Arrange labels in priority order (higher position = higher priority)
- Support for sublabels to create a hierarchical structure

### 2. Label Policies
- Create label policies to make labels available to users
- Publish labels to specific users or groups
- Configure policy settings like default labels and mandatory labeling
- Control whether users can change or remove labels

### 3. Multilingual Support
- Configure labels for different languages using PowerShell
- Specify translations for label names and tooltips
- Support for Office language identifiers

### 4. Advanced Settings
- Additional configuration options available through Security & Compliance PowerShell
- Special settings for specific scenarios or requirements
- Support for custom configurations

### 5. Automatic Labeling
- Configure auto-labeling policies to automatically apply labels
- Base labeling on sensitive information types or trainable classifiers
- Apply labels to content in SharePoint, OneDrive, and Exchange

### 6. Monitoring and Reporting
- View label usage and activity through Microsoft Purview portal
- Generate reports on label application and protection actions
- Monitor compliance with labeling policies

## Deployment Best Practices

### 1. Planning
- Identify sensitive information types in the organization
- Define classification taxonomy aligned with business needs
- Determine protection requirements for each classification level
- Consider regulatory and compliance requirements

### 2. Phased Implementation
- Start with a pilot group to test label functionality
- Deploy labels in simulation mode before enforcing protection
- Gradually expand to more users and content
- Monitor impact and adjust as needed

### 3. User Education
- Provide training on label usage and importance
- Use policy tips to guide users on appropriate labeling
- Create awareness materials and documentation
- Ensure users understand the implications of different labels

### 4. Integration with Broader Security Strategy
- Align with DLP policies and other security controls
- Integrate with information governance strategy
- Consider how labels interact with retention policies
- Coordinate with eDiscovery and compliance teams

### 5. Maintenance and Evolution
- Regularly review and update labels as needs change
- Monitor label usage and effectiveness
- Adjust protection settings based on feedback and incidents
- Stay current with new features and capabilities
