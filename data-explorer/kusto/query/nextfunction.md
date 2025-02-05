---
title: next() - Azure Data Explorer
description: Learn how to use the next() function to return the value of the next column at an offset. 
ms.reviewer: alexans
ms.topic: reference
ms.date: 12/26/2022
---
# next()

Returns the value of a column in a row that is at some offset following the
current row in a [serialized row set](./windowsfunctions.md#serialized-row-set).

## Syntax

`next(column)`

`next(column, offset)`

`next(column, offset, default_value)`

## Arguments

* `column`: the column to get the values from.

* `offset`: the offset to go ahead in rows. When no offset is specified a default offset 1 is used.

* `default_value`: the default value to be used when there's no next rows to take the value from. When no default value is specified, null is used.

## Examples

```kusto
Table | serialize | extend nextA = next(A,1)
| extend diff = A - nextA
| where diff > 1

Table | serialize nextA = next(A,1,10)
| extend diff = A - nextA
| where diff <= 10
```
