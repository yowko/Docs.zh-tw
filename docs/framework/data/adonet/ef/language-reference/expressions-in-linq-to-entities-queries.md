---
title: LINQ to Entities 查詢中的運算式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f449e7d5626d4a8c9709ae2cb4c026869d1e2dc9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661772"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="42291-102">LINQ to Entities 查詢中的運算式</span><span class="sxs-lookup"><span data-stu-id="42291-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="42291-103">運算式是可以評估為單一值、物件、方法或命名空間的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="42291-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="42291-104">運算式可以包含常值、方法呼叫、運算子及其運算元，或是簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="42291-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="42291-105">簡單名稱可以是變數、型別成員、方法參數、命名空間或型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="42291-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="42291-106">運算式可以使用運算子 (後者又可能使用其他運算式當做參數) 或方法呼叫 (它的參數又可能是其他方法呼叫)。</span><span class="sxs-lookup"><span data-stu-id="42291-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="42291-107">因此，運算式可以很簡單，也可以非常複雜。</span><span class="sxs-lookup"><span data-stu-id="42291-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="42291-108">在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]查詢運算式可以包含內類型所允許的任何項目<xref:System.Linq.Expressions>命名空間，包括 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="42291-108">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="42291-109">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中可以使用的運算式是可用於查詢 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 之運算式的超集。</span><span class="sxs-lookup"><span data-stu-id="42291-109">The expressions that can be used in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="42291-110">運算式所產生的查詢部分[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]所支援的作業僅限於`ObjectQuery<T>`和基礎資料來源。</span><span class="sxs-lookup"><span data-stu-id="42291-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="42291-111">在以下範例中，`Where` 子句中的比較就是個運算式：</span><span class="sxs-lookup"><span data-stu-id="42291-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="42291-112">指定語言建構 (例如 C# `unchecked`) 在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 中沒有意義。</span><span class="sxs-lookup"><span data-stu-id="42291-112">Specific language constructs, such as C# `unchecked`, have no meaning in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42291-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="42291-113">In This Section</span></span>  
 [<span data-ttu-id="42291-114">常數運算式</span><span class="sxs-lookup"><span data-stu-id="42291-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="42291-115">比較運算式</span><span class="sxs-lookup"><span data-stu-id="42291-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="42291-116">Null 比較</span><span class="sxs-lookup"><span data-stu-id="42291-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="42291-117">初始化運算式</span><span class="sxs-lookup"><span data-stu-id="42291-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="42291-118">導覽屬性</span><span class="sxs-lookup"><span data-stu-id="42291-118">Navigation Properties</span></span>](https://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a><span data-ttu-id="42291-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42291-119">See also</span></span>
- [<span data-ttu-id="42291-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="42291-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
