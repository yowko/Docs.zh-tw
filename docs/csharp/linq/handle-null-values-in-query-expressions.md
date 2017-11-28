---
title: "處理查詢運算式中的 Null 值"
description: "如何處理查詢運算式中的 Null 值。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="58183-104">處理查詢運算式中的 Null 值</span><span class="sxs-lookup"><span data-stu-id="58183-104">Handle null values in query expressions</span></span>

<span data-ttu-id="58183-105">本例示範如何處理來源集合中可能有的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="58183-105">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="58183-106">如 <xref:System.Collections.Generic.IEnumerable%601> 的物件集合，可以包含值為 [null](../language-reference/keywords/null.md) 的元素。</span><span class="sxs-lookup"><span data-stu-id="58183-106">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="58183-107">如果來源集合為 Null 或包含值為 Null 的項目，而您的查詢不處理 Null 值，則當您執行查詢時會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="58183-107">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58183-108">範例</span><span class="sxs-lookup"><span data-stu-id="58183-108">Example</span></span>

 <span data-ttu-id="58183-109">您可以謹慎撰寫程式碼以避免發生 Null 參考例外狀況，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="58183-109">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 <span data-ttu-id="58183-110">在上例中，`where` 子句會篩選掉類別序列中的所有 Null 項目。</span><span class="sxs-lookup"><span data-stu-id="58183-110">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="58183-111">這項技術不影響 join 子句中的 Null 檢查。</span><span class="sxs-lookup"><span data-stu-id="58183-111">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="58183-112">因為 `Products.CategoryID` 是 `int?` 類型，即 `Nullable<int>` 的速記，所以具有 Null 的條件運算式在本例中可以運作。</span><span class="sxs-lookup"><span data-stu-id="58183-112">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58183-113">範例</span><span class="sxs-lookup"><span data-stu-id="58183-113">Example</span></span>

 <span data-ttu-id="58183-114">在 join 子句中，如果僅有一個比較索引鍵是可為 Null 的實值型別，則可以在查詢運算式中將其他的轉換成可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="58183-114">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="58183-115">在下列範例中，假設 `EmployeeID` 是包含 `int?` 類型值的資料行：</span><span class="sxs-lookup"><span data-stu-id="58183-115">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="58183-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="58183-116">See also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="58183-117">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="58183-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="58183-118">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="58183-118">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
