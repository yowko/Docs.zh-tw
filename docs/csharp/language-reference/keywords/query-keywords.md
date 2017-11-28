---
title: "查詢關鍵字 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 30526e7bc4f99110d421855866381d9b7934d31c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="bb455-102">查詢關鍵字 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bb455-102">Query Keywords (C# Reference)</span></span>
<span data-ttu-id="bb455-103">本節包含查詢運算式中所使用的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb455-103">This section contains the contextual keywords used in query expressions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb455-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="bb455-104">In This Section</span></span>  
  
|<span data-ttu-id="bb455-105">子句</span><span class="sxs-lookup"><span data-stu-id="bb455-105">Clause</span></span>|<span data-ttu-id="bb455-106">說明</span><span class="sxs-lookup"><span data-stu-id="bb455-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb455-107">from</span><span class="sxs-lookup"><span data-stu-id="bb455-107">from</span></span>](../../../csharp/language-reference/keywords/from-clause.md)|<span data-ttu-id="bb455-108">指定資料來源和範圍變數 (與反覆運算變數類似)。</span><span class="sxs-lookup"><span data-stu-id="bb455-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|  
|[<span data-ttu-id="bb455-109">where</span><span class="sxs-lookup"><span data-stu-id="bb455-109">where</span></span>](../../../csharp/language-reference/keywords/where-clause.md)|<span data-ttu-id="bb455-110">根據以邏輯 AND 和 OR 運算子區隔的一或多個布林運算式，以篩選來源項目 (`&&` 或 <code>&#124;&#124;</code>)。</span><span class="sxs-lookup"><span data-stu-id="bb455-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|  
|[<span data-ttu-id="bb455-111">select</span><span class="sxs-lookup"><span data-stu-id="bb455-111">select</span></span>](../../../csharp/language-reference/keywords/select-clause.md)|<span data-ttu-id="bb455-112">指定在執行查詢時，所傳回序列中的項目會有的類型和形狀。</span><span class="sxs-lookup"><span data-stu-id="bb455-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|  
|[<span data-ttu-id="bb455-113">group</span><span class="sxs-lookup"><span data-stu-id="bb455-113">group</span></span>](../../../csharp/language-reference/keywords/group-clause.md)|<span data-ttu-id="bb455-114">根據指定的索引鍵值來群組查詢結果。</span><span class="sxs-lookup"><span data-stu-id="bb455-114">Groups query results according to a specified key value.</span></span>|  
|[<span data-ttu-id="bb455-115">into</span><span class="sxs-lookup"><span data-stu-id="bb455-115">into</span></span>](../../../csharp/language-reference/keywords/into.md)|<span data-ttu-id="bb455-116">提供可作為 join、group 或 select 子句結果參考的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bb455-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|  
|[<span data-ttu-id="bb455-117">orderby</span><span class="sxs-lookup"><span data-stu-id="bb455-117">orderby</span></span>](../../../csharp/language-reference/keywords/orderby-clause.md)|<span data-ttu-id="bb455-118">根據項目類型的預設比較子，以遞增或遞減順序來排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="bb455-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|  
|[<span data-ttu-id="bb455-119">join</span><span class="sxs-lookup"><span data-stu-id="bb455-119">join</span></span>](../../../csharp/language-reference/keywords/join-clause.md)|<span data-ttu-id="bb455-120">根據兩個指定比對準則的相等比較，以聯結兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="bb455-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|  
|[<span data-ttu-id="bb455-121">let</span><span class="sxs-lookup"><span data-stu-id="bb455-121">let</span></span>](../../../csharp/language-reference/keywords/let-clause.md)|<span data-ttu-id="bb455-122">引進範圍變數以儲存查詢運算式中的子運算式結果。</span><span class="sxs-lookup"><span data-stu-id="bb455-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|  
|[<span data-ttu-id="bb455-123">in</span><span class="sxs-lookup"><span data-stu-id="bb455-123">in</span></span>](../../../csharp/language-reference/keywords/in.md)|<span data-ttu-id="bb455-124">[join](../../../csharp/language-reference/keywords/join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb455-124">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="bb455-125">on</span><span class="sxs-lookup"><span data-stu-id="bb455-125">on</span></span>](../../../csharp/language-reference/keywords/on.md)|<span data-ttu-id="bb455-126">[join](../../../csharp/language-reference/keywords/join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb455-126">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="bb455-127">equals</span><span class="sxs-lookup"><span data-stu-id="bb455-127">equals</span></span>](../../../csharp/language-reference/keywords/equals.md)|<span data-ttu-id="bb455-128">[join](../../../csharp/language-reference/keywords/join-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb455-128">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="bb455-129">by</span><span class="sxs-lookup"><span data-stu-id="bb455-129">by</span></span>](../../../csharp/language-reference/keywords/by.md)|<span data-ttu-id="bb455-130">[group](../../../csharp/language-reference/keywords/group-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb455-130">Contextual keyword in a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>|  
|[<span data-ttu-id="bb455-131">ascending</span><span class="sxs-lookup"><span data-stu-id="bb455-131">ascending</span></span>](../../../csharp/language-reference/keywords/ascending.md)|<span data-ttu-id="bb455-132">[orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb455-132">Contextual keyword in an [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clause.</span></span>|  
|[<span data-ttu-id="bb455-133">descending</span><span class="sxs-lookup"><span data-stu-id="bb455-133">descending</span></span>](../../../csharp/language-reference/keywords/descending.md)|<span data-ttu-id="bb455-134">[orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 子句中的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb455-134">Contextual keyword in an [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clause.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb455-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb455-135">See Also</span></span>  
 [<span data-ttu-id="bb455-136">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bb455-136">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bb455-137">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="bb455-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="bb455-138">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="bb455-138">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="bb455-139">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="bb455-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
