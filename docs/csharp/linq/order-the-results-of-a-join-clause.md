---
title: 排序 join 子句的結果 (C# 中的 LINQ)
description: 了解如何在 C# 中排序 LINQ join 子句的結果。
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: e4a12b6f9b4a99decb1f64524ebe67a196084a04
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404732"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="a216f-103">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="a216f-103">Order the results of a join clause</span></span>

<span data-ttu-id="a216f-104">本例示範如何排序聯結作業的結果。</span><span class="sxs-lookup"><span data-stu-id="a216f-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="a216f-105">請注意，排序是在聯結後執行。</span><span class="sxs-lookup"><span data-stu-id="a216f-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="a216f-106">雖然您可以在聯結之前使用 `orderby` 子句搭配一或多個來源序列，但通常不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="a216f-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="a216f-107">某些 LINQ 提供者在聯結後可能不會保留排序。</span><span class="sxs-lookup"><span data-stu-id="a216f-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="a216f-108">範例</span><span class="sxs-lookup"><span data-stu-id="a216f-108">Example</span></span>

<span data-ttu-id="a216f-109">此查詢會建立群組聯結，然後根據類別項目排序仍在範圍內的群組。</span><span class="sxs-lookup"><span data-stu-id="a216f-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="a216f-110">在匿名型別初始設定式內，子查詢會排序產品序列中的所有相符項目。</span><span class="sxs-lookup"><span data-stu-id="a216f-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="a216f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a216f-111">See also</span></span>

[<span data-ttu-id="a216f-112">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="a216f-112">Language Integrated Query (LINQ)</span></span>](index.md)  
[<span data-ttu-id="a216f-113">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="a216f-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
[<span data-ttu-id="a216f-114">join 子句</span><span class="sxs-lookup"><span data-stu-id="a216f-114">join clause</span></span>](../language-reference/keywords/join-clause.md)  