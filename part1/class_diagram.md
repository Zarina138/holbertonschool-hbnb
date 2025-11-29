# Business Logic Layer  Detailed Class Diagram (HBnB)

This document describes the detailed class diagram of the Business Logic layer of the HBnB application. It focuses on the main entities: User, Place, Review, and Amenity
including their attributes, methods, and relationships.

---

## Detailed Class Diagram

```mermaid
classDiagram

class User {
  +UUID id
  +string email
  +string password
  +string first_name
  +string last_name
  +datetime created_at
  +datetime updated_at
  +register()
  +login()
  +update_profile()
}

class Place {
  +UUID id
  +string name
  +string description
  +float price_per_night
  +UUID owner_id
  +datetime created_at
  +datetime updated_at
  +create_place()
  +update_place()
  +delete_place()
}

class Review {
  +UUID id
  +string comment
  +int rating
  +UUID user_id
  +UUID place_id
  +datetime created_at
  +datetime updated_at
  +create_review()
  +update_review()
  +delete_review()
}

class Amenity {
  +UUID id
  +string name
  +datetime created_at
  +datetime updated_at
  +add_amenity()
  +update_amenity()
  +delete_amenity()
}

User "1" --> "0..*" Place : owns
User "1" --> "0..*" Review : writes
Place "1" --> "0..*" Review : receives
Place "0..*" -- "0..*" Amenity : has

