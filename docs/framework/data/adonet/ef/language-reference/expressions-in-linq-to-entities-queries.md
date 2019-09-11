---
title: LINQ to Entities 查詢中的運算式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: e625ac3968542c65e737093c0ac292de4c2ffa37
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854466"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="7f591-102">LINQ to Entities 查詢中的運算式</span><span class="sxs-lookup"><span data-stu-id="7f591-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="7f591-103">運算式是可以評估為單一值、物件、方法或命名空間的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="7f591-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="7f591-104">運算式可以包含常值、方法呼叫、運算子及其運算元，或是簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="7f591-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="7f591-105">簡單名稱可以是變數、型別成員、方法參數、命名空間或型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f591-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="7f591-106">運算式可以使用運算子 (後者又可能使用其他運算式當做參數) 或方法呼叫 (它的參數又可能是其他方法呼叫)。</span><span class="sxs-lookup"><span data-stu-id="7f591-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="7f591-107">因此，運算式可以很簡單，也可以非常複雜。</span><span class="sxs-lookup"><span data-stu-id="7f591-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="7f591-108">在 LINQ to Entities 查詢中，運算式可以包含<xref:System.Linq.Expressions>命名空間中的類型所允許的任何專案，包括 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="7f591-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="7f591-109">可以在 LINQ to Entities 查詢中使用的運算式是運算式的超集合，可以用來查詢 Entity Framework。針對 Entity Framework 的查詢中的運算式僅限於`ObjectQuery<T>`和支援的作業基礎資料來源。</span><span class="sxs-lookup"><span data-stu-id="7f591-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="7f591-110">在以下範例中，`Where` 子句中的比較就是個運算式：</span><span class="sxs-lookup"><span data-stu-id="7f591-110">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="7f591-111">特定語言結構（例如C# `unchecked`）在 LINQ to Entities 中沒有任何意義。</span><span class="sxs-lookup"><span data-stu-id="7f591-111">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f591-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="7f591-112">In This Section</span></span>  
 [<span data-ttu-id="7f591-113">常數運算式</span><span class="sxs-lookup"><span data-stu-id="7f591-113">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="7f591-114">比較運算式</span><span class="sxs-lookup"><span data-stu-id="7f591-114">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="7f591-115">Null 比較</span><span class="sxs-lookup"><span data-stu-id="7f591-115">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="7f591-116">初始化運算式</span><span class="sxs-lookup"><span data-stu-id="7f591-116">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="7f591-117">關聯性、導覽屬性和外鍵</span><span class="sxs-lookup"><span data-stu-id="7f591-117">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="7f591-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f591-118">See also</span></span>

- [<span data-ttu-id="7f591-119">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="7f591-119">ADO.NET Entity Framework</span></span>](../index.md)
