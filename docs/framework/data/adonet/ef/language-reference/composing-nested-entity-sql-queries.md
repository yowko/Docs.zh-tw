---
title: 撰寫巢狀 Entity SQL 查詢
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: cd41c36853f50597a32d511d455148d649d9eb64
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395551"
---
# <a name="composing-nested-entity-sql-queries"></a>撰寫巢狀 Entity SQL 查詢
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 是一個豐富的功能性語言。 @No__t-0 的建立區塊是運算式。 不同于傳統 SQL，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不限於表格式結果集： [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援撰寫可以具有常值、參數或嵌套運算式的複雜運算式。 運算式中的值可以參數化，或由其他運算式組成。  
  
## <a name="nested-expressions"></a>巢狀運算式  
 巢狀運算式可以放在它傳回之型別的值接受的任何地方。 例如:  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 巢狀查詢可放在投影子句中。 例如:  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，巢狀查詢一定要括在括號中：  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 下列範例示範如何在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中適當地嵌套運算式： how [to：排序兩個查詢的聯集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))。  
  
## <a name="nested-queries-in-projection"></a>投影中的巢狀查詢  
 投影子句中的巢狀查詢可能會在伺服器上轉譯成笛卡兒乘積 (Cartesian Product) 查詢。 在某些後端伺服器（包括 SQL Server）中，這可能會導致 TempDB 資料表變得非常大，這可能會對伺服器效能造成負面影響。  
  
 下列是這類查詢的範例：  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>排序巢狀查詢  
 在 Entity Framework 中，巢狀運算式可放在查詢中的任何地方。 由於 Entity SQL 在撰寫查詢方面提供很大的彈性，所以您可以撰寫包含巢狀查詢排序的查詢。 不過，系統不會保留巢狀查詢的順序。  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
