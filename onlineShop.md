```mermaid


---
title: Online Shop
---
classDiagram
    class Product {
      +String productId
      +String name
      +String description
      +Double price
      +String category
      +displayInfo()
    }

    class Electronics {
      +String manufacturer
      +Int warrantyPeriod
    }

    class Gadget {
      +String gadgetType
      +String connectivity
    }

    class User {
      +String userId
      +String name
      +String email
      +String address
      +register()
      +login()
      +updateProfile()
    }

    class ShoppingCart {
      +List{Product} products
      +Double totalCost
      +addProduct(Product)
      +removeProduct(Product)
      +calculateTotal()
      +checkout()
    }

    class Order {
      +String orderId
      +List{Product} products
      +Double totalCost
      +User userDetails
      +String orderStatus
      +generateOrderDetails()
      +updateOrderStatus()
    }

    class Payment {
      +Double amount
      +String paymentType
      +processPayment()
      +validateTransaction()
      +issueReceipt()
    }

    class Inventory {
      +List{Product} products
      +Map{Product, Int} productQuantities
      +updateInventory()
      +checkAvailability(Product)
    }

    class Review {
      +String reviewId
      +String userId
      +String productId
      +Int rating
      +String comment
      +addReview()
      +displayReviews()
    }

    class Admin {
      +manageProducts()
      +viewOrders()
      +updateInventory()
    }

    Product <|-- Electronics : inherits
    Product <|-- Gadget : inherits
    User <|-- Admin : inherits
    User "1" -- "1" ShoppingCart : has
    User "1" -- "*" Order : places
    User "1" -- "*" Review : writes
    Order "1" -- "*" Product : contains
    Order "1" -- "1" Payment : uses
    Inventory "1" -- "*" Product : stores

classDiagram
    note "Electronics and Gadgest"
    class Category
    <<Abstract>> Category
    Category : string name
    Category : vector< Item>  items_vect

    
    class Item
    Item : #int ID
    Item : #string name
    Item : #float price
    Item : #string manufacturer
    Item : #vector< string> certifications
    Item : #int varanty

    class User
    User : -int ID
    User : -string name
    User : -string email
    User : -string adress
    User: +updateProfile()
    
    class ShoppingCart
    ShoppingCart : vector< Item> cart
    ShoppingCart: addItem()
    ShoppingCart: removeItem()
    ShoppingCart: calculateTotal()
    ShoppingCart: checkout()

    class Order
    Order : -int ID
    Order : -vector~Item~ lst_of_products
    Order : -string status
    Order: getID()
    Order: getStatus()
    Order: updateStatus(status)

    
    Order <-- User
    Order o-- Item
    Admin <|-- User
    class Admin
    


    User o-- ShoppingCart
    ShoppingCart o-- Item

    Electronics<|-- Category
    Electronics o-- Item
    Gadget o-- Item

    Gadget<|-- Category
    Gadget : vector< string> conectivity


```



