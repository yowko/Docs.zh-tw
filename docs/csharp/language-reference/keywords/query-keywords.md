---
title: 查詢關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 44af3bf1a7c013c16c7b4a4528c3516621bea149
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422543"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="06757-102">查詢關鍵字 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="06757-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="06757-103">本節包含查詢運算式中所使用的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06757-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="06757-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="06757-104">In this section</span></span>

|<span data-ttu-id="06757-105">子句</span><span class="sxs-lookup"><span data-stu-id="06757-105">Clause</span></span>|<span data-ttu-id="06757-106">描述</span><span class="sxs-lookup"><span data-stu-id="06757-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="06757-107">from</span><span class="sxs-lookup"><span data-stu-id="06757-107">from</span></span>](from-clause.md)|<span data-ttu-id="06757-108">指定資料來源和範圍變數 (與反覆運算變數類似)。</span><span class="sxs-lookup"><span data-stu-id="06757-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="06757-109">where</span><span class="sxs-lookup"><span data-stu-id="06757-109">where</span></span>](where-clause.md)|<span data-ttu-id="06757-110">根據以邏輯 AND 和 OR 運算子區隔的一或多個布林運算式，以篩選來源項目 (`&&` 或 <code>&#124;&#124;</code>)。</span><span class="sxs-lookup"><span data-stu-id="06757-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="06757-111">select</span><span class="sxs-lookup"><span data-stu-id="06757-111">select</span></span>](select-clause.md)|<span data-ttu-id="06757-112">指定在執行查詢時，所傳回序列中的項目會有的類型和形狀。</span><span class="sxs-lookup"><span data-stu-id="06757-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="06757-113">group</span><span class="sxs-lookup"><span data-stu-id="06757-113">group</span></span>](group-clause.md)|<span data-ttu-id="06757-114">根據指定的索引鍵值來群組查詢結果。</span><span class="sxs-lookup"><span data-stu-id="06757-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="06757-115">into</span><span class="sxs-lookup"><span data-stu-id="06757-115">into</span></span>](into.md)|<span data-ttu-id="06757-116">提供可作為 join、group 或 select 子句結果參考的識別碼。</span><span class="sxs-lookup"><span data-stu-id="06757-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="06757-117">orderby</span><span class="sxs-lookup"><span data-stu-id="06757-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="06757-118">根據項目類型的預設比較子，以遞增或遞減順序來排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="06757-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="06757-119">join</span><span class="sxs-lookup"><span data-stu-id="06757-119">join</span></span>](join-clause.md)|<span data-ttu-id="06757-120">根據兩個指定比對準則的相等比較，以聯結兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="06757-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="06757-121">let</span><span class="sxs-lookup"><span data-stu-id="06757-121">let</span></span>](let-clause.md)|<span data-ttu-id="06757-122">引進範圍變數以儲存查詢運算式中的子運算式結果。</span><span class="sxs-lookup"><span data-stu-id="06757-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="06757-123">in</span><span class="sxs-lookup"><span data-stu-id="06757-123">in</span></span>](in.md)|<span data-ttu-id="06757-124">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06757-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="06757-125">on</span><span class="sxs-lookup"><span data-stu-id="06757-125">on</span></span>](on.md)|<span data-ttu-id="06757-126">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06757-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="06757-127">equals</span><span class="sxs-lookup"><span data-stu-id="06757-127">equals</span></span>](equals.md)|<span data-ttu-id="06757-128">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06757-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="06757-129">by</span><span class="sxs-lookup"><span data-stu-id="06757-129">by</span></span>](by.md)|<span data-ttu-id="06757-130">[group](group-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06757-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="06757-131">ascending</span><span class="sxs-lookup"><span data-stu-id="06757-131">ascending</span></span>](ascending.md)|<span data-ttu-id="06757-132">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06757-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="06757-133">descending</span><span class="sxs-lookup"><span data-stu-id="06757-133">descending</span></span>](descending.md)|<span data-ttu-id="06757-134">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06757-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="06757-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="06757-135">See also</span></span>

- [<span data-ttu-id="06757-136">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="06757-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="06757-137">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="06757-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="06757-138">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="06757-138">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="06757-139">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="06757-139">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
