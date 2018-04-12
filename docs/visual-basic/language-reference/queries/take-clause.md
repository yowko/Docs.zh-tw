---
title: Take 子句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee289a24c15226126a526af116ed53b4a9055b35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="8af0d-102">Take 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8af0d-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="8af0d-103">從集合開頭傳回指定數目的連續項目。</span><span class="sxs-lookup"><span data-stu-id="8af0d-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="8af0d-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="8af0d-105">組件</span><span class="sxs-lookup"><span data-stu-id="8af0d-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="8af0d-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="8af0d-106">Required.</span></span> <span data-ttu-id="8af0d-107">值或評估運算式傳回序列的項目數目。</span><span class="sxs-lookup"><span data-stu-id="8af0d-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8af0d-108">備註</span><span class="sxs-lookup"><span data-stu-id="8af0d-108">Remarks</span></span>  
 <span data-ttu-id="8af0d-109">`Take`子句，會使查詢包含連續的項目，從結果清單的開頭指定的數目。</span><span class="sxs-lookup"><span data-stu-id="8af0d-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="8af0d-110">所指定要包含的項目數`count`參數。</span><span class="sxs-lookup"><span data-stu-id="8af0d-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="8af0d-111">您可以使用`Take`子句搭配`Skip`子句傳回的資料範圍查詢的任何區段。</span><span class="sxs-lookup"><span data-stu-id="8af0d-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="8af0d-112">若要這樣做，傳遞到範圍內的第一個元素索引`Skip`子句和範圍的大小`Take`子句。</span><span class="sxs-lookup"><span data-stu-id="8af0d-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="8af0d-113">在此情況下，`Take`子句必須指定後面`Skip`子句。</span><span class="sxs-lookup"><span data-stu-id="8af0d-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="8af0d-114">當您使用`Take`子句的查詢中，您可能也需要確保結果會傳回順序將會啟用`Take`子句，以包含所要的結果。</span><span class="sxs-lookup"><span data-stu-id="8af0d-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="8af0d-115">如需排序查詢結果的詳細資訊，請參閱[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="8af0d-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="8af0d-116">您可以使用`TakeWhile`子句來指定傳回特定項目，根據提供的條件。</span><span class="sxs-lookup"><span data-stu-id="8af0d-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af0d-117">範例</span><span class="sxs-lookup"><span data-stu-id="8af0d-117">Example</span></span>  
 <span data-ttu-id="8af0d-118">下列程式碼範例使用`Take`子句搭配`Skip`子句，從頁面中的查詢傳回資料。</span><span class="sxs-lookup"><span data-stu-id="8af0d-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="8af0d-119">GetCustomers 函式使用`Skip`子句來略過清單中的客戶，直到提供開始索引值，並使用`Take`子句傳回的客戶，從該索引值開始的頁面。</span><span class="sxs-lookup"><span data-stu-id="8af0d-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8af0d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8af0d-120">See Also</span></span>  
 [<span data-ttu-id="8af0d-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="8af0d-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="8af0d-122">查詢</span><span class="sxs-lookup"><span data-stu-id="8af0d-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="8af0d-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="8af0d-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="8af0d-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="8af0d-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="8af0d-125">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="8af0d-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="8af0d-126">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="8af0d-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="8af0d-127">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="8af0d-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
