# Vehicle Service Management

An end-to-end Pega Infinity case management application designed to automate and streamline vehicle service bookings, diagnostic assessments, customer approvals, and fulfillment.

---

## 🚀 Application Overview

* **Application Name:** `NIP-VehicleService-UmanshiGupta`
* **Case Type Name:** `Vehicle Service Request`
* **Author / Developer:** Umanshi Gupta
* **Platform:** Pega Infinity

---

## 📋 Case Lifecycle Stages

The case progresses through the following stages from creation to resolution:

1. **Submit Request:** Customer initiates the process by submitting vehicle details, model, and issue description.
2. **Inspection:** A Service Advisor evaluates the vehicle, inputs condition ratings, and adds detailed diagnostic notes.
3. **Estimation & Approval:** The system automatically calculates total costs, and the case is routed to the customer for estimate review and approval.
4. **Service Execution:** Tasks are automatically routed to specialized work queues based on vehicle classification for technician assignment.
5. **Resolution:** Service completion is finalized, and automated notifications are dispatched.

---

## 👥 Personas & Work Queues

### Personas
* **Customer:** Initiates requests, reviews itemized estimates, and provides approval or rejection.
* **Service Advisor:** Performs vehicle inspections, captures condition ratings, and manages service notes.
* **Technician:** Executes assigned vehicle repairs and updates service statuses.

### Work Queues
* **`HeavyVehicleQueue`:** Automatically routes service execution tasks for heavy commercial vehicles to specialized technicians.
* **`LightVehicleQueue`:** Default fallback work queue for standard passenger vehicles and light automobiles.

---

## ⚙️ Key Technical Configurations & Rules

* **Declare Expression (`CalculateTotalCost`):** Automatically computes the dynamic `TotalCost` field as a sum of `LaborCost` and `PartsCost`.
* **Dynamic Routing Rule (`RouteTasks`):** Evaluates the `VehicleType` property to dynamically route cases to either `HeavyVehicleQueue` or `LightVehicleQueue`.
* **Service Level Agreement (`ServiceLevelAgreement`):** Configured on the case type with a **2-day goal** and **3-day deadline** to automatically escalate case priority upon expiration.
* **Data Object (`VehicleProperties`):** Reusable data model capturing `Vehicle ID`, `Vehicle Model`, `Vehicle Type`, `Registration Number`, and `Customer Name`.

---

## 📦 Repository Contents

* **`META-INF/`** & **`Application.xml`**: Pega application descriptor and metadata.
* **`VehicleServicePackage_01.01.01_rules.jar`**: Pega rules product package.
* **`VehicleServicePackage_01.01.01_schema.jar`**: Pega database schema package.
* **`application.properties`**: Configuration properties file.

---

## 📄 License

This project is licensed under the terms of the [MIT License](LICENSE).
