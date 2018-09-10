---
title: 在分組作業上執行子查詢 (C# 中的 LINQ)
description: 如何使用 C# 中的 LINQ 在分組作業上執行子查詢。
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 514db81b80557a3026589f00177910cc9446c0f4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270191"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="8266a-103">在分組作業上執行子查詢</span><span class="sxs-lookup"><span data-stu-id="8266a-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="8266a-104">本文說明兩種不同的建立查詢方式，將來源資料排序成群組，然後個別對每個群組執行子查詢。</span><span class="sxs-lookup"><span data-stu-id="8266a-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="8266a-105">每個範例中的基本技巧是使用名為 `newGroup` 的「接續」來分組來源項目，然後針對 `newGroup` 產生新的子查詢。</span><span class="sxs-lookup"><span data-stu-id="8266a-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="8266a-106">這個子查詢會針對外部查詢所建立的每個新群組執行。</span><span class="sxs-lookup"><span data-stu-id="8266a-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="8266a-107">請注意，在這個特別的範例中，最終輸出不是群組，而是匿名型別的一般序列。</span><span class="sxs-lookup"><span data-stu-id="8266a-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="8266a-108">如需如何分組的詳細資訊，請參閱 [group 子句](../language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="8266a-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="8266a-109">如需接續的詳細資訊，請參閱 [into](../language-reference/keywords/into.md)。</span><span class="sxs-lookup"><span data-stu-id="8266a-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="8266a-110">下例將記憶體內部資料結構用為資料來源，但是相同的原則也適用於任何一種 LINQ 資料來源。</span><span class="sxs-lookup"><span data-stu-id="8266a-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8266a-111">範例</span><span class="sxs-lookup"><span data-stu-id="8266a-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="8266a-112">這個範例包含[查詢物件的集合](query-a-collection-of-objects.md)中範例程式碼中定義的物件參考。</span><span class="sxs-lookup"><span data-stu-id="8266a-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="8266a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8266a-113">See also</span></span>

- [<span data-ttu-id="8266a-114">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8266a-114">Language Integrated Query (LINQ)</span></span>](index.md)
