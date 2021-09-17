# WS3: Outbound Delivery Confirmation

GWSI confirms preparation and shipment of an outbound delivery.

## Parameters

| Parameter | Type | Notes |
|----------|--------| ----- |
| Carrier name | Input | |
| Outbound delivery | Input | |
| Shipment date | Input | |
| Status | Input | |
| Truck ID | Input | |
| Units | Input | Table with the Units picked for the outbound delivery |
| Warehouse company | Input | |
| Error/Success message table | Output | |

`Units` object contains the following keys:

| Parameter | Type | Notes |
|----------|--------| ----- |
| DeliveryItemRef | Output | This field represents the SAP Delivery-ítem to whom each Unit-ID belongs. We need it to identify under which specific item needs to be updated each of the Unit-IDs you confirm as delivered. |
| Material | Output | |
| Quantity | Output | |
| UnitID | Output | |
| UnitOfMeasure | Output | |

**Note** For _pulp_ orders, GWSI has asked the customer if the `batchNumber` should be sent as part of the response table, as this value is typically provided by hand.

> For Pulp, it is expected that `Batch N°` to be sent in the `Unit-ID` field.

## Current Issues & Notes

### Reduced Order Number Scenario

In the event that inventory is damaged, or an outbound truck is overweight, a portion of the order may be removed from the outbound delivery. In this scenario, GWSI will report the number actually shipped and the remained will remain in inventory. Do we send a note or indication with the transaction?

### Units

Our teams need to discuss primary and secondary units of measurement across business units. We want to verify we are interpreting and providing back details in the correct units.

> Do you think it is needed to build a sheet with the proposed unit of measure to be used for each of the product types?
