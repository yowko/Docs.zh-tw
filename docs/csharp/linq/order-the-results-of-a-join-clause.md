---
title: "排序 join 子句的結果"
description: "如何排序 join 子句的結果。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="b7aee-104">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="b7aee-104">Order the results of a join clause</span></span>
<span data-ttu-id="b7aee-105">本例示範如何排序聯結作業的結果。</span><span class="sxs-lookup"><span data-stu-id="b7aee-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="b7aee-106">請注意，排序是在聯結後執行。</span><span class="sxs-lookup"><span data-stu-id="b7aee-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="b7aee-107">雖然您可以在聯結之前使用 `orderby` 子句搭配一或多個來源序列，但通常不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="b7aee-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="b7aee-108">某些 LINQ 提供者在聯結後可能不會保留排序。</span><span class="sxs-lookup"><span data-stu-id="b7aee-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7aee-109">範例</span><span class="sxs-lookup"><span data-stu-id="b7aee-109">Example</span></span>  
 <span data-ttu-id="b7aee-110">此查詢會建立群組聯結，然後根據類別項目排序仍在範圍內的群組。</span><span class="sxs-lookup"><span data-stu-id="b7aee-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="b7aee-111">在匿名型別初始設定式內，子查詢會排序產品序列中的所有相符項目。</span><span class="sxs-lookup"><span data-stu-id="b7aee-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="b7aee-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7aee-112">See also</span></span>  
 [<span data-ttu-id="b7aee-113">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="b7aee-113">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="b7aee-114">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="b7aee-114">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="b7aee-115">join 子句</span><span class="sxs-lookup"><span data-stu-id="b7aee-115">join clause</span></span>](../language-reference/keywords/join-clause.md) 
