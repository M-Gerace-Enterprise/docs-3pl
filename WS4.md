#WS4: Inventory Reconciliation

GWSI sends daily inventory reconciliation reports to the customer.

## Parameters

| Parameter | Type | Notes |
|----------|--------|----|
| InfoInventory | Input | Table with the inventory information |
| Warehouse company | Input | Fixed value `GWSI` |
| Warehouse-ID (Plant-Sto.Loc) | Input | |
| Differences | Output | Table with the identified differences |
| Error/Success message table | Output | |

Input `InfoInventory` is a object with the following keys:

| Parameter | Type | Notes |
|----------|--------|----|
| Material | Input | |
| UnitID | Input | For _pulp_, this field should hold the `Batch N` |
| Inventory | Input | |
| UnitOfMeasure | Input | |
| NumberOfPieces | Input | |
| ReasonOfDifference | Input | |

Output `Differences` is a object with the following keys:

| Parameter | Type | Notes |
|----------|--------|----|
| Material | Output | |
| Unit | Output | |
| DifferenceInventory | Output | |
| DifferencePieces | Output | |
| Result | Output | object with two keys:<br>`Status`<br>&nbsp;&nbsp;&nbsp;**S**: Successful<br>&nbsp;&nbsp;&nbsp;**I**: Informative<br>&nbsp;&nbsp;&nbsp;**E**: Error<br>`Message`: _string_ |

## Current Issues & Notes

### Units

Need clarification from the customer on primary and secondary units of measurement.
