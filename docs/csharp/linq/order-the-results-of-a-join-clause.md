---
title: "排序 join 子句的結果"
description: "如何排序 join 子句的結果。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6272181647bb200c18231c5fc836e3dd1a2d6d55
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="b1942-104">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="b1942-104">Order the results of a join clause</span></span>
<span data-ttu-id="b1942-105">本例示範如何排序聯結作業的結果。</span><span class="sxs-lookup"><span data-stu-id="b1942-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="b1942-106">請注意，排序是在聯結後執行。</span><span class="sxs-lookup"><span data-stu-id="b1942-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="b1942-107">雖然您可以在聯結之前使用 `orderby` 子句搭配一或多個來源序列，但通常不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="b1942-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="b1942-108">某些 LINQ 提供者在聯結後可能不會保留排序。</span><span class="sxs-lookup"><span data-stu-id="b1942-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1942-109">範例</span><span class="sxs-lookup"><span data-stu-id="b1942-109">Example</span></span>  
 <span data-ttu-id="b1942-110">此查詢會建立群組聯結，然後根據類別項目排序仍在範圍內的群組。</span><span class="sxs-lookup"><span data-stu-id="b1942-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="b1942-111">在匿名型別初始設定式內，子查詢會排序產品序列中的所有相符項目。</span><span class="sxs-lookup"><span data-stu-id="b1942-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 <span data-ttu-id="b1942-112">[!code-cs[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1942-112">[!code-cs[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="b1942-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1942-113">See also</span></span>  
 <span data-ttu-id="b1942-114">[LINQ 查詢運算式](index.md) </span><span class="sxs-lookup"><span data-stu-id="b1942-114">[LINQ query expressions](index.md) </span></span>  
 <span data-ttu-id="b1942-115">[orderby 子句](../language-reference/keywords/orderby-clause.md) </span><span class="sxs-lookup"><span data-stu-id="b1942-115">[orderby clause](../language-reference/keywords/orderby-clause.md) </span></span>  
 [<span data-ttu-id="b1942-116">join 子句</span><span class="sxs-lookup"><span data-stu-id="b1942-116">join clause</span></span>](../language-reference/keywords/join-clause.md) 

