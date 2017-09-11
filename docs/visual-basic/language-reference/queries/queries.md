---
title: "查詢 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic]
- LINQ, queries
ms.assetid: 8edc717c-4a24-4cbc-9c16-11f479c935db
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4a178714055076537033fbda32d7c7c1c544351d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="queries-visual-basic"></a><span data-ttu-id="3e796-102">查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e796-102">Queries (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="3e796-103">可讓您建立[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]您的程式碼中的運算式。</span><span class="sxs-lookup"><span data-stu-id="3e796-103"> enables you to create [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e796-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="3e796-104">In This Section</span></span>  
 [<span data-ttu-id="3e796-105">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-105">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 <span data-ttu-id="3e796-106">描述`Aggregate`子句套用至集合的一個或多個彙總函式。</span><span class="sxs-lookup"><span data-stu-id="3e796-106">Describes the `Aggregate` clause, which applies one or more aggregate functions to a collection.</span></span>  
  
 [<span data-ttu-id="3e796-107">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-107">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 <span data-ttu-id="3e796-108">描述`Distinct`子句，以刪除重複的值，查詢結果中目前的範圍變數的值限制。</span><span class="sxs-lookup"><span data-stu-id="3e796-108">Describes the `Distinct` clause, which restricts the values of the current range variable to eliminate duplicate values in query results.</span></span>  
  
 [<span data-ttu-id="3e796-109">From 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-109">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 <span data-ttu-id="3e796-110">描述`From`子句，指定的集合和範圍變數的查詢。</span><span class="sxs-lookup"><span data-stu-id="3e796-110">Describes the `From` clause, which specifies a collection and a range variable for a query.</span></span>  
  
 [<span data-ttu-id="3e796-111">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-111">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)  
 <span data-ttu-id="3e796-112">描述`Group By`子句，分組查詢結果的項目，而且可用來將彙總函式套用至每個群組。</span><span class="sxs-lookup"><span data-stu-id="3e796-112">Describes the `Group By` clause, which groups the elements of a query result and can be used to apply aggregate functions to each group.</span></span>  
  
 [<span data-ttu-id="3e796-113">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-113">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 <span data-ttu-id="3e796-114">描述`Group Join`結合成單一階層式集合的兩個集合的子句。</span><span class="sxs-lookup"><span data-stu-id="3e796-114">Describes the `Group Join` clause, which combines two collections into a single hierarchical collection.</span></span>  
  
 [<span data-ttu-id="3e796-115">Join 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-115">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 <span data-ttu-id="3e796-116">描述`Join`結合成單一集合的兩個集合的子句。</span><span class="sxs-lookup"><span data-stu-id="3e796-116">Describes the `Join` clause, which combines two collections into a single collection.</span></span>  
  
 [<span data-ttu-id="3e796-117">Let 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-117">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 <span data-ttu-id="3e796-118">描述`Let`子句，其中會計算值，並將它指派給查詢中的新變數。</span><span class="sxs-lookup"><span data-stu-id="3e796-118">Describes the `Let` clause, which computes a value and assigns it to a new variable in the query.</span></span>  
  
 [<span data-ttu-id="3e796-119">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-119">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 <span data-ttu-id="3e796-120">描述`Order By`子句，指定在查詢中的資料行的排序順序。</span><span class="sxs-lookup"><span data-stu-id="3e796-120">Describes the `Order By` clause, which specifies the sort order for columns in a query.</span></span>  
  
 [<span data-ttu-id="3e796-121">Select 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-121">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 <span data-ttu-id="3e796-122">描述`Select`子句，會宣告一組查詢的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="3e796-122">Describes the `Select` clause, which declares a set of range variables for a query.</span></span>  
  
 [<span data-ttu-id="3e796-123">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-123">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 <span data-ttu-id="3e796-124">描述`Skip`子句，略過指定的集合中的項目數目，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="3e796-124">Describes the `Skip` clause, which bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="3e796-125">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 <span data-ttu-id="3e796-126">描述`Skip While`子句，略過在集合中的項目，只要指定的條件是`true`，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="3e796-126">Describes the `Skip While` clause, which bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="3e796-127">Take 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-127">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 <span data-ttu-id="3e796-128">描述`Take`子句，從集合開頭傳回指定的連續的項目數。</span><span class="sxs-lookup"><span data-stu-id="3e796-128">Describes the `Take` clause, which returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
 [<span data-ttu-id="3e796-129">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-129">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 <span data-ttu-id="3e796-130">描述`Take While`子句，其中包含集合中的項目，只要指定的條件是`true`，會略過其餘的項目。</span><span class="sxs-lookup"><span data-stu-id="3e796-130">Describes the `Take While` clause, which includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
 [<span data-ttu-id="3e796-131">Where 子句</span><span class="sxs-lookup"><span data-stu-id="3e796-131">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 <span data-ttu-id="3e796-132">描述`Where`子句，指定查詢的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="3e796-132">Describes the `Where` clause, which specifies a filtering condition for a query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e796-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e796-133">See Also</span></span>  
 <span data-ttu-id="3e796-134">[LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="3e796-134">[LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="3e796-135"> [在 Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="3e796-135"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
