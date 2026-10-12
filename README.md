# AquaLife Billing System

A comprehensive inventory management and billing solution designed specifically for aquatic fish stores. Built with **Java** and **MySQL**, AquaLife Billing System helps store owners efficiently manage products, process sales, and generate printable bills for customers.

---

## Overview

AquaLife Billing System is a Point of Sale (POS) and inventory management application for aquarium and fish retail businesses. It provides administrators with a dashboard to manage product categories such as ornamental fishes, fish food, tanks, and accessories. The system supports barcode-based product lookup and generates customer bills automatically based on selected items, quantities, and prices.

---

## Features

- **Product Management by Category**
  - Ornamental Fishes
  - Fish Food
  - Tanks
  - Accessories

- **Inventory Tracking & Management**
  - Real-time stock updates
  - Product availability tracking
  - Stock level management

- **Barcode Support**
  - Generate and assign barcodes to products
  - Quick product identification via barcode scanning

- **Advanced Product Search**
  - Search by product name
  - Search by price
  - Search by barcode

- **Admin Dashboard**
  - Centralized sales and inventory operations
  - Easy product management
  - Stock monitoring

- **Billing System**
  - Automatic bill generation
  - Quantity-based total calculation
  - Printable customer bills
  - Professional invoice formatting

---

## Technology Stack

- **Language**: Java
- **Database**: MySQL
- **IDE**: NetBeans (recommended version 8.1+)
- **Database Connectivity**: JDBC
- **Build Tool**: Maven or Gradle (optional)

---

## Problem Statement

Aquatic fish stores often manage products manually, which can lead to:

- Inventory errors and discrepancies
- Difficulty searching for products across categories
- Slow and error-prone billing operations
- Inaccurate or inconsistent pricing
- Poor stock visibility and management

AquaLife Billing System addresses these challenges by offering a centralized digital solution for inventory and sales management.

---

## Objectives

- Simplify product categorization and management
- Maintain accurate stock records in real-time
- Generate bills quickly and accurately
- Improve customer checkout efficiency
- Organize products by category for easy navigation
- Provide fast barcode-based product lookup
- Reduce manual data entry errors

---

## Prerequisites

Before running the project, ensure you have the following installed:

- **Java Development Kit (JDK)** 8 or later
- **MySQL Server** 5.7 or higher
- **NetBeans IDE** 8.1+ (recommended) or any Java IDE
- **MySQL Workbench** or command-line MySQL client
- **JDBC Driver** for MySQL

---

## Installation & Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/adityawaghmare19/aqualifebilling.git
cd aqualifebilling
```

### Step 2: Create the Database

```sql
CREATE DATABASE aqualifebilling;
```

### Step 3: Configure Database Connection

Update your database configuration with the following details:

- **Database Name**: aqualifebilling
- **Host**: localhost
- **Port**: 3306
- **Username**: root (or your MySQL username)
- **Password**: your_password

### Step 4: Import Database Schema

If a schema file is provided, import it:

```bash
mysql -u root -p aqualifebilling < database/schema.sql
```

### Step 5: Open Project in NetBeans

1. Open NetBeans IDE
2. Click **File** → **Open Project**
3. Navigate to the `aqualifebilling` folder
4. Click **Open Project**

### Step 6: Run the Application

- Right-click the project and select **Run**
- Or press `F6` to execute

---

## Project Workflow

1. **Admin Login**: Administrator logs into the dashboard
2. **Add Products**: Add products under specific categories with details
3. **Assign Barcode**: Each product is assigned a unique barcode
4. **Search Products**: Retrieve products by name, barcode, or price
5. **Create Bill**: Select products and enter quantities
6. **Auto Calculate**: System calculates the total automatically
7. **Generate & Print Bill**: Create and print a professional bill for the customer

---

## Product Categories

- Ornamental Fishes
- Fish Food
- Tanks
- Accessories

---

## Billing Process

The billing module calculates the total customer amount using:

- **Selected Products**: List of items purchased
- **Quantity**: Quantity of each product
- **Unit Price**: Individual product price
- **Total Amount**: Auto-calculated final amount

The generated bill includes:

- Customer details
- Bill number and date
- Itemized product list with prices
- Subtotal and total amount
- Professional formatting for printing

---

## Search Functionality

The system supports searching products using:

- **Product Name**: Find products by their name
- **Price**: Filter products by price range
- **Barcode**: Quick lookup using barcode scanning

This helps reduce search time and improves operational efficiency.

---

## Suggested Database Schema

### Products Table

```sql
CREATE TABLE products (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    category VARCHAR(100) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    quantity INT NOT NULL,
    barcode VARCHAR(255) UNIQUE,
    description VARCHAR(500),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

### Bills Table

```sql
CREATE TABLE bills (
    id INT PRIMARY KEY AUTO_INCREMENT,
    bill_number VARCHAR(100) UNIQUE NOT NULL,
    total_amount DECIMAL(10, 2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Bill Items Table

```sql
CREATE TABLE bill_items (
    id INT PRIMARY KEY AUTO_INCREMENT,
    bill_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL,
    unit_price DECIMAL(10, 2) NOT NULL,
    total_price DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (bill_id) REFERENCES bills(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

---

## Project Structure

```
aqualifebilling/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── controller/       # UI Controllers
│   │   │   ├── model/            # Data Models
│   │   │   ├── service/          # Business Logic
│   │   │   ├── dao/              # Database Access
│   │   │   └── util/             # Utility Classes
│   │   └── resources/
│   └── test/
├── database/
│   └── schema.sql
├── README.md
├── LICENSE
└── .gitignore
```

---

## Future Enhancements

- [ ] User authentication and role-based access control
- [ ] Customer database and purchase history
- [ ] Sales analytics and reporting
- [ ] Low-stock alert notifications
- [ ] Supplier management module
- [ ] Barcode generation feature
- [ ] Export bills to PDF
- [ ] Email receipt functionality
- [ ] Payment gateway integration
- [ ] Mobile app version
- [ ] Multi-location support
- [ ] Advanced inventory forecasting

---

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## Troubleshooting

### Database Connection Issues

- Verify MySQL Server is running
- Check database credentials in the configuration file
- Ensure the JDBC MySQL driver is in the classpath

### Application Won't Start

- Verify all prerequisites are installed
- Check Java version compatibility
- Review console error messages for detailed diagnostics

---

## License

This project is provided for educational and commercial use. For license details, see the LICENSE file.

---

## Support & Contact

For questions, bug reports, or feature requests, please:

- Open an issue on the GitHub repository
- Contact the project maintainer
- Check existing issues for solutions

---

## Acknowledgments

Built for aquatic fish store businesses to streamline operations and improve customer experience.

---

**Made with ❤️ for aquatic store management**

**Last Updated**: 2026  
**Status**: Active Development
