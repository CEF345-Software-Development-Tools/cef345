# MarketStock Software Requirements Specification (SRS)

## 1. Introduction

### 1.1 Purpose

This document describes the software requirements for MarketStock, a stock and sales management system designed to help small shops manage products, record sales, monitor stock levels and keep track of customer credit transactions.

### 1.2 Scope

MarketStock will provide a simple system for managing daily shop activities. It will allow authorised users to manage products, record sales, update stock quantities, manage customer credit and repayments, and view daily sales reports.

The system will have two main user roles: Owner and Assistant.

### 1.3 Definitions

- **SRS:** Software Requirements Specification.
- **FR:** Functional Requirement.
- **NFR:** Non-Functional Requirement.
- **Owner:** The person responsible for managing the shop and its records.
- **Assistant:** A staff member who performs daily shop operations.
- **XAF:** Central African CFA franc, the currency used for transactions.
- **MoSCoW:** A method of prioritising requirements as Must, Should, Could and Won't.

## 2. Overall Description

### 2.1 Product Perspective

MarketStock is intended to provide a central place for managing shop activities. It will reduce reliance on manual records and make it easier to monitor sales, stock quantities and customer debts.

### 2.2 User Classes and Characteristics

**Owner**
- Has full access to the system.
- Can manage products and user accounts.
- Can view reports and credit records.
- Has permission to perform restricted administrative actions.

**Assistant**
- Can log in using an authorised account.
- Can view stock information.
- Can record sales, restocking and customer repayments.
- Cannot perform restricted owner-only actions.

### 2.3 Operating Environment

The system is intended to operate through a web browser on desktop computers, tablets and mobile phones. It should support commonly used browsers such as Google Chrome, Mozilla Firefox and Microsoft Edge.

### 2.4 Constraints

- The system must use XAF for recording monetary transactions.
- Access to protected features must require authentication.
- Certain administrative actions must be restricted to the Owner.
- The interface should support mobile devices.

### 2.5 Assumptions and Dependencies

- Users will have valid login credentials.
- Product information and prices will be entered correctly by authorised users.
- The shop will provide the devices and browser access needed to use the system.
- The system will depend on a working device and suitable browser.

## 3. Functional Requirements

### FR-01: User Login
**Description:** The system shall allow registered users to log in using a username and password.

**Priority:** Must

### FR-02: Manage Products
**Description:** The system shall allow the Owner to add, edit and view products.

**Priority:** Must

### FR-03: Restock Products
**Description:** The system shall allow authorised users to record new stock received.

**Priority:** Must

### FR-04: View Stock
**Description:** The system shall display the available quantity of each product.

**Priority:** Must

### FR-05: Record Sales
**Description:** The system shall allow assistants to record customer sales.

**Priority:** Must

### FR-06: Calculate Sale Total
**Description:** The system shall calculate the total cost of selected products and quantities.

**Priority:** Must

### FR-07: Update Stock After Sales
**Description:** The system shall automatically reduce stock quantities after a successful sale.

**Priority:** Must

### FR-08: Prevent Insufficient Stock
**Description:** The system shall prevent a sale when the requested quantity exceeds available stock.

**Priority:** Must

### FR-09: Record Credit Sales
**Description:** The system shall allow authorised users to record sales made on credit.

**Priority:** Should

### FR-10: Record Repayments
**Description:** The system shall allow authorised users to record customer repayments.

**Priority:** Should

### FR-11: View Credit Book
**Description:** The system shall display customer credit balances and repayment records.

**Priority:** Should

### FR-12: View Daily Sales Report
**Description:** The system shall generate a daily sales report.

**Priority:** Should

### FR-13: Manage Users
**Description:** The system shall allow the Owner to create, update and manage user accounts.

**Priority:** Should

## 4. Non-Functional Requirements

### NFR-01: System Security
**Description:** The system shall require users to authenticate before accessing protected pages and shall restrict sensitive actions to authorised roles.

**Priority:** Must

### NFR-02: System Performance
**Description:** Normal pages and sale calculations should respond within 3 seconds under normal operating conditions.

**Priority:** Must

### NFR-03: Browser Compatibility
**Description:** The system should work correctly on supported versions of Chrome, Firefox and Edge.

**Priority:** Should

### NFR-04: Ease of Use
**Description:** The system should provide a clear and easy-to-understand interface for shop owners and assistants.

**Priority:** Should

### NFR-05: Mobile Responsiveness
**Description:** The system should display properly on mobile screens without unnecessary horizontal scrolling.

**Priority:** Should

## 5. Use Case Diagram and Descriptions

### 5.1 Use Case Diagram

The use case diagram represents the interactions between the MarketStock system and its two main actors: Owner and Assistant.

The diagram should be stored at:

`docs/diagrams/usecases.drawio.svg`

### 5.2 Use Case 1: Record a Sale

**Use Case ID:** UC-01

**Primary Actor:** Assistant

**Description:** Allows an assistant to record a customer's purchase.

**Preconditions:**
- The assistant is logged in.
- The required products exist in the system.
- Sufficient stock is available.

**Main Flow:**
1. The assistant opens the sales page.
2. The assistant selects the products purchased.
3. The assistant enters the quantities.
4. The system calculates the total amount.
5. The assistant confirms the sale.
6. The system saves the sale and updates stock quantities.

**Alternative Flow:**
- If the requested quantity exceeds available stock, the system rejects the sale and displays an error message.

**Postcondition:** The sale is saved and stock quantities are updated.

### 5.3 Use Case 2: Restock Product

**Use Case ID:** UC-02

**Primary Actor:** Assistant

**Description:** Allows an assistant to record new stock received by the shop.

**Preconditions:**
- The assistant is logged in.
- The product already exists in the system.

**Main Flow:**
1. The assistant opens the restocking page.
2. The assistant selects a product.
3. The assistant enters the quantity received.
4. The system validates the quantity.
5. The assistant confirms the restocking.
6. The system increases the available stock.

**Alternative Flow:**
- If the quantity is zero or negative, the system rejects the entry and displays an error message.

**Postcondition:** The product's stock quantity is updated.

### 5.4 Use Case 3: Record a Repayment

**Use Case ID:** UC-03

**Primary Actor:** Assistant

**Description:** Allows an assistant to record a customer's repayment of an outstanding credit balance.

**Preconditions:**
- The assistant is logged in.
- The customer has an outstanding credit balance.

**Main Flow:**
1. The assistant opens the credit records.
2. The assistant selects the customer.
3. The assistant enters the repayment amount.
4. The system checks the amount against the outstanding balance.
5. The assistant confirms the repayment.
6. The system saves the repayment and updates the balance.

**Alternative Flow:**
- If the repayment amount exceeds the outstanding balance, the system rejects the entry and displays an error message.

**Postcondition:** The repayment is recorded and the customer's outstanding balance is reduced.

## 6. Requirements Priorities

The MoSCoW method is used to organise the requirements.

- **Must:** Essential requirements needed for the first working version.
- **Should:** Important requirements that should be implemented if possible.
- **Could:** Useful additional features that may be considered later.
- **Won't:** Features excluded from the current release.

The current proposed Must and Should classifications are shown in the functional and non-functional requirements tables.

## 7. Out of Scope

The following features are not included in the current version of MarketStock:

- Online payment gateway integration.
- Automatic ordering from suppliers.
- Multi-branch shop management.
- Advanced financial forecasting.
- Customer mobile applications.

## 8. Document Status

This SRS is a working draft prepared for the CEF345 MarketStock project. The requirements and priorities should be reviewed and approved by the group, and updated using the problem statement and findings from the required business observation.