# System Architecture

Client: Python script / notebook

Database: MongoDB Atlas (cloud)

Collections: users, employees, products, orders

Driver: PyMongo

Diagrams: Lucidchart (for schema visualization)

# Data Modeling & Collection Organization
## Entities

User – customers

Employee – employees who process orders

Product – products available in the store

Order – orders placed by users

# Relationships

User → Orders → a user can place multiple orders

Order → Products → an order can contain multiple products (stored as an array)

Order → Employee → an employee can process multiple orders

# Schema Design Strategies
## Referencing (Implemented)

orders.userId → reference to users._id

orders.employeeId → reference to employees._id

orders.products[i].productId → reference to products._id

Advantages: scalable, consistent data, smaller documents
Disadvantages: joins/aggregations are needed for combining data

## Embedding (Alternative Model)

All product details could be embedded inside the orders collection:

"products": [
  {"name": "Laptop", "price": 1200, "quantity": 3},
  {"name": "Mouse", "price": 50, "quantity": 1}
]


Advantages: fast reads, no joins needed
Disadvantages: data duplication, harder to maintain

Conclusion: Referencing was chosen for this project for better scalability and maintainability.

<img width="559" height="650" alt="Screenshot (38)" src="https://github.com/user-attachments/assets/fe857d21-f3ba-46e0-9e50-a0232c6fe6f5" />

