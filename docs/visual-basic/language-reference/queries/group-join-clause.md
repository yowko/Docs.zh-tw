---
title: Group Join 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 184077f2689eb64e4373d407913eefcc03b795c2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005730"
---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="0ad51-102">Group Join 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ad51-102">Group Join Clause (Visual Basic)</span></span>
<span data-ttu-id="0ad51-103">將兩個集合合併成單一階層式集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-103">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="0ad51-104">聯結作業是以相符的索引鍵為基礎。</span><span class="sxs-lookup"><span data-stu-id="0ad51-104">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad51-105">語法</span><span class="sxs-lookup"><span data-stu-id="0ad51-105">Syntax</span></span>  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="0ad51-106">組件</span><span class="sxs-lookup"><span data-stu-id="0ad51-106">Parts</span></span>  
  
|<span data-ttu-id="0ad51-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="0ad51-107">Term</span></span>|<span data-ttu-id="0ad51-108">定義</span><span class="sxs-lookup"><span data-stu-id="0ad51-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="0ad51-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="0ad51-109">Required.</span></span> <span data-ttu-id="0ad51-110">要聯結之集合的控制項變數。</span><span class="sxs-lookup"><span data-stu-id="0ad51-110">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="0ad51-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0ad51-111">Optional.</span></span> <span data-ttu-id="0ad51-112">`element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="0ad51-112">The type of `element`.</span></span> <span data-ttu-id="0ad51-113">如果未指定 `type`，則會從 `collection` 推斷 `element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="0ad51-113">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="0ad51-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="0ad51-114">Required.</span></span> <span data-ttu-id="0ad51-115">要與 `Group Join` 運算子左邊的集合結合的集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-115">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="0ad51-116">@No__t 0 子句可以嵌套在 @no__t 1 子句或另一個 `Group Join` 子句中。</span><span class="sxs-lookup"><span data-stu-id="0ad51-116">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="0ad51-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="0ad51-117">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="0ad51-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="0ad51-118">Required.</span></span> <span data-ttu-id="0ad51-119">識別要聯結之集合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0ad51-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="0ad51-120">您必須使用 `Equals` 運算子來比較所聯結之集合中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0ad51-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="0ad51-121">您可以使用 `And` 運算子來結合聯結條件，以識別多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0ad51-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="0ad51-122">@No__t-0 參數必須來自 `Join` 運算子左邊的集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-122">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="0ad51-123">@No__t-0 參數必須來自 `Join` 運算子右邊的集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-123">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="0ad51-124">聯結條件中使用的索引鍵可以是包含集合中一個以上專案的運算式。</span><span class="sxs-lookup"><span data-stu-id="0ad51-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="0ad51-125">不過，每個索引鍵運算式只能包含其各自集合中的專案。</span><span class="sxs-lookup"><span data-stu-id="0ad51-125">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="0ad51-126">必要項。</span><span class="sxs-lookup"><span data-stu-id="0ad51-126">Required.</span></span> <span data-ttu-id="0ad51-127">一或多個運算式，可識別如何匯總集合中的元素群組。</span><span class="sxs-lookup"><span data-stu-id="0ad51-127">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="0ad51-128">若要識別群組結果的成員名稱，請使用 `Group` 關鍵字（`<alias> = Group`）。</span><span class="sxs-lookup"><span data-stu-id="0ad51-128">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="0ad51-129">您也可以包含將套用至群組的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="0ad51-129">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ad51-130">備註</span><span class="sxs-lookup"><span data-stu-id="0ad51-130">Remarks</span></span>  
 <span data-ttu-id="0ad51-131">@No__t-0 子句會根據聯結的集合中相符的索引鍵值，結合兩個集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-131">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="0ad51-132">產生的集合可以包含一個成員，其參考第二個集合中符合第一個集合之索引鍵值的元素集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-132">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="0ad51-133">您也可以指定彙總函式，以套用至第二個集合中的群組元素。</span><span class="sxs-lookup"><span data-stu-id="0ad51-133">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="0ad51-134">如需彙總函式的詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad51-134">For information about aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="0ad51-135">例如，假設有一組經理和員工集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-135">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="0ad51-136">這兩個集合中的元素都具有 ManagerID 屬性，可識別向特定經理報告的員工。</span><span class="sxs-lookup"><span data-stu-id="0ad51-136">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="0ad51-137">聯結作業的結果會包含每個經理和員工的結果，並具有相符的 ManagerID 值。</span><span class="sxs-lookup"><span data-stu-id="0ad51-137">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="0ad51-138">@No__t-0 作業的結果會包含完整的管理員清單。</span><span class="sxs-lookup"><span data-stu-id="0ad51-138">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="0ad51-139">每個管理員結果都有一個成員，參考與特定經理相符的員工清單。</span><span class="sxs-lookup"><span data-stu-id="0ad51-139">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="0ad51-140">由 @no__t 0 作業所產生的集合可以包含在 `From` 子句中識別之集合中的任何值組合，以及在 `Group Join` 子句的 `Into` 子句中識別的運算式。</span><span class="sxs-lookup"><span data-stu-id="0ad51-140">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="0ad51-141">如需 `Into` 子句之有效運算式的詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad51-141">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="0ad51-142">@No__t-0 作業會從 `Group Join` 運算子左側識別的集合傳回所有結果。</span><span class="sxs-lookup"><span data-stu-id="0ad51-142">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="0ad51-143">即使聯結的集合中沒有相符專案，也是如此。</span><span class="sxs-lookup"><span data-stu-id="0ad51-143">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="0ad51-144">這就像是 SQL 中的 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="0ad51-144">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="0ad51-145">您可以使用 `Join` 子句，將集合結合成單一集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-145">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="0ad51-146">這相當於 SQL 中的 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="0ad51-146">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ad51-147">範例</span><span class="sxs-lookup"><span data-stu-id="0ad51-147">Example</span></span>  
 <span data-ttu-id="0ad51-148">下列程式碼範例使用 `Group Join` 子句來聯結兩個集合。</span><span class="sxs-lookup"><span data-stu-id="0ad51-148">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="0ad51-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad51-149">See also</span></span>

- [<span data-ttu-id="0ad51-150">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="0ad51-150">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0ad51-151">查詢</span><span class="sxs-lookup"><span data-stu-id="0ad51-151">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="0ad51-152">Select 子句</span><span class="sxs-lookup"><span data-stu-id="0ad51-152">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="0ad51-153">From 子句</span><span class="sxs-lookup"><span data-stu-id="0ad51-153">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="0ad51-154">Join 子句</span><span class="sxs-lookup"><span data-stu-id="0ad51-154">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="0ad51-155">Where 子句</span><span class="sxs-lookup"><span data-stu-id="0ad51-155">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="0ad51-156">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="0ad51-156">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)
