---
title: "Entity SQL 快速參考 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Entity SQL 快速參考
本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。  本主題的範例是以 AdventureWorks Sales Model 為基礎。  
  
## 常值  
  
### String  
 字串常值包括 Unicode 和非 Unicode 字元兩種。  Unicode 字串前面會加一個 N，  例如，`N'hello'`。  
  
 以下是非 Unicode 字串常值的範例：  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 輸出：  
  
|值|  
|-------|  
|hello|  
  
### DateTime  
 在 DateTime 常值中，日期和時間兩者都是必要項。  沒有預設值。  
  
 範例：  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 輸出：  
  
|值|  
|-------|  
|12\/25\/2006 1:01:00 AM|  
  
### Integer  
 整數常值可以屬於型別 Int32 \(123\)、UInt32 \(123U\)、Int64 \(123L\) 和 UInt64 \(123UL\)。  
  
 範例：  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 輸出：  
  
|值|  
|-------|  
|1|  
|2|  
|3|  
  
### 其他  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援的其他常值包括 Guid、二進位、浮點數\/雙精度浮點數、十進位和 `null`。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的 Null 常值視為與概念模型的每一種其他型別相容。  
  
## 型別建構函式  
  
### ROW  
 [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) 會建構匿名、結構式型別 \(記錄\) 值，例如：`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 範例：  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 輸出：  
  
|ProductID|名稱|  
|---------------|--------|  
|1|Adjustable Race|  
|879|All\-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) 會建構集合，例如：  
  
 `MULTISET(1,2,2,3)` `--same as`\-`{1,2,2,3}.`  
  
 範例：  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 輸出：  
  
|ProductID|名稱|ProductNumber|…|  
|---------------|--------|-------------------|-------|  
|842|Touring\-Panniers, Large|PA\-T100|…|  
  
### 物件  
 [具名類型建構函式](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) 會建構 \(具名\) 使用者定義物件，例如 `person("abc", 12)`。  
  
 範例：  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 輸出：  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911\-403C\-98|1|776|...|  
|2|4911\-403C\-98|3|777|...|  
|...|...|...|...|...|  
  
## 參考  
  
### REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) 會建立實體類型執行個體的參考。  例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 輸出：  
  
|值|  
|-------|  
|1|  
|2|  
|3|  
|...|  
  
 以下範例使用屬性引出運算子 \(.\) 來存取實體的屬性。  使用屬性引出運算子時，參考會自動取值。  
  
 範例：  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 輸出：  
  
|值|  
|-------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) 會對參考值取值並且產生該取值的結果。  例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。  
  
 範例：  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 輸出：  
  
|值|  
|-------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### CREATEREF 和 KEY  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) 會建立傳遞索引鍵的參考。  [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) 會擷取具有型別參考之運算式的索引鍵部分。  
  
 範例：  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 輸出：  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## 函式  
  
### 標準  
 [標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)的命名空間為 Edm，例如 `Edm.Length("string")`。  除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。  如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。  
  
 範例：  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 輸出：  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### Microsoft 提供者專用  
 [Microsoft 提供者專用函式](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)是在 `SqlServer` 命名空間中。  
  
 範例：  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 輸出：  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## 命名空間  
 [USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) 會指定查詢運算式中使用的命名空間。  
  
 範例：  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 輸出：  
  
|值|  
|-------|  
|aa|  
  
## 分頁  
 分頁可以利用宣告 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) 和 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) 次子句到 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) 子句的方式表示。  
  
 範例：  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 輸出：  
  
|ID|名稱|  
|--------|--------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## 群組  
 [GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) 指定要放置查詢 \([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)\) 運算式所傳回物件的群組。  
  
 範例：  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 輸出：  
  
|name|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## 巡覽  
 關聯性巡覽運算子可以讓您在關聯性上從一個實體 \(開始端\) 巡覽到另一個實體 \(結束端\)。  [NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) 接受限定為 \<namespace\>.\<relationship type name\> 的關係類型。  如果結束端的基數為 1，巡覽會傳回 Ref\<T\>。  如果結束端的基數為 n，將傳回 Collection\<Ref\<T\>\>。  
  
 範例：  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 輸出：  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## SELECT VALUE 和 SELECT  
  
### SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供 SELECT VALUE 子句來略過隱含資料列建構。  SELECT VALUE 子句中可指定一個項目。  使用這類子句時，將不會建構包含 SELECT 子句中這個項目的資料列包裝函式，並且可以產生所需形狀的集合，例如：`SELECT VALUE a`。  
  
 範例：  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 輸出：  
  
|名稱|  
|--------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也提供資料列建構函式來建構任意資料列。  SELECT 會擷取投影中的一個或多個項目，並且產生具有欄位的資料記錄，例如：`SELECT a, b, c`。  
  
 範例：  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|名稱|ProductID|  
|--------|---------------|  
|Adjustable Race|1|  
|All\-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## CASE 運算式  
 [CASE 運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)會評估一組布林運算式來判斷結果。  
  
 範例：  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 輸出：  
  
|值|  
|-------|  
|TRUE|  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)