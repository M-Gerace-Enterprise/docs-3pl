# WS2: Order Check

An event firing on an interval that checks for new orders from the customer. GWSI would like the development team's recommendation on how to implement this functionality, and what an ideal interval would be.

## Parameters

| Parameter | Type | Value |
|----------|--------|------|
| Warehouse company | Input | Fixed value `GWSI` |
| Warehouse-ID (Plant-Sto.Loc) | Input | Describes the specific Warehouse facility ID where the Container has been received. If needed, an equivalence with SAP Plant and Storage location will be created. |
| Delivery | Output | |
| CustomerName | Output | |
| CustomerPONumber | Output | |
| DeliveryDate | Output | |
| SalesType | Output | F: Firm Order<br>O: Other |
| Status | Output | I: New<br>U: Update<br>D: Delete |
| ShipToAddress | Output | |
| City | Output | |
| Zipcode | Output | |
| Country | Output | |
| SpecialRemarks | Output | |
| DeliveriesDetail | Output | |

`DeliveriesDetail` object contains the following parameters:

| Parameter | Type | Value |
|----------|--------|------|
| Delivery | Output | |
| DeliveryItemRef | Output | |
| Material | Output | |
| UnitsQuantity | Output | |
| QuantityBUoM | Output | |
| UnitOfMeasure | Output | |
| PiecesPerUnit | Output | |
| CustomerQualifer | Output | |
| UnitID | Output | **Note** for _pulp_, it is expected that `Batch N` be sent in this field. |


## Current Issues & Notes

### Inconsistent Values

The `WarehouseID` value is inconsistent between WS1 and WS2. We have reached out to the customer for clarification.

### Business Unit Information

GWSI has requested the customer identify the business unit associated with each order.

### Error Scenarios

- If an item is not in our system
- If `piecesPerUnit` does not match

In all error instances, an order in one order should not shut down the entire system.

### Accept & Advise

- If inventory is inadequate, we accept the order and wait for the customer to advise on how to proceed. Current 3PL UI includes indicators for these scenarios.

### Additional Questions

- How do we handle `UnitsOfMeasure`? bundles vs. pallets vs etc.
