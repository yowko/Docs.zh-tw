---
title: 撰寫巢狀 Entity SQL 查詢
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 0ab92c1e41c89f141c3cbd37be3e1e18e64d9666
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833907"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="21807-102">撰寫巢狀 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="21807-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="21807-103">是一個豐富的功能性語言。</span><span class="sxs-lookup"><span data-stu-id="21807-103">is a rich functional language.</span></span> <span data-ttu-id="21807-104">@No__t-0 的建立區塊是運算式。</span><span class="sxs-lookup"><span data-stu-id="21807-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="21807-105">不同于傳統 SQL，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不限於表格式結果集： [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援撰寫可以具有常值、參數或嵌套運算式的複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="21807-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="21807-106">運算式中的值可以參數化，或由其他運算式組成。</span><span class="sxs-lookup"><span data-stu-id="21807-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="21807-107">巢狀運算式</span><span class="sxs-lookup"><span data-stu-id="21807-107">Nested Expressions</span></span>  
 <span data-ttu-id="21807-108">巢狀運算式可以放在它傳回之型別的值接受的任何地方。</span><span class="sxs-lookup"><span data-stu-id="21807-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="21807-109">例如:</span><span class="sxs-lookup"><span data-stu-id="21807-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="21807-110">巢狀查詢可放在投影子句中。</span><span class="sxs-lookup"><span data-stu-id="21807-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="21807-111">例如:</span><span class="sxs-lookup"><span data-stu-id="21807-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="21807-112">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，巢狀查詢一定要括在括號中：</span><span class="sxs-lookup"><span data-stu-id="21807-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="21807-113">下列範例示範如何在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中適當地嵌套運算式：[如何：將兩個查詢的聯集排序 @ no__t-0。</span><span class="sxs-lookup"><span data-stu-id="21807-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="21807-114">投影中的巢狀查詢</span><span class="sxs-lookup"><span data-stu-id="21807-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="21807-115">投影子句中的巢狀查詢可能會在伺服器上轉譯成笛卡兒乘積 (Cartesian Product) 查詢。</span><span class="sxs-lookup"><span data-stu-id="21807-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="21807-116">在包括 SQL Server 的某些後端伺服器上，這樣可能會導致 TempDB 資料表變得相當大，因而對伺服器效能造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="21807-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="21807-117">下列是這類查詢的範例：</span><span class="sxs-lookup"><span data-stu-id="21807-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="21807-118">排序巢狀查詢</span><span class="sxs-lookup"><span data-stu-id="21807-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="21807-119">在 Entity Framework 中，巢狀運算式可放在查詢中的任何地方。</span><span class="sxs-lookup"><span data-stu-id="21807-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="21807-120">由於 Entity SQL 在撰寫查詢方面提供很大的彈性，所以您可以撰寫包含巢狀查詢排序的查詢。</span><span class="sxs-lookup"><span data-stu-id="21807-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="21807-121">不過，系統不會保留巢狀查詢的順序。</span><span class="sxs-lookup"><span data-stu-id="21807-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21807-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21807-122">See also</span></span>

- [<span data-ttu-id="21807-123">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="21807-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
