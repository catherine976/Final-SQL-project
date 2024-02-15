CREATE DATABASE Online_Retail;
USE Online_Retail;

-- 1. Customers table
CREATE TABLE Customers (
    CustomerID INTEGER NOT NULL,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(50),
    CONSTRAINT PK_Customers PRIMARY KEY (CustomerID));

INSERT INTO Customers
(CustomerID, FirstName, LastName, Email)
VALUES
(1, 'Scott', 'Smith', 'scottsmith@yahoo.com'),
(2, 'Emily', 'Atkins', 'emily_atkins@outlook.com'),
(3, 'Michael', 'Parsons', 'm_parsons94@yahoo.com'),
(4, 'Becky', 'Jones', 'bjones7@gmail.com'),
(5, 'Jim', 'Jackson', 'jim.jackson@gmail.com'),
(6, 'Amy', 'Baker', 'a.baker@yahoo.com'),
(7, 'Sam', 'Gardner', 'sam_gardner@gmail.com'),
(8, 'Olivia', 'Carpenter', 'o.carpenter@outlook.com'),
(9, 'Ben', 'Peabody', 'benpeabody@gmail.com'),
(10, 'Rachel', 'Hopkins', 'r_hopkins@yahoo.com'),
(11, 'Steve', 'Upton', 'supton@gmail.com'),
(12, 'Lewis', 'Thorne', 'lthorne@outlook.com'),
(13, 'Kate', 'Wallace', 'kate.wallace@gmail.com'),
(14, 'Mary', 'Upton', 'm_upton@outlook.com'),
(15, 'Richard', 'Ferguson', 'r.ferguson@gmail.com');

-- 2. Addresses table
CREATE TABLE Addresses (
    AddressID VARCHAR(10) NOT NULL,
    BuildingNumber INTEGER,
    Street VARCHAR(50),
    City VARCHAR(50),
    PostCode VARCHAR(50),
    Country VARCHAR(50),
    CONSTRAINT PK_Addresses PRIMARY KEY (AddressID));

INSERT INTO Addresses
(AddressID, BuildingNumber, Street, City, PostCode, Country)
VALUES
('AD1', 30, 'Green Lane', 'Edinburgh', 'EH48 2BL', 'United Kingdom'),
('AD2', 74, 'Chester Road', 'Stoke-on-Trent', 'ST10 3AE', 'United Kingdom'),
('AD3', 68, 'York Road', 'Watford', 'WD17 2HX', 'United Kingdom'),
('AD4', 24, 'The Drive', 'Taunton', 'TA19 9AP', 'United Kingdom'),
('AD5', 34, 'The Avenue', 'Truro', 'TR11 5HR', 'United Kingdom'),
('AD6', 49, 'Park Road', 'Newcastle upon Tyne', 'NE46 1QB', 'United Kingdom'),
('AD7', 17, 'St Johns Road', 'Salisbury', 'SP2 9JJ', 'United Kingdom'),
('AD8', 60, 'Alexander Road', 'Luton', 'LU6 3PD', 'United Kingdom'),
('AD9', 52, 'Stanley Street', 'Llandrindod Wells', 'LD1 5SN', 'United Kingdom'),
('AD10', 3, 'Mill Lane', 'Halifax', 'HX6 2ED', 'United Kingdom'),
('AD11', 68, 'King Street', 'Rochester', 'ME19 5JU', 'United Kingdom'),
('AD12', 61, 'Manchester Road', 'Bath', 'BA1 1EY', 'United Kingdom'),
('AD13', 2, 'Manor Road', 'Bournemouth', 'BH12 9FT', 'United Kingdom'),
('AD14', 32, 'Victoria Road', 'Brighton', 'BN3 4QD', 'United Kingdom'),
('AD15', 65, 'Queens Road', 'Leicester', 'LE8 9HH', 'United Kingdom');

-- 3. CustomersAddresses table
CREATE TABLE CustomersAddresses (
    CustomerID INTEGER,
    AddressID VARCHAR(10) NOT NULL,
    CONSTRAINT FK_CustomerID FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID),
    CONSTRAINT FK_AddressID FOREIGN KEY (AddressID) REFERENCES Addresses(AddressID)
);

INSERT INTO CustomersAddresses
(CustomerID, AddressID)
VALUES
(1, 'AD15'),
(2, 'AD5'),
(3, 'AD1'),
(4, 'AD14'),
(5, 'AD13'),
(6, 'AD2'),
(7, 'AD8'),
(8, 'AD11'),
(9, 'AD10'),
(10, 'AD4'),
(11, 'AD3'),
(12, 'AD6'),
(13, 'AD7'),
(14, 'AD9'),
(15, 'AD12');

-- 4. Categories table
CREATE TABLE Categories (
    CategoryID VARCHAR(10) NOT NULL, 
    CategoryName VARCHAR(50),
    CONSTRAINT PK_Categories PRIMARY KEY (CategoryID));

INSERT INTO Categories
(CategoryID, CategoryName)
VALUES
('A1', 'Books'), 
('B2', 'Films & TV'),
('C3', 'Electronics & Computers'),
('D4', 'Clothes & Accessories'),
('E5', 'Sports & Outdoors'),
('F6', 'Health & Beauty'),
('G7', 'Home & Garden'),
('H8', 'Pets'),
('I9', 'DIY'),
('J10', 'Gift Cards');

-- 5. Couriers table
CREATE TABLE Couriers (
    CourierID VARCHAR(10) NOT NULL, 
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    NumberPlate VARCHAR(50),
    PhoneNumber VARCHAR(50),
    CONSTRAINT PK_Couriers PRIMARY KEY (CourierID));

INSERT INTO Couriers
(CourierID, FirstName, LastName, NumberPlate, PhoneNumber)
VALUES
('COR1', 'Sharon', 'Chapman', 'YX04HCG', '+44-4134-319-535'),
('COR2', 'Eliza', 'Fletcher', 'VC07ZKF', '+44-1511-814-740'),
('COR3', 'Ben', 'Davies', 'RU10WXR', '+44-6287-749-734'),
('COR4', 'Rebecca', 'Edwards', 'HK07RHI', '+44-4531-414-948'),
('COR5', 'John', 'Fisher', 'YV51CKJ', '+44-7134-216-194'),
('COR6', 'Tim', 'Gibson', 'PN20HNG', '+44-8127-899-727'),
('COR7', 'Dennis', 'Allen', 'WX66SXO', '+44-3320-022-286'),
('COR8', 'Danny', 'Bailey', 'RY04QEL', '+44-5202-014-477'),
('COR9', 'Ian', 'Hall', 'BX03EDD', '+44-6128-382-406'),
('COR10', 'Charles', 'Bates', 'EO03WYM', '+44-1165-610-910'),
('COR11', 'Amy', 'Elliott', 'VP19BUC', '+44-1050-361-578'),
('COR12', 'David', 'Armstrong', 'WX66GXE', '+44-1211-954-835'),
('COR13', 'Peter', 'Campbell', 'SX07YXA', '+44-3987-815-647'),
('COR14', 'Jim', 'Davidson', 'SN22WWV', '+44-6993-964-475'),
('COR15', 'Paul', 'Williams', 'MR06BFZ', '+44-2077-325-302');

-- 6. Orders table
CREATE TABLE Orders (
    OrderID VARCHAR(10) NOT NULL,
    CustomerID INTEGER,
    OrderDate DATE,
    Status VARCHAR(50),
    PRIMARY KEY (OrderID),
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

INSERT INTO Orders
(OrderID, CustomerID, OrderDate, Status)
VALUES
('ORD001', 1, '2023-12-15', 'Processing'),
('ORD002', 3, '2023-11-02', 'Shipped'),
('ORD003', 5, '2023-03-10', 'Delivered'),
('ORD004', 7, '2023-11-22', 'Processing'),
('ORD005', 9, '2023-11-05', 'Shipped'),
('ORD006', 11, '2023-06-18', 'Delivered'),
('ORD007', 13, '2023-07-03', 'Processing'),
('ORD008', 15, '2023-08-14', 'Shipped'),
('ORD009', 2, '2023-09-30', 'Delivered'),
('ORD010', 4, '2023-10-12', 'Processing'),
('ORD011', 6, '2023-11-25', 'Shipped'),
('ORD012', 8, '2023-12-01', 'Delivered'),
('ORD013', 10, '2023-12-17', 'Processing'),
('ORD014', 12, '2023-12-14', 'Shipped'),
('ORD015', 14, '2023-03-22', 'Delivered'),
('ORD016', 10, '2023-12-16', 'Shipped');

-- 7. Products table
CREATE TABLE Products (
    ProductID VARCHAR(10) NOT NULL,
    ProductName VARCHAR(255),
    Price DECIMAL(10, 2),
    CategoryID VARCHAR(10), 
    PRIMARY KEY (ProductID),
    FOREIGN KEY (CategoryID) REFERENCES Categories(CategoryID)
);

INSERT INTO Products
(ProductID, ProductName, Price, CategoryID)
VALUES
('PROD001', 'Laptop', 899.99, 'C3'),
('PROD002', 'Smartphone', 499.99, 'C3'),
('PROD003', 'Dress', 59.99, 'D4'),
('PROD004', 'Running Shoes', 79.99, 'E5'),
('PROD005', 'Headphones', 129.99, 'C3'),
('PROD006', 'Coffee Maker', 49.99, 'G7'),
('PROD007', 'Fitness Tracker', 79.99, 'E5'),
('PROD008', 'Novel', 14.99, 'A1'),
('PROD009', 'Blender', 39.99, 'G7'),
('PROD010', 'Sunglasses', 29.99, 'D4'),
('PROD011', 'Gardening Kit', 44.99, 'G7'),
('PROD012', 'Watch', 119.99, 'D4'),
('PROD013', 'Backpack', 34.99, 'D4'),
('PROD014', 'Yoga Mat', 24.99, 'E5'),
('PROD015', 'Camera', 299.99, 'C3');

-- 8. OrderDetails table
CREATE TABLE OrderDetails (
    OrderDetailID VARCHAR(10) NOT NULL,
    OrderID VARCHAR(10),
    ProductID VARCHAR(10),
    Quantity INTEGER,
    TotalPrice DECIMAL(10, 2),
    PRIMARY KEY (OrderDetailID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
);

INSERT INTO OrderDetails
(OrderDetailID, OrderID, ProductID, Quantity, TotalPrice)
VALUES
('OD001', 'ORD001', 'PROD002', 1, 499.99),
('OD002', 'ORD001', 'PROD005', 2, 259.98),
('OD003', 'ORD002', 'PROD008', 3, 44.97),
('OD004', 'ORD002', 'PROD010', 1, 29.99),
('OD005', 'ORD003', 'PROD003', 2, 119.98),
('OD006', 'ORD003', 'PROD006', 1, 49.99),
('OD007', 'ORD004', 'PROD001', 1, 899.99),
('OD008', 'ORD004', 'PROD004', 1, 79.99),
('OD009', 'ORD005', 'PROD014', 2, 49.98),
('OD010', 'ORD005', 'PROD007', 1, 79.99),
('OD011', 'ORD006', 'PROD012', 1, 119.99),
('OD012', 'ORD006', 'PROD015', 1, 299.99),
('OD013', 'ORD007', 'PROD009', 3, 119.97),
('OD014', 'ORD007', 'PROD011', 1, 44.99),
('OD015', 'ORD008', 'PROD013', 2, 69.98),
('OD016', 'ORD008', 'PROD006', 2, 99.98),
('OD017', 'ORD009', 'PROD003', 1, 59.99),
('OD018', 'ORD010', 'PROD014', 3, 74.97),
('OD019', 'ORD011', 'PROD011', 2, 89.98),
('OD020', 'ORD012', 'PROD001', 1, 899.99),
('OD021', 'ORD013', 'PROD005', 2, 259.98),
('OD022', 'ORD014', 'PROD009', 1, 39.99),
('OD023', 'ORD015', 'PROD012', 1, 119.99),
('OD024', 'ORD016', 'PROD002', 1, 499.99);

-- 9. PaymentMethods table
CREATE TABLE PaymentMethods (
    PaymentMethodID VARCHAR(10) NOT NULL,
    MethodName VARCHAR(255),
    PRIMARY KEY (PaymentMethodID)
);

INSERT INTO PaymentMethods
(PaymentMethodID, MethodName)
VALUES
('PAY001', 'Credit Card'),
('PAY002', 'PayPal'),
('PAY003', 'Bank Transfer'),
('PAY004', 'Cash on Delivery');

-- 10. Payments table
CREATE TABLE Payments (
    PaymentID VARCHAR(10) NOT NULL,
    OrderID VARCHAR(10),
    Amount DECIMAL(10, 2),
    PaymentDate DATETIME NOT NULL,
    PaymentMethodID VARCHAR(10),
    PRIMARY KEY (PaymentID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (PaymentMethodID) REFERENCES PaymentMethods(PaymentMethodID)
);
-- 11. Insert data into Payments table
INSERT INTO Payments
(PaymentID, OrderID, Amount, PaymentDate, PaymentMethodID)
VALUES
('PAY001', 'ORD001', 759.97, '2023-12-15', 'PAY001'),
('PAY002', 'ORD002', 74.96, '2023-11-02', 'PAY002'),
('PAY003', 'ORD003', 169.97, '2023-03-10', 'PAY003'),
('PAY004', 'ORD004', 979.98, '2023-11-22', 'PAY001'),
('PAY005', 'ORD005', 129.97, '2023-11-05', 'PAY002'),
('PAY006', 'ORD006', 419.98, '2023-06-18', 'PAY003'),
('PAY007', 'ORD007', 164.96, '2023-07-03', 'PAY001'),
('PAY008', 'ORD008', 169.96, '2023-08-14', 'PAY002'),
('PAY009', 'ORD009', 59.99, '2023-09-30', 'PAY004'),
('PAY010', 'ORD010', 74.97, '2023-10-12', 'PAY001'),
('PAY011', 'ORD011', 89.98, '2023-11-25', 'PAY002'),
('PAY012', 'ORD012', 899.99, '2023-12-01', 'PAY003'),
('PAY013', 'ORD013', 259.98, '2023-12-17', 'PAY001'),
('PAY014', 'ORD014', 39.99, '2023-12-14', 'PAY002'),
('PAY015', 'ORD015', 119.99, '2023-03-22', 'PAY003'),
('PAY016', 'ORD016', 499.99, '2023-12-16', 'PAY002');
