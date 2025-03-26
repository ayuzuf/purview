---
title: "DLP Capabilities"
weight: 1
---

# Microsoft Purview DLP Capabilities Research

## Overview
Microsoft Purview Data Loss Prevention (DLP) provides a unified and cloud-native solution that prevents sensitive data loss with minimal impact to business continuity. It enables organizations to identify, monitor, and automatically protect sensitive items across Microsoft 365 services, endpoints, and on-premises environments.

## Core Capabilities

### 1. Comprehensive Protection
- Discover and help secure sensitive data wherever it lives, is used, or travels
- Protection across Microsoft 365 services (Teams, Exchange, SharePoint, OneDrive)
- Protection for Office applications (Word, Excel, PowerPoint)
- Endpoint protection for Windows 10, Windows 11, and macOS devices
- Protection for non-Microsoft cloud apps
- Protection for on-premises file shares and SharePoint
- Protection for Fabric and Power BI workspaces
- Protection for Microsoft 365 Copilot interactions

### 2. Cloud-Managed and Delivered
- Centralize end-to-end DLP program in one cloud-native solution
- Easy to deploy, use, and scale
- Single location for policy management through Microsoft Purview compliance portal
- Create, manage, and enforce data loss prevention policies from a central location

### 3. Adaptive Controls
- Balance security and user productivity with machine learning-driven analysis
- Classification and policy controls that adapt to organizational needs
- Deep content analysis beyond simple text scanning:
  - Primary data matches to keywords
  - Evaluation of regular expressions
  - Internal function validation
  - Secondary data matches in proximity to primary data
  - Machine learning algorithms for content detection

### 4. Protective Actions
- Show policy tips to warn users about potentially inappropriate sharing
- Block sharing with override option and justification capture
- Block sharing without override option
- Lock and move sensitive items to secure quarantine location
- Hide sensitive information in Teams chat
- Record all DLP monitored activities to Microsoft 365 Audit log
- Route activities to Activity explorer

## Recent Enhancements

### 1. Efficient Investigation
- Context-rich email alerts with robust metadata
- Custom email templates for policy actions
- Rich filters for DLP alerts in Microsoft Defender XDR
- Filter by external user risk
- Insider risk summaries integration
- Simulation mode for policy testing
- DLP analytics with machine learning recommendations
- Adaptive Protection integration based on insider risk levels

### 2. Strengthened Protection
- Automatic pause and resume of user actions
- Improvements to device onboarding
- Application allowlists
- Minimized business disruption while maintaining security

### 3. Extended Protection
- Support for file type and file extension-based policy conditions
- Allowed domain groups for macOS
- Protection across multiple workloads

## Implementation Lifecycle

### 1. Plan for DLP
- Technology planning: Consider different locations, data types, and actions
- Business processes planning: Identify processes touching sensitive items
- Organizational culture planning: Train users on data loss prevention practices

### 2. Prepare for DLP
- Identify locations for DLP policy application
- Deploy Microsoft Purview Information Protection scanner for on-premises repositories
- Prepare environment and code draft policies
- Test policies thoroughly before activation

### 3. Deploy Policies in Production
- Start with simulation mode to evaluate impact
- Use policy tips to raise awareness
- Gradually move to more restrictive modes
- Monitor and tune policies based on feedback and alerts

## Licensing and Subscriptions
- DLP is part of the larger Microsoft Purview offering
- Specific licensing requirements based on Microsoft 365 guidance for security & compliance
- E5 licenses provide full capabilities, with some features available in other license tiers

## Integration with Other Microsoft Purview Tools
- Integration with Microsoft Purview Information Protection
- Unified alerting and remediation
- Connection to Microsoft Defender XDR for security operations
- Integration with Microsoft Purview Insider Risk Management