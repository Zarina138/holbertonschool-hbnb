# HBnB Evolution – High-Level Package Diagram

## Objective
This document presents a high-level package diagram for the HBnB application.  
It shows the three-layer architecture and how the layers communicate through the **Facade Pattern**.

---

## 1. Layer Overview

### **1. Presentation Layer (API & Services)**
- Handles all user interactions.
- Contains API endpoints and service handlers.
- Sends requests to the Business Logic Layer through the Facade.

### **2. Business Logic Layer (Models & Facade)**
- Contains the core application logic.
- Includes main entities:
  - User
  - Place
  - Review
  - Amenity
- Includes the **HBnB Facade**, which provides a single entry point for the Presentation Layer.

### **3. Persistence Layer (Repositories / Database Access)**
- Responsible for data storage and retrieval.
- Communicates directly with the database.
- Contains repository classes for each model.

---

## 2. Package Diagram (Mermaid UML)

```mermaid
%% High-Level Package Diagram for HBnB Evolution

graph TD

    %% Presentation Layer
    subgraph Presentation_Layer["Presentation Layer"]
        API[API Endpoints / Services]
    end

    %% Business Logic Layer
    subgraph Business_Logic_Layer["Business Logic Layer"]
        Facade[HBnB Facade]
        Models[Models: User, Place, Review, Amenity]
    end

    %% Persistence Layer
    subgraph Persistence_Layer["Persistence Layer"]
        Repositories[Repositories / Database Access]
    end

    API --> Facade : Uses Facade Pattern
    Facade --> Models
    Facade --> Repositories : Database Requests
```

---

## 3. How the Facade Pattern Works

The Facade Pattern provides a **single unified interface** for the Presentation Layer.

### Without Facade ❌
- API would call models directly.
- More coupling, harder to maintain.

### With Facade ✔️
- API → Facade → Models / Repositories
- Clean architecture
- Easier to test
- Layers are isolated

---

## 4. Summary
- The diagram clearly shows the 3 main layers of the HBnB Architecture.
- Communication always flows through the Facade.
- This structure ensures clean separation of concerns and scalable design.


