-- Core Requirements:

-- 1. Using any type of joins, create a view that combines multiple tables in a logical way

CREATE VIEW CombinedData AS
SELECT
    O.OrderID,
    O.OrderDate,
    O.Status,
    C.CustomerID,
    C.FirstName,
    C.LastName,
    P.ProductID,
    P.ProductName,
    OD.Quantity,
    OD.TotalPrice,
    PM.MethodName AS PaymentMethod
FROM
    Orders O
INNER JOIN Customers C ON O.CustomerID = C.CustomerID
LEFT JOIN OrderDetails OD ON O.OrderID = OD.OrderID
LEFT JOIN Products P ON OD.ProductID = P.ProductID
LEFT JOIN Payments PA ON O.OrderID = PA.OrderID
LEFT JOIN PaymentMethods PM ON PA.PaymentMethodID = PM.PaymentMethodID;

-- Query the CombinedData view
SELECT * FROM CombinedData;

-- 2. Create a stored function that calculates the total price for a given quantity and product price:

DELIMITER //

CREATE FUNCTION CalculateTotalPrice(quantity INT, productPrice DECIMAL(10, 2))
RETURNS DECIMAL(10, 2)
DETERMINISTIC
BEGIN
    DECLARE total DECIMAL(10, 2);
    SET total = quantity * productPrice;
    RETURN total;
END //

DELIMITER ;

-- Example query using the stored function
SELECT
    OD.OrderID,
    OD.ProductID,
    OD.Quantity,
    P.Price,
    CalculateTotalPrice(OD.Quantity, P.Price) AS TotalPrice
FROM
    OrderDetails OD
JOIN
    Products P ON OD.ProductID = P.ProductID;
    
-- 3. Prepare an example query with a subquery to demonstrate how to extract data from your DB for analysis 

SELECT
    O.OrderID,
    O.OrderDate,
    O.Status,
    C.CustomerID,
    C.FirstName,
    C.LastName,
    (
        SELECT COUNT(OD.ProductID)
        FROM OrderDetails OD
        WHERE OD.OrderID = O.OrderID
    ) AS TotalProductsOrdered
FROM
    Orders O
JOIN
    Customers C ON O.CustomerID = C.CustomerID
ORDER BY
    CustomerID DESC;
    
    -- ADVANCED REQUIREMENTS:
-- 1. In your database, create a stored procedure and demonstrate how it runs:

-- Option 1: Create a stored procedure retrieves information about a specific customer based on their ID
DELIMITER //

CREATE PROCEDURE GetCustomerInfo(IN p_CustomerID INT)
BEGIN
    SELECT
        CustomerID,
        FirstName,
        LastName,
        Email
    FROM
        Customers
    WHERE
        CustomerID = p_CustomerID;
END //

DELIMITER ;

-- Call the stored procedure
CALL GetCustomerInfo(3);

-- Option 2: Get a list of products with the highest total sales:
DELIMITER //
CREATE PROCEDURE GetTopSellingProducts(IN topCount INT)
BEGIN
    SELECT 
        p.ProductID,
        p.ProductName,
        SUM(od.Quantity) AS TotalSales
    FROM Products p
    INNER JOIN OrderDetails od ON p.ProductID = od.ProductID
    GROUP BY p.ProductID
    ORDER BY TotalSales DESC
    LIMIT topCount;
END //DELIMITER ;

-- To execute this stored procedure:
CALL GetTopSellingProducts(5);

-- 2. In your database, create a trigger and demonstrate how it runs:

-- Trigger that automatically updates the order status to 'Shipped' when a payment is made
DELIMITER //
CREATE TRIGGER UpdateOrderStatus
AFTER INSERT ON Payments
FOR EACH ROW
BEGIN
    DECLARE orderStatus VARCHAR(50);
    
    -- Retrieve the order status
    SELECT Status INTO orderStatus
    FROM Orders
    WHERE OrderID = NEW.OrderID;
    
    -- Update the order status to 'Shipped' if not already shipped
    IF orderStatus <> 'Shipped' THEN
        UPDATE Orders
        SET Status = 'Shipped'
        WHERE OrderID = NEW.OrderID;
    END IF;
END;
//
DELIMITER ;

-- Insert a new payment
INSERT INTO Payments (PaymentID, OrderID, Amount, PaymentDate, PaymentMethodID)
VALUES ('PAY017', 'ORD007', 99.99, '2023-12-18', 'PAY001');

-- Check the updated order status
SELECT * FROM Orders WHERE OrderID = 'ORD007';

-- 3. In your database, create an event and demonstrate how it runs.

-- Option 1: Create an event that updates the status of orders from "Processing" to "Delayed" if the order date is more than 30 days ago.

DELIMITER //

CREATE EVENT UpdateDelayedOrders
ON SCHEDULE EVERY 1 DAY
DO
BEGIN
    UPDATE Orders
    SET Status = 'Delayed'
    WHERE Status = 'Processing' AND OrderDate < DATE_SUB(NOW(), INTERVAL 30 DAY);
END //

DELIMITER ;
-- Insert a new order that is more than 30 days old
INSERT INTO Orders (OrderID, CustomerID, OrderDate, Status)
VALUES ('ORD018', 5, '2023-11-01', 'Processing');


select * from orders;

-- Option 2:
-- This event archives the data from the orders table when it is 6 months after the order date.

CREATE TABLE orders_archive (
	OrderID VARCHAR(10) NOT NULL,
    CustomerID INTEGER,
    OrderDate DATE,
    Status VARCHAR(50));

SET GLOBAL event_scheduler = ON;

DELIMITER //

CREATE EVENT archive_orders
ON SCHEDULE AT NOW() + INTERVAL 1 MINUTE
	DO BEGIN 
    INSERT INTO orders_archive (OrderID, CustomerID, OrderDate, Status) SELECT OrderID, CustomerID, OrderDate, Status from orders
	WHERE (DATEDIFF(CURRENT_DATE(), OrderDate) > 183);
    
    END//

DELIMITER ;

-- 4. Create a  view that uses at least 3-4 base tables; Prepare and demonstrate a query that uses the view to produce a logically arranged result set for analysis

-- Combine Order, Product, and Payment information using LEFT JOIN:
CREATE VIEW OrderProductPaymentView AS
SELECT 
    o.OrderID,
    o.OrderDate,
    p.ProductID,
    p.ProductName,
    od.Quantity,
    od.TotalPrice,
    pm.MethodName,
    py.Amount,
    py.PaymentDate
FROM Orders o
INNER JOIN OrderDetails od ON o.OrderID = od.OrderID
INNER JOIN Products p ON od.ProductID = p.ProductID
LEFT JOIN Payments py ON o.OrderID = py.OrderID
LEFT JOIN PaymentMethods pm ON py.PaymentMethodID = pm.PaymentMethodID;


-- 5. Prepare an example query with group by and having to demonstrate how to extract data from your database for analysis.
-- This query shows the number of transactions using each payment method that is used at least once.
SELECT
p.PaymentMethodID,
(SELECT MethodName FROM paymentmethods pm WHERE pm.PaymentMethodID = p.PaymentMethodID) AS PaymentMethodName,
COUNT(p.PaymentMethodID) AS number_of_transactions
FROM payments AS p
GROUP BY p.PaymentMethodID
HAVING COUNT(p.PaymentMethodID) >=1;
