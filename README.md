# SAP RAP Purchase & Inventory Management

> An end-to-end **SAP ABAP Cloud** application for Purchase Order and Inventory Management, developed using **RAP, CDS, OData V4 and Fiori Elements**.

---

## Overview

This project demonstrates the development of a transactional business application using the **SAP RESTful Application Programming Model (RAP)**.

The application manages:

* Purchase Orders
* Purchase Order Items
* Inventory

It implements business logic through **RAP validations, determinations and actions**, exposes the application through **OData V4**, and provides a **Fiori Elements** user interface.

---

## Key Features

| Feature                   | Implementation          |
| ------------------------- | ----------------------- |
| Purchase Order Management | RAP Business Object     |
| Purchase Item Management  | RAP Composition         |
| Inventory Management      | CDS Association         |
| CRUD Operations           | Managed RAP             |
| Quantity Validation       | RAP Validation          |
| Item Amount Calculation   | RAP Determination       |
| Purchase Order Processing | RAP Action              |
| Authorization             | RAP Authorization       |
| Service Exposure          | OData V4                |
| User Interface            | Fiori Elements          |
| UI Configuration          | CDS Metadata Extensions |
| Search & Filtering        | Fiori Elements          |

---

## Technology Stack

* **SAP BTP ABAP Environment**
* **ABAP Cloud**
* **ABAP**
* **Core Data Services (CDS)**
* **RESTful Application Programming Model (RAP)**
* **OData V4**
* **SAP Fiori Elements**
* **Eclipse ADT**

---

## Application Architecture

The project follows the standard layered architecture of an SAP RAP application.

```text
┌──────────────────────────────┐
│       Fiori Elements         │
│      List Report / Page      │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│          OData V4            │
│       Service Binding        │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      Service Definition      │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       RAP Business Object    │
│                              │
│  Behavior Definition         │
│  Behavior Implementation     │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        CDS Data Model        │
│                              │
│ Header → Items → Inventory   │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       ABAP Database Tables   │
└──────────────────────────────┘
```

---

## Data Model

The application contains three main entities.

### Purchase Order Header

Root entity representing the Purchase Order.

**Main fields:**

* PO ID
* Supplier
* PO Date
* Status
* Total Amount
* Currency

### Purchase Order Item

Child entity containing individual Purchase Order items.

**Main fields:**

* PO ID
* Item Number
* Material
* Quantity
* Unit Price
* Currency
* Item Amount

### Inventory

Entity containing material-level inventory information.

**Main fields:**

* Material
* Quantity
* Unit

### Entity Relationship

```text
Purchase Order Header
          │
          │ Composition
          ▼
Purchase Order Item
          │
          │ Association
          ▼
       Inventory
```

---

## CDS Data Model

The CDS layer defines the application's business data model and relationships.

| CDS Entity             | Purpose                    |
| ---------------------- | -------------------------- |
| `ZCDS_PURCHASE_HEADER` | Purchase Order root entity |
| `ZCDS_PURCHASE_ITEM`   | Purchase Order item entity |
| `ZCDS_INVENTORY`       | Inventory entity           |

The Purchase Order Header is defined as the **root entity**.

The Header-to-Item relationship uses **CDS composition**, while the Item-to-Inventory relationship uses a **CDS association**.

---

## RAP Behavior

The application uses **Managed RAP** for transactional processing.

### CRUD

The Business Object supports:

* Create
* Read
* Update
* Delete

### Validation

A validation checks the Purchase Order Item quantity during save.

```text
Quantity <= 0
       │
       ▼
Validation Error
```

This prevents invalid item quantities from being persisted.

### Determination

A RAP determination automatically calculates the Item Amount.

```text
Item Amount = Quantity × Unit Price
```

This demonstrates automatic business logic execution during RAP processing.

### Action

A **Submit Purchase Order** action is implemented as an explicit business operation on the Purchase Order.

---

## Business Process

```text
Create Purchase Order
          │
          ▼
Add Purchase Order Items
          │
          ▼
Validate Quantity
          │
          ▼
Calculate Item Amount
          │
          ▼
Calculate Purchase Order Total
          │
          ▼
Submit Purchase Order
```

---

## Service Exposure

The RAP Business Object is exposed using **OData V4**.

```text
RAP Business Object
        │
        ▼
Service Definition
        │
        ▼
Service Binding
        │
        ▼
OData V4
        │
        ▼
Fiori Elements
```

The service layer provides the interface between the RAP backend and the Fiori Elements application.

---

## Fiori Elements

The application uses **Fiori Elements** to provide the user interface.

Implemented UI capabilities include:

* List Report
* Object Page
* Search
* Filtering
* Purchase Order navigation
* Item table
* Business actions
* CDS-based UI annotations

The UI is generated using the metadata provided by the RAP service and CDS annotations.

---

## Project Structure

```text
SAP-RAP-Purchase-Inventory-Management
│
├── Database Tables
│   ├── ZPURCHASE_HDR
│   ├── ZPURCHASE_ITM
│   └── ZINVENTORY
│
├── CDS Data Model
│   ├── ZCDS_PURCHASE_HEADER
│   ├── ZCDS_PURCHASE_ITEM
│   └── ZCDS_INVENTORY
│
├── RAP Behavior
│   ├── Behavior Definition
│   └── Behavior Implementation
│
├── Metadata Extensions
│
├── Service Definition
│
├── Service Binding
│
└── Test Data
```

---

## Development Environment

| Component        | Details        |
| ---------------- | -------------- |
| Platform         | SAP BTP        |
| Runtime          | ABAP Cloud     |
| IDE              | Eclipse ADT    |
| Service Protocol | OData V4       |
| UI Framework     | Fiori Elements |

---

## Concepts Demonstrated

This project provides hands-on implementation of:

**ABAP Cloud**
Cloud-ready ABAP development using the restricted ABAP language and released APIs.

**CDS**
Data modeling, associations, compositions and UI annotations.

**RAP**
Business Objects, managed behavior, validations, determinations, actions and authorization.

**OData V4**
Service exposure of the RAP Business Object.

**Fiori Elements**
Metadata-driven application UI using List Report and Object Page.

---

## Testing

The application was tested using the SAP ABAP Cloud development environment and Fiori Elements preview.

Testing covers:

* Purchase Order creation
* Purchase Order Item creation
* Quantity validation
* Item Amount calculation
* Purchase Order total calculation
* Submit action
* Inventory data access
* Fiori Elements navigation
* RAP transactional behavior

---

## Future Enhancements

* Advanced Purchase Order approval workflow
* Enhanced inventory stock update processing
* Supplier master data
* Material master integration
* Additional reporting capabilities
* Extended Fiori Elements UI adaptations

---

## Project Purpose

This project was developed to demonstrate practical experience with **SAP ABAP Cloud and RAP application development**, covering the complete backend-to-UI flow from data modeling to transactional processing and Fiori Elements consumption.
