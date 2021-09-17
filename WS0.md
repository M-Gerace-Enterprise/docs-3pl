# WS0: MPL Data

GWSI currently waiting for documentation from customer for this service.

## Data Fields

The following are common to all product lines:

Data Field | 3PL Field
---------|---------
ARRIVAL DATE | ExpectedDate |
CMPC_M_Invoice | SealNumber |
CONTAINER ID | ReferenceNumber = CONCATENATE(Container ID, Ship Date) to create a unique reference<br>TrailerNumber<br>**LARRY: NEED CLARIFICATION**  |
CONTAINER SEAL | SealNumber
CUSTOMER |  |
DESTINATION PORT |  |
Factura | not used |
FirmSale | |
INCOTERMS |  |
OCEAN BILL OF LADING | BillOfLading |
PO_CMPC | PurchaseOrderNumber |
PO_CUSTOMER | LotNumber (Firm Sale Only) |
PRODUCT (Lumber, Paper, Pulp) | We have a different Warehouse Location and 3PL Customer for each Warehouse ID and Product Line and Firm Sale Value<br>**LARRY: NEED CLARIFICATION**  |
SHIP DATE |  |
VESSEL | ShipCarrier |
VOYAGE |  |
Warehouse-ID (Plant-Sto.Loc) | |
WarehouseCompany | Fixed value `GWSI` |

### Lumber Product Line

The following are specific to the _Lumber_ product line:

Data Field | 3PL Field
---------|---------
SAP_Code | SKU<br>Quantity Default to Quantity of 1 per Unit ID<br>MUType (Default to 3PL Item setup)<br>**LARRY: NEED CLARIFICATION**  |
CUSTOMER SKU | |
BATCH | |
Unit_Id | SerialNumber<br>MULabel Set MU Label to be the same as SerialNumber<br>**LARRY: NEED CLARIFICATION**  |
Description | |
Length | |
Pcs_Unit | Qualifier<br>MULength (Default to 3PL Item setup)<br>MUWidth (Default to 3PL Item setup)<br>MUHeight (Default to 3PL Item setup)<br>**LARRY: NEED CLARIFICATION**  |
Lbs_unit | MUWeight<br>LocationField1 (Default to "APRON")<br>**LARRY: NEED CLARIFICATION** |

### Paper Product Line

The following fields are specific to the _Paper_ product line:

- Order_Item
- Spec Name
- CERTIFICATION
- Gsm
- Gross (Lbs)
- Net Weight (Lbs)
- Caliper
- Linear Feet
- Square Feet
- Width (In)
- Length diam (in)
- Sheets/Core

### Pulp Product Line

The following fields are specific to the _Pulp_ product line:

- Sheets/Core
- PROD_BATCH
- BALE QTY
- UNIT QTY
- NTGEW
- BRGEW
- TOTAL WEIGHT
- VOLUMEN
- UNIT ID
- PRODUCER

### Bag Product Line

Awaiting details from our customer.

## Additional Parameters & Issues

1. We have requested the customer add the following parameters to the data being sent:

- `FIRM_SALE`: boolean
  - approved by customer 15 September 2021, awaiting updated documentation
- `SEAL_NUMBER`: string
  - approved by customer 15 September 2021, awaiting updated documentation

2. **PULP Specific**: We have requested the customer add weights for each batch. Will discuss with customer.

## Developer Questions

- We would like to have the system automatically create entries for new items if the system does not have an entry for an item. Possible? Recommendations?
  - In the case new items are created automatically, we need an indicator that this type of event has occurred. Use existing 3PL UI? Something custom?
