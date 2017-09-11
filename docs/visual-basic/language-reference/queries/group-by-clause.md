---
title: "Group By 子句 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement
- Group By clause
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: 20
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
ms.openlocfilehash: a27e2f15e61456b2e7ac0ede81c66cdb4e8fd612
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="1f695-102">Group By 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f695-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="1f695-103">群組查詢結果的項目。</span><span class="sxs-lookup"><span data-stu-id="1f695-103">Groups the elements of a query result.</span></span> <span data-ttu-id="1f695-104">也可用來將彙總函式套用至每個群組。</span><span class="sxs-lookup"><span data-stu-id="1f695-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="1f695-105">群組作業是根據一個或多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1f695-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f695-106">語法</span><span class="sxs-lookup"><span data-stu-id="1f695-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="1f695-107">組件</span><span class="sxs-lookup"><span data-stu-id="1f695-107">Parts</span></span>  
  
-   <span data-ttu-id="1f695-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="1f695-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="1f695-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1f695-109">Optional.</span></span> <span data-ttu-id="1f695-110">一或多個查詢變數的欄位，明確識別要包含在群組結果中的欄位。</span><span class="sxs-lookup"><span data-stu-id="1f695-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="1f695-111">如果未指定任何欄位，群組結果中會包含查詢變數的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="1f695-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="1f695-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="1f695-112">Required.</span></span> <span data-ttu-id="1f695-113">識別要用來判斷項目群組之索引鍵的運算式。</span><span class="sxs-lookup"><span data-stu-id="1f695-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="1f695-114">您可以指定多個索引鍵，指定複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1f695-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="1f695-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1f695-115">Optional.</span></span> <span data-ttu-id="1f695-116">一或多個額外的金鑰，結合了 `keyExp1` 以建立複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1f695-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="1f695-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="1f695-117">Required.</span></span> <span data-ttu-id="1f695-118">識別群組彙總方式的一或多個運算式。</span><span class="sxs-lookup"><span data-stu-id="1f695-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="1f695-119">若要識別群組結果的成員名稱，請使用 `Group` 關鍵字，它可以是下列任一形式：</span><span class="sxs-lookup"><span data-stu-id="1f695-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="1f695-120">-或-</span><span class="sxs-lookup"><span data-stu-id="1f695-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="1f695-121">您也可以包含將套用至群組的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="1f695-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f695-122">備註</span><span class="sxs-lookup"><span data-stu-id="1f695-122">Remarks</span></span>  
 <span data-ttu-id="1f695-123">您可以使用 `Group By` 子句來將查詢的結果分成群組。</span><span class="sxs-lookup"><span data-stu-id="1f695-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="1f695-124">群組是根據索引鍵或多個索引鍵所組成的複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1f695-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="1f695-125">與相符索引鍵值相關聯的項目會包含在相同的群組。</span><span class="sxs-lookup"><span data-stu-id="1f695-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="1f695-126">您使用 `aggregateList` 子句的 `Into` 參數和 `Group` 關鍵字來識別用來參考群組的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="1f695-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="1f695-127">您也可以在 `Into` 子句中包含彙總函式來計算群組項目的值。</span><span class="sxs-lookup"><span data-stu-id="1f695-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="1f695-128">如需標準彙總函式的清單，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="1f695-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f695-129">範例</span><span class="sxs-lookup"><span data-stu-id="1f695-129">Example</span></span>  
 <span data-ttu-id="1f695-130">下列程式碼範例根據客戶的位置 (國家/地區) 進行客戶清單的分組，並提供每個群組中的客戶計數。</span><span class="sxs-lookup"><span data-stu-id="1f695-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="1f695-131">結果會依國家/地區名稱排序。</span><span class="sxs-lookup"><span data-stu-id="1f695-131">The results are ordered by country name.</span></span> <span data-ttu-id="1f695-132">群組結果會依城市名稱排序。</span><span class="sxs-lookup"><span data-stu-id="1f695-132">The grouped results are ordered by city name.</span></span>  
  
 <span data-ttu-id="1f695-133">[!code-vb[VbSimpleQuerySamples #&11;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f695-133">[!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f695-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f695-134">See Also</span></span>  
 <span data-ttu-id="1f695-135">[在 Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="1f695-135">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="1f695-136"> [查詢](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="1f695-136"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="1f695-137"> [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="1f695-137"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="1f695-138"> [From 子句](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="1f695-138"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="1f695-139"> [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="1f695-139"> [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="1f695-140"> [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="1f695-140"> [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="1f695-141"> [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="1f695-141"> [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)</span></span>
