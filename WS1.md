# WS1: Warehouse Confirms Reception of a Container

## Parameters

| Parameter | Type |
|----------|--------|
| Warehouse company | Input |
| Container N° | Input |
| Warehouse-ID (Plant-Sto.Loc) | Input |
| CMPC PO N° | Input |
| B/L N° | Input |
| CMPC Invoice N° | Input |
| Arrival date to the warehouse | Input |
| Error/Success message table | Output |

**Note** Currently an issue exists with determining if the order is from a firm sale or general inventory.

**Note** For _pulp_ orders, GWSI has asked the customer if the `batchNumber` should be sent as part of the response table, as this value is typically provided by hand.

> For Pulp, it is expected that `Batch N°` to be sent in the `Unit-ID` field.

No `Unit-ID` specced at this time.

## Current Issues & Notes

### Container Number

Container number values are not always unique. We have requested the customer add a parameter that combines the container number with the ship date to create a unique value. If the customer will not comply, we will need our own parameter that holds a unique value.

Customer response:

> Because of this, we are always asking additionally for these fields `CMPC PO N°`, `B/L N°` and `CMPC Invoice N°`

**Question** What does GWSI want to do in this case? In our system do we use a unique key and pass everything back?

### Customer Invoice Number

GWSI does not currently capture the CMPC Invoice N° in our data base, this value is not available to return in this message stream. This value however is required.

`CMPC Invoice N°`

### WS0 Comparison

Is there a need to compare the WS0 data with what is actually received? If so, do we generate a report for the customer? Is there a common key between WS0 and WS1 to perform the comparison?

### No WS0 Data Provided

There are instances when a container is received with no prior WS0 data. An example of this type of scenario: the customer purchases material from a US supplier. Do we simply add the contents into inventory? Is a report needed?

### Damaged Items

How to we address damaged items? Typically we're required to send pictures and follow up via phone/email. Is there a workflow to accept the container and split the good inventory from the damaged? How can we resolve the damaged items?

### Multiple Confirmations

What is the workflow in the case were a container is accepted, but then reopened (some type of edit required, for example, adding additional notes), and then confirmed again? Can we update the original record? Do we send a new record?

### Restrictions Needed

There is currently a problem with restricting the picking of items for firm sales on the scanners. We are proposing creating different customer entities for firm sales vs. open inventory sales as a way of verifying the items picked match customer requirements. Need to discuss this further with the development team.