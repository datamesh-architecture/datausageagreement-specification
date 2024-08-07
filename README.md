# Data Usage Agreement Specification

The Data Usage Agreement Specification is an open initiative to define a common data usage agreement format. It can be used on its own, or in combination with the [Data Contract Specification](https://datacontract.com) and the [Data Product Specification](https://dataproduct-specification.com).

A data usage agreement is a 1:1 relation between a data provider and a data consumer. It defines the purpose, status, and lifecycle of the agreement. A [data contract](https://datacontract.com) can be part of an agreement.

A data usage agreement enables you to always know who is using what data and why. You can use agreements as input for automatically granting or revoking access in the platform, and store the current automation state in the agreement

## Version

0.0.1

## Example

```yaml
dataUsageAgreementSpecification: 0.0.1
id: agreement-8f237f9h
info:
  purpose: ML model training for real-time user classification (Project RTUSR-3)
  status: approved
  active: true
  startDate: 2024-01-01
  endDate: null
  individualAgreements: null
provider:
  teamId: checkout
  dataProductId: orders
  outputPortId: orders_pii_v1_snowflake
  dataContractId: orders_pii_v1
consumer:
  teamId: marketing
  dataProductId: realtime_user_classification
tags:
- automated
links:
  aws: https://example.com/aws-role
custom:
  platformRole: arn:aws:iam::123456789012:role/agreement-8f237f9h
  platformRoleCreatedAt: 2024-01-01T13:00:00Z
  platformAgent: Data Mesh Manager Platform Agent v0.1
```

## Specification

We currently offer the specification in form of a JSON Schema [datausageagreement.schema.json](datausageagreement.schema.json).

### Info

- Purpose: string
- Status: requested, approved, rejected
- Active: true, false
- Start Date: date
- End Date: date (optional)

### Provider

The specification supports the output port of a data product as a provider. The data contract is optional but recommended.

```yaml
provider:
  teamId: checkout
  dataProductId: orders
  outputPortId: orders_pii_v1_snowflake
  dataContractId: orders_pii_v1 # optional
```

### Consumer

The specification supports three different consumer types:

- dataproduct (give a data product access to data)
- team (give a team access to data)
- user (give a single user access to data)

#### Data Product

```yaml
consumer:
  teamId: marketing
  dataProductId: realtime_user_classification
```

#### Team

```yaml
consumer:
  teamId: marketing
```

#### User

```yaml
consumer:
  userId: mail@example.com
```

## Tooling

- [Data Mesh Manager](https://datamesh-manager.com) supports the data usage agreement specification and offers a request and approval workflow around agreements.

## Licence

[MIT Licence](LICENSE)
