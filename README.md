# Equipment Management System

A web application for managing and tracking measuring instruments, tools, and supporting equipment. The system provides centralized equipment management, status and location tracking, equipment assignment and return, reservations, fault reporting, calibration tracking, and usage history.

## Features

### Authentication and User Roles

Users access the application using a unique username and password. The system supports role-based access control, allowing different users to access different functionalities depending on their assigned role. Passwords are stored as securely hashed values.

The application supports the following roles:

* **Administrator** – manages users, equipment categories, equipment data, statuses, and system history.
* **Operator / Technician** – views equipment, assigns and returns equipment, creates reservations, and reports faults.
* **Manager / Supervisor** – has access to equipment, active assignments, history, reported faults, and reports.

## Equipment Management

The system stores detailed information for every instrument, tool, or equipment item, including:

* name and description;
* category;
* manufacturer and model;
* serial number;
* inventory number;
* production or purchase year;
* location;
* equipment image;
* current status;
* responsible person;
* currently assigned user;
* equipment expert;
* additional equipment;
* notes.

Equipment is organized into categories such as instruments, cables, probes, emulators and development systems, and tools. Categories can be extended through the administration functionality.

## Equipment Status

The application tracks the current status of each equipment item:

* Available
* Assigned
* Reserved
* Faulty
* Retired

Equipment status is automatically updated during assignment and return operations, while administrators can manually change the status when necessary.

## Equipment Assignment and Return

Users can assign available equipment directly through the application. During the assignment process, the system records the user, equipment, assignment date and time, as well as the project, task, or purpose for which the equipment is being used. After a successful assignment, the equipment status becomes **Assigned**.

When equipment is returned, the system records the return date and time, user, equipment condition, and any additional notes or fault reports. The active assignment is closed, while the complete assignment period remains stored in the history.

Faulty or retired equipment cannot normally be assigned.

## Reservations

If equipment is currently assigned to another user, it can be reserved.

The reservation system stores:

* user who created the reservation;
* reservation date and time;
* queue position;
* reservation status;
* note or reason.

Reservations are processed according to their creation order.

## Fault and Damage Reporting

Users can report equipment faults or damage directly through the application.

Each report contains:

* affected equipment;
* user who reported the issue;
* date and time;
* fault or damage description;
* report status.

After a fault is reported, the equipment status is automatically changed to **Faulty**. An administrator can change the status after the equipment has been inspected or repaired.

## Calibration Management

For measuring instruments that require calibration, the system stores:

* whether calibration is required;
* last calibration date;
* next calibration date;
* calibration result;
* calibration notes.

The application determines the current calibration status:

* Calibration valid
* Calibration expiring soon
* Calibration expired
* Calibration not required
* Calibration data not entered

By default, the system considers calibration to be expiring soon when there are 30 days or less remaining until the next calibration date.

When assigning an instrument whose calibration has expired or is about to expire, the application displays a warning to the user.

## Equipment History

The application maintains a history of important equipment-related events, including:

* equipment creation;
* equipment data changes;
* status changes;
* calibration changes;
* assignments and returns;
* reservations and cancellations;
* fault reports;
* changes of responsible person;
* location changes.

This provides a complete overview of equipment usage and changes over time.

## Search and Filtering

The equipment list supports searching and filtering by:

* equipment name;
* inventory number;
* serial number;
* manufacturer;
* model;
* category;
* status;
* location;
* currently assigned user;
* responsible person;
* equipment expert;
* project or task;
* calibration status;
* next calibration date.

Equipment lists also support sorting by the main columns.

## Dashboard and Reports

The dashboard provides an overview of the most important system information:

* total equipment count;
* available equipment;
* assigned equipment;
* faulty equipment;
* user's active assignments;
* pending reservations;
* instruments with expired or upcoming calibration;
* recent activities.

The system provides reports for:

* all equipment;
* available and assigned equipment;
* faulty equipment;
* equipment by location;
* equipment by user;
* active assignments;
* assignment history;
* active reservations;
* instruments with expired calibration;
* instruments with upcoming calibration.

## System Architecture

The application follows a layered architecture with clearly separated components:

* **Frontend** – user interface;
* **Backend REST API** – request processing and communication with the frontend;
* **Database** – persistent storage of users, equipment, and system activities;
* **Authentication & Authorization** – user authentication and access control;
* **Business Logic** – implementation of application rules;
* **Data Access Layer** – communication with the database.

## Technologies

### Backend

* Java
* Spring Boot
* Spring REST API
* Spring Security
* JPA / Hibernate

### Frontend

* React
* Vite
* JavaScript / TypeScript
* HTML
* CSS

### Database

* PostgreSQL

### Version Control

* Git
* GitHub

## Security

The system uses user authentication and role-based access control. Unauthenticated users cannot access the application, while access to specific features is determined by the user's role.

Passwords are stored only as hashes, and important system actions are recorded in the application history.

## Business Rules

The application enforces business rules to maintain data consistency, including:

* inventory numbers must be unique;
* equipment with an active assignment cannot be deleted;
* equipment uses soft delete instead of physical deletion;
* faulty equipment cannot be assigned;
* every assignment must have a start date;
* returning equipment closes the active assignment;
* reservations are processed in creation order;
* historical records cannot be deleted through the standard user interface.


The interface is designed to provide convenient access to equipment search, filtering, details, assignment, return, reservation, fault reporting, and calibration status.

## Purpose

The goal of the system is to provide a centralized and efficient solution for managing measuring instruments, tools, and supporting equipment, while providing clear visibility into equipment availability, assignments, reservations, faults, usage history, and calibration status.
