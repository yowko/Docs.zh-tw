---
title: 查詢關鍵字 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 9ec163e1de018bd87348a5b39a1f34654d7d6d84
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47202649"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="ca374-102">查詢關鍵字 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ca374-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="ca374-103">本節包含查詢運算式中所使用的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca374-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ca374-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="ca374-104">In this section</span></span>

|<span data-ttu-id="ca374-105">子句</span><span class="sxs-lookup"><span data-stu-id="ca374-105">Clause</span></span>|<span data-ttu-id="ca374-106">描述</span><span class="sxs-lookup"><span data-stu-id="ca374-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="ca374-107">from</span><span class="sxs-lookup"><span data-stu-id="ca374-107">from</span></span>](from-clause.md)|<span data-ttu-id="ca374-108">指定資料來源和範圍變數 (與反覆運算變數類似)。</span><span class="sxs-lookup"><span data-stu-id="ca374-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="ca374-109">where</span><span class="sxs-lookup"><span data-stu-id="ca374-109">where</span></span>](where-clause.md)|<span data-ttu-id="ca374-110">根據以邏輯 AND 和 OR 運算子區隔的一或多個布林運算式，以篩選來源項目 (`&&` 或 <code>&#124;&#124;</code>)。</span><span class="sxs-lookup"><span data-stu-id="ca374-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="ca374-111">select</span><span class="sxs-lookup"><span data-stu-id="ca374-111">select</span></span>](select-clause.md)|<span data-ttu-id="ca374-112">指定在執行查詢時，所傳回序列中的項目會有的類型和形狀。</span><span class="sxs-lookup"><span data-stu-id="ca374-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="ca374-113">group</span><span class="sxs-lookup"><span data-stu-id="ca374-113">group</span></span>](group-clause.md)|<span data-ttu-id="ca374-114">根據指定的索引鍵值來群組查詢結果。</span><span class="sxs-lookup"><span data-stu-id="ca374-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="ca374-115">into</span><span class="sxs-lookup"><span data-stu-id="ca374-115">into</span></span>](into.md)|<span data-ttu-id="ca374-116">提供可作為 join、group 或 select 子句結果參考的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ca374-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="ca374-117">orderby</span><span class="sxs-lookup"><span data-stu-id="ca374-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="ca374-118">根據項目類型的預設比較子，以遞增或遞減順序來排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="ca374-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="ca374-119">join</span><span class="sxs-lookup"><span data-stu-id="ca374-119">join</span></span>](join-clause.md)|<span data-ttu-id="ca374-120">根據兩個指定比對準則的相等比較，以聯結兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="ca374-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="ca374-121">let</span><span class="sxs-lookup"><span data-stu-id="ca374-121">let</span></span>](let-clause.md)|<span data-ttu-id="ca374-122">引進範圍變數以儲存查詢運算式中的子運算式結果。</span><span class="sxs-lookup"><span data-stu-id="ca374-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="ca374-123">in</span><span class="sxs-lookup"><span data-stu-id="ca374-123">in</span></span>](in.md)|<span data-ttu-id="ca374-124">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca374-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="ca374-125">on</span><span class="sxs-lookup"><span data-stu-id="ca374-125">on</span></span>](on.md)|<span data-ttu-id="ca374-126">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca374-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="ca374-127">equals</span><span class="sxs-lookup"><span data-stu-id="ca374-127">equals</span></span>](equals.md)|<span data-ttu-id="ca374-128">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca374-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="ca374-129">by</span><span class="sxs-lookup"><span data-stu-id="ca374-129">by</span></span>](by.md)|<span data-ttu-id="ca374-130">[group](group-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca374-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="ca374-131">ascending</span><span class="sxs-lookup"><span data-stu-id="ca374-131">ascending</span></span>](ascending.md)|<span data-ttu-id="ca374-132">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca374-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="ca374-133">descending</span><span class="sxs-lookup"><span data-stu-id="ca374-133">descending</span></span>](descending.md)|<span data-ttu-id="ca374-134">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca374-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ca374-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca374-135">See also</span></span>

- [<span data-ttu-id="ca374-136">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ca374-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ca374-137">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="ca374-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="ca374-138">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="ca374-138">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="ca374-139">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="ca374-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)