# Data Usage Agreement Specification

The Data Usage Agreement Specification is an open initiative to define a common data usage agreement format. It can be used on its own, or in combination with the [Data Contract Specification](datacontract.com).

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
provider:
  teamId: checkout
  dataProductId: orders
  outputPortId: orders_pii_v1_snowflake
consumer:
  teamId: marketing
  dataProductId: realtime_user_classification
tags:
- automated
custom:
  platformRole: arn:aws:iam::123456789012:role/agreement-8f237f9h
  platformRoleCreatedAt: 2024-01-01T13:00:00Z
  platformAgent: Data Mesh Manager Platform Agent v0.1
```

## Specification

We currently offer the specification in form of a JSON Schema [datausageagreement.schema.json](datausageagreement.schema.json).

### Consumer Types

The specification supports three different consumer types:

- dataproduct (give a data product access to data)
- team (give a team access to data)
- user (give a single user access to data)

#### dataproduct

```yaml
consumer:
  teamId: marketing
  dataProductId: realtime_user_classification
```

#### team

```yaml
consumer:
  teamId: marketing
```

#### user

```yaml
consumer:
  userId: mail@example.com
```

## Tooling

- [Data Mesh Manager](https://datamesh-manager.com) supports the data usage agreement specification and offers a request and approval workflow around agreements.

## Licence

[MIT Licence](LICENSE)
