---
title: Ether.js GrapQL Server Query

search: true
---

# Get amount of contract

> Query

```
{
  contract{
    address
    amount
  }
}
```

> Response

```json
- success
{
  "data": {
    "contract": {
      "address": "0xBB9bc244D798123fDe783fCc1C72d3Bb8C189413",
      "amount": 43.081018693858226
    }
  }
}
```

### Type

Query

# Request Transaction list

> Query

```
{
  transactions {
    status
    data {
      hash
      amount
      type
      time
    }
  }
}
```

> Response

```json
{
  "data": {
    "transactions": {
      "status": "loading",
      "data": []
    }
  }
}
```

### Type

Query

# Listen subscription to load transaction list 

> Query

```
subscription {
  getTransactions {
    status
    data {
      hash
      amount
      type
      time
    }
  }
}
```

> Response

```json
{
  "data": {
    "getTransactions": {
      "status": "loaded",
      "data": [
        {
          "hash":"0x6f9acb64d35f1fe1fbd7a86136e4939858c04b5ae3f9e1991a709d3b59efd8d5",
          "amount":10.0,
          "type":"receive",
          "time":"192830848"
        },
        {
          "hash":"0x6f9acb64d35f1fe1fbd7a86136e4939858c04b5ae3f9e1991a709d3b59efd8d5",
          "amount":10.0,
          "type":"receive",
          "time":"192830848"
        },
      ]
    }
  }
}
```

### Required details

`Request Transaction list before call this subscription`

### Type

Subscription

# Request subscription to load pending transaction.

> Query

```
mutation {
  checkNewEvent {
    status
    data {
      hash
      amount
      type
      time
    }
  }
}
```

> Response

```json
{
  "data": {
    "checkNewEvent": {
      "status": "pending",
      "data": {
        "hash":"0x6f9acb64d35f1fe1fbd7a86136e4939858c04b5ae3f9e1991a709d3b59efd8d5",
        "amount":10.0,
        "type":"receive",
        "time":"192830848"
      }
    }
  }
}
```

### Type

Mutation

# Subscription event to finish current pending transaction.

> Query

```
subscription {
  transaction {
    status
    data{
      hash
      type
      amount
      time
    }
  }
}
```

> Response

```json
{
  "data": {
    "transaction": {
      "status": "received",
      "data": {
        "hash":"0x6f9acb64d35f1fe1fbd7a86136e4939858c04b5ae3f9e1991a709d3b59efd8d5",
        "amount":10.0,
        "type":"receive",
        "time":"192830848"
      }
    }
  }
}
```

### Required details

`Must request subscription to load pending transaction before call this subscription`

### Type

Subsctiption