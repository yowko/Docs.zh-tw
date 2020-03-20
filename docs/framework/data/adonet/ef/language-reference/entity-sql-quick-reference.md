---
title: Entity SQL 快速參考
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: fc7cf8f8f692f9dc4230569d5f575b6d5fad19fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150346"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL 快速參考
本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。 本主題的範例是以 AdventureWorks Sales Model 為基礎。  
  
## <a name="literals"></a>常值  
  
### <a name="string"></a>String  
 字串常值包括 Unicode 和非 Unicode 字元兩種。 Unicode 字串用 N 預寫。例如， `N'hello'`.  
  
 以下是非 Unicode 字串常值的範例：  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 輸出：  
  
|值|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>Datetime  
 在 DateTime 常值中，日期和時間兩者都是必要項。 沒有預設值。  
  
 範例：  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 輸出：  
  
|值|  
|-----------|  
|12/25/2006 1:01:00 AM|  
  
### <a name="integer"></a>整數   
 整數常值可以屬於型別 Int32 (123)、UInt32 (123U)、Int64 (123L) 和 UInt64 (123UL)。  
  
 範例：  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 輸出：  
  
|值|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>其他  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援的其他常值包括 Guid、二進位、浮點數/雙精度浮點數、十進位和 `null`。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的 Null 常值視為與概念模型的每一種其他型別相容。  
  
## <a name="type-constructors"></a>型別建構函式  
  
### <a name="row"></a>ROW  
 [ROW](row-entity-sql.md)構造一個匿名的、結構類型（記錄）值，如：`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 範例：  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 輸出：  
  
|ProductID|名稱|  
|---------------|----------|  
|1|Adjustable Race|  
|879|All-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](multiset-entity-sql.md)構造集合，例如：  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 範例：  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 輸出：  
  
|ProductID|名稱|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Object  
 [命名類型建構函式](named-type-constructor-entity-sql.md)構造（命名）使用者定義物件，如`person("abc", 12)`。  
  
 範例：  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 輸出：  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>參考  
  
### <a name="ref"></a>REF  
 [REF](ref-entity-sql.md)創建對實體類型實例的引用。 例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 輸出：  
  
|值|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 以下範例使用屬性引出運算子 (.) 來存取實體的屬性。 使用屬性引出運算子時，參考會自動取值。  
  
 範例：  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 輸出：  
  
|值|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md)取消引用值並生成該取消引用的結果。 例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。  
  
 範例：  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 輸出：  
  
|值|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF 和 KEY  
 [CREATEREF](createref-entity-sql.md)創建傳遞金鑰的引用。 [KEY](key-entity-sql.md)使用類型引用提取運算式的鍵部分。  
  
 範例：  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 輸出：  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>函式  
  
### <a name="canonical"></a>Canonical  
 [規範函數](canonical-functions.md)的命名空間是 Edm，如 中`Edm.Length("string")`。 除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。 如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。  
  
 範例：  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 輸出：  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Microsoft 提供者專用  
 [特定于 Microsoft 提供程式的函數](../sqlclient-for-ef-functions.md)位於`SqlServer`命名空間中。  
  
 範例：  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 輸出：  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>命名空間  
 [USING](using-entity-sql.md)指定查詢運算式中使用的命名空間。  
  
 範例：  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 輸出：  
  
|值|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Paging  
 可以通過向[ORDER BY](order-by-entity-sql.md)子句聲明[SKIP](skip-entity-sql.md)和[LIMIT](limit-entity-sql.md)子子子子子子子子句來表示分頁。  
  
 範例：  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 輸出：  
  
|ID|名稱|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>分組  
 [GROUPING BY](group-by-entity-sql.md)指定要將查詢 （[SELECT](select-entity-sql.md)） 運算式返回的物件放入其中的組。  
  
 範例：  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 輸出：  
  
|NAME|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## <a name="navigation"></a>導覽  
 關聯性巡覽運算子可以讓您在關聯性上從一個實體 (開始端) 巡覽到另一個實體 (結束端)。 [NAVIGATE](navigate-entity-sql.md)將限定為\<命名空間>的關聯類型。\<關聯類型名稱>。 如果結尾的\<基數為 1，則導航返回參考 T>。 如果到末尾的基數為 n，則將返回"收集<\<參考 T>> 。  
  
 範例：  
  
```sql  
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
  
## <a name="select-value-and-select"></a>SELECT VALUE 和 SELECT  
  
### <a name="select-value"></a>SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供 SELECT VALUE 子句來略過隱含資料列建構。 SELECT VALUE 子句中可指定一個項目。 使用此類子句時，不會圍繞 SELECT 子句中的項構造行包裝器，並且可以生成所需形狀的集合，例如： `SELECT VALUE a`。  
  
 範例：  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 輸出：  
  
|名稱|  
|----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也提供資料列建構函式來建構任意資料列。 SELECT 會擷取投影中的一個或多個項目，並且產生具有欄位的資料記錄，例如：`SELECT a, b, c`。  
  
 範例：  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|名稱|ProductID|  
|----------|---------------|  
|Adjustable Race|1|  
|All-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## <a name="case-expression"></a>CASE 運算式  
 [大小寫運算式](case-entity-sql.md)計算一組布林運算式以確定結果。  
  
 範例：  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 輸出：  
  
|值|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [Entity SQL 概觀](entity-sql-overview.md)
