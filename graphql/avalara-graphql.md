# Avalara GraphQL Schema

## Overview

Avalara provides automated tax compliance through a suite of REST APIs. Avalara does not natively offer a GraphQL endpoint. This conceptual GraphQL schema translates the AvaTax REST API v2 surface — accounts, companies, transactions, nexus, certificates, exemptions, filings, batches, and reference data — into a unified GraphQL type system. It is intended as a design reference for teams building GraphQL gateways or federation layers over the Avalara platform.

## Source APIs

- **AvaTax REST API v2**: https://developer.avalara.com/api-reference/avatax/rest/v2/
- **CertCapture API**: https://developer.avalara.com/api-reference/CertCapture/v2/
- **Communications Tax API**: https://developer.avalara.com/api-reference/communications/v2/
- **Excise Platform API**: https://developer.avalara.com/api-reference/excise/v1/
- **VAT Reporting API**: https://developer.avalara.com/api-reference/vat-reporting/v1/
- **E-Invoicing REST API**: https://developer.avalara.com/api-reference/e-invoicing/v1.0
- **1099 & W-9 API**: https://developer.avalara.com/api-reference/avalara1099/avalara1099/

## GitHub

- https://github.com/avadev
- https://github.com/Avalara

## Schema Design Notes

### Core Domains

- **Account & Company Management** — Account, Company, Contact, User, AccountConfiguration
- **Transaction Processing** — Transaction, TransactionLine, Address, AdjustmentReason, RefundTransaction, VoidTransaction, BulkTransaction
- **Tax Calculation** — TaxCode, TaxRule, TaxCategory, TaxDetail, TaxAuthority, JurisdictionOverride
- **Nexus & Compliance** — NexusDeclaration, FilingCalendar, FilingPeriod, ReturnCalendar
- **Exemption Management** — Certificate, Exemption, ExemptionReason, CertExpressRequest, Customer
- **Batch Operations** — Batch, BatchFile, BatchStatus
- **Reference Data** — CountryInfo, RegionInfo, Postcode, UPC, DataSource, Freight
- **Reporting** — Report, ReportFilter
- **Miscellaneous** — AvaHubConfig, NoticeReason, ChangeRequest, Provisioned

### Query Conventions

- List queries accept `filter`, `top`, `skip`, and `orderBy` arguments following OData conventions used by AvaTax REST.
- Mutations mirror POST/PUT/DELETE REST endpoints.
- IDs are `String` to accommodate both integer and UUID formats across Avalara services.

## Schema File

See `avalara-schema.graphql` for the full type definitions (60+ types).
