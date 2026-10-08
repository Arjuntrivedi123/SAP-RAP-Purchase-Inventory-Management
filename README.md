SAP RAP Purchase & Inventory Management

An end-to-end SAP ABAP Cloud application developed using the RESTful Application Programming Model (RAP) for Purchase Order and Inventory Management.

The project demonstrates modern SAP cloud application development using ABAP Cloud, Core Data Services (CDS), RAP Business Objects, OData V4 and Fiori Elements.

Project Overview

The application provides a structured solution for managing Purchase Orders, Purchase Order Items and Inventory data.

The project implements transactional business logic using the RAP framework, including validations, determinations, actions and authorization handling.

The RAP Business Object is exposed through an OData V4 service and consumed using a Fiori Elements-based user interface.

Business Scope

The application consists of three main business entities:

Purchase Order Header
Purchase Order Item
Inventory

The Purchase Order Header acts as the root entity and maintains its associated Purchase Order Items through a CDS composition.

Purchase Order Items are associated with Inventory based on the Material field.

Key Features
Purchase Order Header management
Purchase Order Item management
Inventory data management
Header-Item composition
Item-to-Inventory association
Managed RAP Business Object
Create, Read, Update and Delete operations
Purchase Order Item quantity validation
Automatic Item Amount calculation
Purchase Order total calculation
Purchase Order Submit action
RAP validations
RAP determinations
RAP actions
Authorization handling
OData V4 service exposure
Fiori Elements user interface
CDS-based UI annotations
Search and filtering
List Report and Object Page
Technology Stack
Technology	Purpose
SAP BTP ABAP Environment	Cloud development platform
ABAP Cloud	Backend development
ABAP	Business logic
CDS	Data modeling
RAP	Transactional application development
OData V4	Service exposure
Fiori Elements	User interface
Eclipse ADT	Development environment
Application Architecture

The application follows the standard layered architecture of an SAP RAP application.

Database Tables
       |
       v
CDS Data Model
       |
       v
RAP Business Object
       |
       +-- Behavior Definition
       |
       +-- Behavior Implementation
       |
       v
Service Definition
       |
       v
Service Binding
       |
       v
OData V4
       |
       v
Fiori Elements
Architecture Layers

Database Layer

Persistent data is stored in custom ABAP Cloud database tables:

ZPURCHASE_HDR
ZPURCHASE_ITM
ZINVENTORY

Data Modeling Layer

CDS view entities define the business data model, relationships and reusable business data.

Behavior Layer

RAP Behavior Definitions and Behavior Implementations define transactional operations and business logic.

This includes validations, determinations, actions and authorization handling.

Service Layer

The RAP Business Object is exposed through a Service Definition and Service Binding using OData V4.

UI Layer

Fiori Elements consumes the OData V4 service and provides the application user interface.

Data Model
Purchase Order Header

The Purchase Order Header represents the root entity of the application.

Main attributes include:

PO ID
Supplier
PO Date
Status
Total Amount
Currency
Purchase Order Item

The Purchase Order Item represents individual materials belonging to a Purchase Order.

Main attributes include:

PO ID
Item Number
Material
Quantity
Unit Price
Currency
Item Amount
Inventory

The Inventory entity maintains material-level stock information.

Main attributes include:

Material
Quantity
Unit
CDS Data Model

The application uses CDS view entities to define the business data model.

ZCDS_PURCHASE_HEADER
          |
          | Composition
          v
ZCDS_PURCHASE_ITEM
          |
          | Association
          v
ZCDS_INVENTORY

The Purchase Order Header is defined as the root entity.

Purchase Order Items are modeled as dependent child entities using CDS composition.

Purchase Order Items are associated with Inventory using the Material field.

RAP Behavior

The application uses a managed RAP Business Object for transactional processing.

CRUD Operations

The Business Object supports:

Create
Read
Update
Delete
Validation

A RAP validation checks the Purchase Order Item quantity during save processing.

The validation prevents invalid quantities from being saved.

Quantity <= 0
       |
       v
Validation Error
Determination

A RAP determination automatically calculates the Purchase Order Item Amount.

Item Amount = Quantity × Unit Price

This demonstrates automatic business logic execution during RAP processing.

Actions

A Submit action is implemented for the Purchase Order Business Object.

The action provides an explicit business operation for processing the Purchase Order.

Business Process

The implemented application flow is:

Create Purchase Order
        |
        v
Add Purchase Order Items
        |
        v
Validate Quantity
        |
        v
Calculate Item Amount
        |
        v
Calculate Purchase Order Total
        |
        v
Submit Purchase Order
OData V4 Service

The RAP Business Object is exposed through an OData V4 service.

RAP Business Object
        |
        v
Service Definition
        |
        v
Service Binding
        |
        v
OData V4
        |
        v
Fiori Elements

The OData service provides the interface between the RAP backend and the Fiori Elements application.

Fiori Elements

The application uses Fiori Elements for the user interface.

The UI provides:

List Report
Object Page
Search
Filtering
Purchase Order navigation
Item table
Business actions
CDS-driven UI annotations

The UI is generated using metadata provided by the RAP service and CDS annotations.

Project Structure
SAP-RAP-Purchase-Inventory-Management
|
+-- Database Tables
|   +-- ZPURCHASE_HDR
|   +-- ZPURCHASE_ITM
|   +-- ZINVENTORY
|
+-- CDS Data Model
|   +-- ZCDS_PURCHASE_HEADER
|   +-- ZCDS_PURCHASE_ITEM
|   +-- ZCDS_INVENTORY
|
+-- RAP Behavior
|   +-- Behavior Definition
|   +-- Behavior Implementation
|
+-- Metadata Extensions
|
+-- Service Definition
|
+-- Service Binding
|
+-- Test Data
Development Environment

The project was developed using:

SAP BTP ABAP Environment
Eclipse
ABAP Development Tools (ADT)
RAP Concepts Demonstrated

This project demonstrates practical implementation of:

ABAP Cloud
CDS View Entities
CDS Associations
CDS Composition
RAP Business Objects
Managed RAP
Behavior Definitions
Behavior Implementations
RAP Validations
RAP Determinations
RAP Actions
Authorization
OData V4
Service Definitions
Service Bindings
Fiori Elements
Metadata Extensions
Testing

The application was tested using the SAP ABAP Cloud development environment and Fiori Elements preview.

Testing includes:

Purchase Order creation
Purchase Order Item creation
Quantity validation
Automatic Item Amount calculation
Purchase Order total calculation
Submit action
Inventory data access
Fiori Elements navigation
RAP transactional behavior
Future Enhancements

Potential future enhancements include:

Advanced Purchase Order approval workflow
Role-based authorization
Enhanced inventory stock update processing
Supplier master data
Material master integration
Additional reporting capabilities
Extended Fiori Elements UI adaptations
