---
title: 查詢關鍵字 - C# 參考
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 01134eda540c5141afbd11b2c89ff779da495a9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173519"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="255a3-102">查詢關鍵字 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="255a3-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="255a3-103">本節包含查詢運算式中所使用的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="255a3-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="255a3-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="255a3-104">In this section</span></span>

|<span data-ttu-id="255a3-105">子句</span><span class="sxs-lookup"><span data-stu-id="255a3-105">Clause</span></span>|<span data-ttu-id="255a3-106">描述</span><span class="sxs-lookup"><span data-stu-id="255a3-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="255a3-107">從</span><span class="sxs-lookup"><span data-stu-id="255a3-107">from</span></span>](from-clause.md)|<span data-ttu-id="255a3-108">指定資料來源和範圍變數 (與反覆運算變數類似)。</span><span class="sxs-lookup"><span data-stu-id="255a3-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="255a3-109">其中</span><span class="sxs-lookup"><span data-stu-id="255a3-109">where</span></span>](where-clause.md)|<span data-ttu-id="255a3-110">根據以邏輯 AND 和 OR 運算子區隔的一或多個布林運算式，以篩選來源項目 (`&&` 或 <code>&#124;&#124;</code>)。</span><span class="sxs-lookup"><span data-stu-id="255a3-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="255a3-111">選擇</span><span class="sxs-lookup"><span data-stu-id="255a3-111">select</span></span>](select-clause.md)|<span data-ttu-id="255a3-112">指定在執行查詢時，所傳回序列中的項目會有的類型和形狀。</span><span class="sxs-lookup"><span data-stu-id="255a3-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="255a3-113">群組</span><span class="sxs-lookup"><span data-stu-id="255a3-113">group</span></span>](group-clause.md)|<span data-ttu-id="255a3-114">根據指定的索引鍵值來群組查詢結果。</span><span class="sxs-lookup"><span data-stu-id="255a3-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="255a3-115">into</span><span class="sxs-lookup"><span data-stu-id="255a3-115">into</span></span>](into.md)|<span data-ttu-id="255a3-116">提供可作為 join、group 或 select 子句結果參考的識別碼。</span><span class="sxs-lookup"><span data-stu-id="255a3-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="255a3-117">orderby</span><span class="sxs-lookup"><span data-stu-id="255a3-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="255a3-118">根據項目類型的預設比較子，以遞增或遞減順序來排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="255a3-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="255a3-119">加入</span><span class="sxs-lookup"><span data-stu-id="255a3-119">join</span></span>](join-clause.md)|<span data-ttu-id="255a3-120">根據兩個指定比對準則的相等比較，以聯結兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="255a3-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="255a3-121">讓</span><span class="sxs-lookup"><span data-stu-id="255a3-121">let</span></span>](let-clause.md)|<span data-ttu-id="255a3-122">引進範圍變數以儲存查詢運算式中的子運算式結果。</span><span class="sxs-lookup"><span data-stu-id="255a3-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="255a3-123">在</span><span class="sxs-lookup"><span data-stu-id="255a3-123">in</span></span>](in.md)|<span data-ttu-id="255a3-124">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="255a3-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="255a3-125">上</span><span class="sxs-lookup"><span data-stu-id="255a3-125">on</span></span>](on.md)|<span data-ttu-id="255a3-126">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="255a3-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="255a3-127">等於</span><span class="sxs-lookup"><span data-stu-id="255a3-127">equals</span></span>](equals.md)|<span data-ttu-id="255a3-128">[join](join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="255a3-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="255a3-129">由</span><span class="sxs-lookup"><span data-stu-id="255a3-129">by</span></span>](by.md)|<span data-ttu-id="255a3-130">[group](group-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="255a3-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="255a3-131">上升</span><span class="sxs-lookup"><span data-stu-id="255a3-131">ascending</span></span>](ascending.md)|<span data-ttu-id="255a3-132">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="255a3-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="255a3-133">降</span><span class="sxs-lookup"><span data-stu-id="255a3-133">descending</span></span>](descending.md)|<span data-ttu-id="255a3-134">[orderby](orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="255a3-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="255a3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="255a3-135">See also</span></span>

- [<span data-ttu-id="255a3-136">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="255a3-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="255a3-137">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="255a3-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="255a3-138">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="255a3-138">LINQ in C#</span></span>](../../linq/index.md)
