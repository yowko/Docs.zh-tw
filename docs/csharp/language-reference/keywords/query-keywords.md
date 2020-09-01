---
description: 查詢關鍵字 - C# 參考
title: 查詢關鍵字 - C# 參考
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 0beea8634d13222aa18f14d79fdbd95a35cc832e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137132"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="742f5-103">查詢關鍵字 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="742f5-103">Query keywords (C# Reference)</span></span>

<span data-ttu-id="742f5-104">本節包含查詢運算式中所使用的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="742f5-104">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="742f5-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="742f5-105">In this section</span></span>

|<span data-ttu-id="742f5-106">子句</span><span class="sxs-lookup"><span data-stu-id="742f5-106">Clause</span></span>|<span data-ttu-id="742f5-107">描述</span><span class="sxs-lookup"><span data-stu-id="742f5-107">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="742f5-108">from</span><span class="sxs-lookup"><span data-stu-id="742f5-108">from</span></span>](from-clause.md)|<span data-ttu-id="742f5-109">指定資料來源和範圍變數 (與反覆運算變數類似)。</span><span class="sxs-lookup"><span data-stu-id="742f5-109">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="742f5-110">where</span><span class="sxs-lookup"><span data-stu-id="742f5-110">where</span></span>](where-clause.md)|<span data-ttu-id="742f5-111">根據以邏輯 AND 和 OR 運算子區隔的一或多個布林運算式，以篩選來源項目 (`&&` 或 <code>&#124;&#124;</code>)。</span><span class="sxs-lookup"><span data-stu-id="742f5-111">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="742f5-112">select</span><span class="sxs-lookup"><span data-stu-id="742f5-112">select</span></span>](select-clause.md)|<span data-ttu-id="742f5-113">指定在執行查詢時，所傳回序列中的項目會有的類型和形狀。</span><span class="sxs-lookup"><span data-stu-id="742f5-113">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="742f5-114">群組</span><span class="sxs-lookup"><span data-stu-id="742f5-114">group</span></span>](group-clause.md)|<span data-ttu-id="742f5-115">根據指定的索引鍵值來群組查詢結果。</span><span class="sxs-lookup"><span data-stu-id="742f5-115">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="742f5-116">into</span><span class="sxs-lookup"><span data-stu-id="742f5-116">into</span></span>](into.md)|<span data-ttu-id="742f5-117">提供可作為 join、group 或 select 子句結果參考的識別碼。</span><span class="sxs-lookup"><span data-stu-id="742f5-117">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="742f5-118">orderby</span><span class="sxs-lookup"><span data-stu-id="742f5-118">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="742f5-119">根據項目類型的預設比較子，以遞增或遞減順序來排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="742f5-119">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="742f5-120">join</span><span class="sxs-lookup"><span data-stu-id="742f5-120">join</span></span>](join-clause.md)|<span data-ttu-id="742f5-121">根據兩個指定比對準則的相等比較，以聯結兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="742f5-121">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="742f5-122">let</span><span class="sxs-lookup"><span data-stu-id="742f5-122">let</span></span>](let-clause.md)|<span data-ttu-id="742f5-123">引進範圍變數以儲存查詢運算式中的子運算式結果。</span><span class="sxs-lookup"><span data-stu-id="742f5-123">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="742f5-124">in</span><span class="sxs-lookup"><span data-stu-id="742f5-124">in</span></span>](in.md)|<span data-ttu-id="742f5-125">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="742f5-125">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="742f5-126">on</span><span class="sxs-lookup"><span data-stu-id="742f5-126">on</span></span>](on.md)|<span data-ttu-id="742f5-127">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="742f5-127">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="742f5-128">equals</span><span class="sxs-lookup"><span data-stu-id="742f5-128">equals</span></span>](equals.md)|<span data-ttu-id="742f5-129">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="742f5-129">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="742f5-130">by</span><span class="sxs-lookup"><span data-stu-id="742f5-130">by</span></span>](by.md)|<span data-ttu-id="742f5-131">[group](group-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="742f5-131">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="742f5-132">ascending</span><span class="sxs-lookup"><span data-stu-id="742f5-132">ascending</span></span>](ascending.md)|<span data-ttu-id="742f5-133">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="742f5-133">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="742f5-134">descending</span><span class="sxs-lookup"><span data-stu-id="742f5-134">descending</span></span>](descending.md)|<span data-ttu-id="742f5-135">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="742f5-135">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="742f5-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="742f5-136">See also</span></span>

- [<span data-ttu-id="742f5-137">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="742f5-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="742f5-138">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="742f5-138">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="742f5-139">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="742f5-139">LINQ in C#</span></span>](../../linq/index.md)
