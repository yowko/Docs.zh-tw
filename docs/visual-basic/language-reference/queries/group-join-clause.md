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
ms.openlocfilehash: f4c0d7fa9f14868404cde6201692e26b919198be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420633"
---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="2a787-102">Group Join 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a787-102">Group Join Clause (Visual Basic)</span></span>
<span data-ttu-id="2a787-103">將兩個集合合併成單一階層式集合。</span><span class="sxs-lookup"><span data-stu-id="2a787-103">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="2a787-104">聯結作業根據對應索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2a787-104">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a787-105">語法</span><span class="sxs-lookup"><span data-stu-id="2a787-105">Syntax</span></span>  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="2a787-106">組件</span><span class="sxs-lookup"><span data-stu-id="2a787-106">Parts</span></span>  
  
|<span data-ttu-id="2a787-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="2a787-107">Term</span></span>|<span data-ttu-id="2a787-108">定義</span><span class="sxs-lookup"><span data-stu-id="2a787-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="2a787-109">必要。</span><span class="sxs-lookup"><span data-stu-id="2a787-109">Required.</span></span> <span data-ttu-id="2a787-110">要聯結之集合的控制變數。</span><span class="sxs-lookup"><span data-stu-id="2a787-110">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="2a787-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2a787-111">Optional.</span></span> <span data-ttu-id="2a787-112">`element` 的類型。</span><span class="sxs-lookup"><span data-stu-id="2a787-112">The type of `element`.</span></span> <span data-ttu-id="2a787-113">如果沒有`type`指定的型別`element`從推斷而來`collection`。</span><span class="sxs-lookup"><span data-stu-id="2a787-113">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="2a787-114">必要。</span><span class="sxs-lookup"><span data-stu-id="2a787-114">Required.</span></span> <span data-ttu-id="2a787-115">要結合的左側集合的集合`Group Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="2a787-115">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="2a787-116">A`Group Join`子句可以巢狀方式置於`Join`子句或以其他`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="2a787-116">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="2a787-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="2a787-117">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="2a787-118">必要。</span><span class="sxs-lookup"><span data-stu-id="2a787-118">Required.</span></span> <span data-ttu-id="2a787-119">識別要聯結之集合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2a787-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="2a787-120">您必須使用`Equals`運算子來比較所聯結之集合中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2a787-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="2a787-121">您可以使用合併聯結條件`And`運算子來識別多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2a787-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="2a787-122">`key1`參數必須是從左側集合`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="2a787-122">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="2a787-123">`key2`參數必須是從右邊的集合`Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="2a787-123">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="2a787-124">聯結條件中使用索引鍵可以包含一個以上的項目從集合的運算式。</span><span class="sxs-lookup"><span data-stu-id="2a787-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="2a787-125">不過，每個索引鍵的運算式可以包含從其個別集合的項目。</span><span class="sxs-lookup"><span data-stu-id="2a787-125">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="2a787-126">必要。</span><span class="sxs-lookup"><span data-stu-id="2a787-126">Required.</span></span> <span data-ttu-id="2a787-127">識別如何彙總集合中的項目群組的一或多個運算式。</span><span class="sxs-lookup"><span data-stu-id="2a787-127">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="2a787-128">若要識別群組結果的成員名稱，請使用`Group`關鍵字 (`<alias> = Group`)。</span><span class="sxs-lookup"><span data-stu-id="2a787-128">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="2a787-129">您也可以包含將套用至群組的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="2a787-129">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a787-130">備註</span><span class="sxs-lookup"><span data-stu-id="2a787-130">Remarks</span></span>  
 <span data-ttu-id="2a787-131">`Group Join`子句結合兩個集合根據比對所聯結之集合中的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="2a787-131">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="2a787-132">產生的集合可以包含第二個集合中符合第一個集合的索引鍵值參考項目集合的成員。</span><span class="sxs-lookup"><span data-stu-id="2a787-132">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="2a787-133">您也可以指定要套用至群組項目的第二個集合中的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="2a787-133">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="2a787-134">彙總函式的相關資訊，請參閱[彙總子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="2a787-134">For information about aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="2a787-135">例如，考慮，主管的集合和員工的集合。</span><span class="sxs-lookup"><span data-stu-id="2a787-135">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="2a787-136">從這兩個集合的項目具有 ManagerID 屬性可識別直屬特定經理的員工。</span><span class="sxs-lookup"><span data-stu-id="2a787-136">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="2a787-137">聯結作業的結果會包含每個經理和員工具有相符的 ManagerID 值的結果。</span><span class="sxs-lookup"><span data-stu-id="2a787-137">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="2a787-138">從結果`Group Join`作業會包含管理員的完整清單。</span><span class="sxs-lookup"><span data-stu-id="2a787-138">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="2a787-139">每個管理員結果必須參考已符合特定經理的員工清單的成員。</span><span class="sxs-lookup"><span data-stu-id="2a787-139">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="2a787-140">所產生的集合`Group Join`作業可包含一個值，識別集合中的任意組合`From`子句和運算式中識別`Into`子句`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="2a787-140">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="2a787-141">如需有效運算式的詳細資訊`Into`子句，請參閱 < [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="2a787-141">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="2a787-142">A`Group Join`作業會傳回所有結果，從集合所識別的左邊`Group Join`運算子。</span><span class="sxs-lookup"><span data-stu-id="2a787-142">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="2a787-143">這是，則為 true，即使有聯結集合中的沒有相符項目。</span><span class="sxs-lookup"><span data-stu-id="2a787-143">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="2a787-144">這就像是`LEFT OUTER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="2a787-144">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="2a787-145">您可以使用`Join`子句結合成單一集合的集合。</span><span class="sxs-lookup"><span data-stu-id="2a787-145">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="2a787-146">這相當於`INNER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="2a787-146">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a787-147">範例</span><span class="sxs-lookup"><span data-stu-id="2a787-147">Example</span></span>  
 <span data-ttu-id="2a787-148">下列程式碼範例以使用聯結兩個集合`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="2a787-148">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2a787-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a787-149">See Also</span></span>  
 [<span data-ttu-id="2a787-150">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="2a787-150">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="2a787-151">查詢</span><span class="sxs-lookup"><span data-stu-id="2a787-151">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="2a787-152">Select 子句</span><span class="sxs-lookup"><span data-stu-id="2a787-152">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="2a787-153">From 子句</span><span class="sxs-lookup"><span data-stu-id="2a787-153">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="2a787-154">Join 子句</span><span class="sxs-lookup"><span data-stu-id="2a787-154">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="2a787-155">Where 子句</span><span class="sxs-lookup"><span data-stu-id="2a787-155">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="2a787-156">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="2a787-156">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)
