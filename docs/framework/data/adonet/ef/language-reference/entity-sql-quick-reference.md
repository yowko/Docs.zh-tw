---
title: Entity SQL 快速參考
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 0617ce96acaf5a6eafb2658cfe218cc8f4135f6e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765850"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL 快速參考
本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。 本主題中的查詢根據 AdventureWorks Sales model。  
  
## <a name="literals"></a>常值  
  
### <a name="string"></a>String  
 字串常值包括 Unicode 和非 Unicode 字元兩種。 Unicode 字串前面會加一個 n，例如， `N'hello'`。  
  
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
  
### <a name="integer"></a>Integer  
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
 [資料列](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)建構匿名、 結構式型別 （記錄） 中的左值做為： `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
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
 [多重集](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)建構集合，例如：  
  
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
 [具名類型建構函式](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)建構 （具名） 使用者定義的物件，例如`person("abc", 12)`。  
  
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
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)會建立實體類型執行個體的參考。 例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：  
  
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
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)對參考值取值並且產生該取值的結果。 例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。  
  
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
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)會建立傳遞索引鍵的參考。 [索引鍵](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)會擷取具有類型參考之運算式的索引鍵部分。  
  
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
  
## <a name="functions"></a>函式  
  
### <a name="canonical"></a>標準  
 命名空間[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)為 Edm，像是`Edm.Length("string")`。 除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。 如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。  
  
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
 [Microsoft 提供者專屬函式](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)中`SqlServer`命名空間。  
  
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
 [使用](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md)指定查詢運算式中使用命名空間。  
  
 範例：  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 輸出：  
  
|值|  
|-----------|  
|aa|  
  
## <a name="paging"></a>分頁  
 藉由宣告可以表示分頁[略過](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)和[限制](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)子子句，以[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句。  
  
 範例：  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 輸出：  
  
|ID|名稱|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>群組  
 [GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)指定查詢所傳回物件的群組 ([選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 運算式是要放置。  
  
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
  
## <a name="navigation"></a>巡覽  
 關聯性巡覽運算子可以讓您在關聯性上從一個實體 (開始端) 巡覽到另一個實體 (結束端)。 [瀏覽](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)採用關聯性類型指定為\<命名空間 >。\<關聯性類型名稱 >。 瀏覽傳回 Ref\<T > 如果基數的結尾為 1。 如果基數的結尾為 n，集合 < Ref\<T >> 會傳回。  
  
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
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供 SELECT VALUE 子句來略過隱含資料列建構。 SELECT VALUE 子句中可指定一個項目。 這類子句使用時，任何資料列包裝函式會不建構包含 SELECT 子句中的項目所需形狀的集合可以產生，例如： `SELECT VALUE a`。  
  
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
 [Case 運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)會評估一組布林運算式來得出結果。  
  
 範例：  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 輸出：  
  
|值|  
|-----------|  
|true|  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
