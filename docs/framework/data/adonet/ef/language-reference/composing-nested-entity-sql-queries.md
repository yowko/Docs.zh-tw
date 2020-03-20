---
title: 撰寫巢狀 Entity SQL 查詢
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150385"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="7d3ca-102">撰寫巢狀 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="7d3ca-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7d3ca-103">是一個豐富的功能性語言。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-103">is a rich functional language.</span></span> <span data-ttu-id="7d3ca-104">的[!INCLUDE[esql](../../../../../../includes/esql-md.md)]構建基塊是運算式。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="7d3ca-105">與傳統的 SQL[!INCLUDE[esql](../../../../../../includes/esql-md.md)]不同，它並不限於表格結果集：[!INCLUDE[esql](../../../../../../includes/esql-md.md)]支援編寫可以具有文本、參數或嵌套運算式的複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="7d3ca-106">運算式中的值可以參數化，或是由某個其他運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="7d3ca-107">巢狀運算式</span><span class="sxs-lookup"><span data-stu-id="7d3ca-107">Nested Expressions</span></span>  
 <span data-ttu-id="7d3ca-108">巢狀運算式可以放在它傳回之型別的值接受的任何地方。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="7d3ca-109">例如：</span><span class="sxs-lookup"><span data-stu-id="7d3ca-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="7d3ca-110">巢狀查詢可放在投影子句中。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="7d3ca-111">例如：</span><span class="sxs-lookup"><span data-stu-id="7d3ca-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="7d3ca-112">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，巢狀查詢一定要括在括號中：</span><span class="sxs-lookup"><span data-stu-id="7d3ca-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="7d3ca-113">下面的示例演示如何在[!INCLUDE[esql](../../../../../../includes/esql-md.md)]：[如何：命令兩個查詢的聯盟](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))中正確嵌套運算式。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="7d3ca-114">投影中的巢狀查詢</span><span class="sxs-lookup"><span data-stu-id="7d3ca-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="7d3ca-115">投影子句中的巢狀查詢可能會在伺服器上轉譯成笛卡兒乘積 (Cartesian Product) 查詢。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="7d3ca-116">在某些後端伺服器（包括 SQL Server）中，這可能導致 TempDB 表變得非常大，從而對伺服器性能產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-116">In some backend servers, including SQL Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="7d3ca-117">下列是這類查詢的範例：</span><span class="sxs-lookup"><span data-stu-id="7d3ca-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="7d3ca-118">排序巢狀查詢</span><span class="sxs-lookup"><span data-stu-id="7d3ca-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="7d3ca-119">在 Entity Framework 中，巢狀運算式可放在查詢中的任何地方。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="7d3ca-120">由於 Entity SQL 在撰寫查詢方面提供很大的彈性，所以您可以撰寫包含巢狀查詢排序的查詢。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="7d3ca-121">不過，系統不會保留巢狀查詢的順序。</span><span class="sxs-lookup"><span data-stu-id="7d3ca-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d3ca-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d3ca-122">See also</span></span>

- [<span data-ttu-id="7d3ca-123">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="7d3ca-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
