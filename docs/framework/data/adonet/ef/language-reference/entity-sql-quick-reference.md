---
title: Entity SQL 快速參考
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7780359d981b130118cb73d4892f3dcb4b6e2e7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251033"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL 快速參考
本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。 本主題中的查詢是以 AdventureWorks Sales model 為基礎。  
  
## <a name="literals"></a>常值  
  
### <a name="string"></a>String  
 字串常值包括 Unicode 和非 Unicode 字元兩種。 Unicode 字串前面會加上 N。例如， `N'hello'`。  
  
 以下是非 Unicode 字串常值的範例：  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 輸出：  
  
|值|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 在 DateTime 常值中，日期和時間兩者都是必要項。 沒有預設值。  
  
 範例：  
  
```  
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
  
```  
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
 資料[列](row-entity-sql.md)會將匿名的結構化型別（記錄）值結構化為：`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 範例：  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 輸出：  
  
|ProductID|名稱|  
|---------------|----------|  
|1|Adjustable Race|  
|879|All-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [多重集](multiset-entity-sql.md)會結構集合，例如：  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 範例：  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 輸出：  
  
|ProductID|名稱|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Object  
 [命名類型](named-type-constructor-entity-sql.md)的函式結構（名為）使用者定義物件， `person("abc", 12)`例如。  
  
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
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>參考  
  
### <a name="ref"></a>REF  
 [REF](ref-entity-sql.md)會建立實體類型實例的參考。 例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：  
  
```  
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
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 輸出：  
  
|值|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md)會對參考值取值，並產生該取值的結果。 例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。  
  
 範例：  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 輸出：  
  
|值|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF 和 KEY  
 [CREATEREF](createref-entity-sql.md)會建立傳遞金鑰的參考。 [Key](key-entity-sql.md)會使用型別參考來解壓縮運算式的索引鍵部分。  
  
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
  
## <a name="functions"></a>Functions  
  
### <a name="canonical"></a>Canonical  
 [標準](canonical-functions.md)函式的命名空間是 Edm，如`Edm.Length("string")`中所示。 除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。 如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。  
  
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
  
### <a name="microsoft-provider-specific"></a>Microsoft 提供者專用  
 [Microsoft 提供者特有](../sqlclient-for-ef-functions.md)的`SqlServer`函式是在命名空間中。  
  
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
  
## <a name="namespaces"></a>命名空間  
 [使用](using-entity-sql.md)指定查詢運算式中使用的命名空間。  
  
 範例：  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 輸出：  
  
|值|  
|-----------|  
|aa|  
  
## <a name="paging"></a>分頁  
 分頁可以藉由將[SKIP](skip-entity-sql.md)和[LIMIT](limit-entity-sql.md)子子句宣告為[ORDER by](order-by-entity-sql.md)子句來表示。  
  
 範例：  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 輸出：  
  
|id|名稱|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>群組  
 [分組方式](group-by-entity-sql.md)指定要放置查詢（[SELECT](select-entity-sql.md)）運算式所傳回物件的群組。  
  
 範例：  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 輸出：  
  
|NAME|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## <a name="navigation"></a>巡覽  
 關聯性巡覽運算子可以讓您在關聯性上從一個實體 (開始端) 巡覽到另一個實體 (結束端)。 [導覽](navigate-entity-sql.md)會採用限定為\<命名空間 > 的關聯性類型。\<關聯性類型名稱 >。 如果要結束\<的基數為1，則導覽會傳回 Ref T >。 如果要結束的基數為 n，則會傳回 < Ref\<T > > 的集合。  
  
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
  
## <a name="select-value-and-select"></a>SELECT VALUE 和 SELECT  
  
### <a name="select-value"></a>SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供 SELECT VALUE 子句來略過隱含資料列建構。 SELECT VALUE 子句中可指定一個項目。 使用這類子句時，不會在 SELECT 子句中的專案周圍建立資料列包裝函式，並且可以產生所需形狀的集合，例如： `SELECT VALUE a`。  
  
 範例：  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
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
 [Case 運算式](case-entity-sql.md)會評估一組布林運算式來決定結果。  
  
 範例：  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 輸出：  
  
|值|  
|-----------|  
|true|  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [Entity SQL 概觀](entity-sql-overview.md)
