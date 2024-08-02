# 1. - Table : OrderDetails
### - 조건 : 제품명,가격, 주문 갯수, 고객명 표시
```
SELECT p.ProductName as "제품명", p.Price as "가격", od.Quantity as "주문 갯수", c.CustomerName as "고객명"
FROM ( (OrderDetails od
INNER JOIN Products p ON od.ProductID = p.ProductID)
INNER JOIN Orders o ON od.OrderID = o.OrderID)
INNER JOIN Customers c ON o.CustomerID = c.CustomerID;

```
![sql01](https://github.com/user-attachments/assets/be636579-db6a-4130-aab9-f0b054ae2b04)

---
# 2. - Table : Orders
### - 조건 : 가장 많이 주문 받은 회사 직원명과 갯수
```
SELECT TOP 1 EmployeeID, COUNT(*) AS order_count 
FROM Orders 
group by employeeId
order by COUNT(*) DESC;

```
![sql02](https://github.com/user-attachments/assets/b3ce56fe-ed0c-4161-8db5-e3ecbd8537c8)

---
# 3. - Table : Customers, Orders
### - 조건 : CustomerName별로 주문 갯수 표시
```
SELECT CustomerName, COUNT(*) as "주문 개수"
FROM Customers
LEFT join Orders on Customers.CustomerID = Orders.CustomerID
group by CustomerName

```
![sql03](https://github.com/user-attachments/assets/95672f13-ffaa-4277-9c82-2a6a99d05c69)

---
# 4. - Table : Products
### - 조건 : CategoryID 가 10개 이상
```
SELECT CategoryID, COUNT(*) as "개수"
FROM Products
GROUP BY CategoryID
HAVING COUNT(*) >= 10;

```
![sql04](https://github.com/user-attachments/assets/d5112189-e474-450a-9151-2d24cb66de90)

---
# 5. - Table : Products
### - 조건 : CategoryName가 Produce, Beverages 제품에 갯수 각각 표시
```
SELECT CategoryName, COUNT(*) AS "갯수"
FROM Products p
INNER JOIN Categories c ON p.CategoryID = c.CategoryID
WHERE p.CategoryID IN (1, 7)
GROUP BY CategoryName;

```
![sql05](https://github.com/user-attachments/assets/b8746f60-bc41-41f1-a7c2-02219ecad686)





