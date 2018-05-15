---
title: Where 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 0b61a52a366fb37a0834c9223bc8b7f099354d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="64e38-102">Where 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64e38-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="64e38-103">指定查詢的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="64e38-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e38-104">語法</span><span class="sxs-lookup"><span data-stu-id="64e38-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="64e38-105">組件</span><span class="sxs-lookup"><span data-stu-id="64e38-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="64e38-106">必要。</span><span class="sxs-lookup"><span data-stu-id="64e38-106">Required.</span></span> <span data-ttu-id="64e38-107">決定輸出集合中是否包含在集合中目前的項目值的運算式。</span><span class="sxs-lookup"><span data-stu-id="64e38-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="64e38-108">運算式必須評估為`Boolean`值或相當的`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="64e38-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="64e38-109">如果條件評估為`True`、 項目包含查詢結果中; 否則項目從查詢結果中排除。</span><span class="sxs-lookup"><span data-stu-id="64e38-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64e38-110">備註</span><span class="sxs-lookup"><span data-stu-id="64e38-110">Remarks</span></span>  
 <span data-ttu-id="64e38-111">`Where`子句可讓您選取符合特定準則的項目來篩選查詢資料。</span><span class="sxs-lookup"><span data-stu-id="64e38-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="64e38-112">項目，其值會導致`Where`子句評估為`True`隨附在查詢結果; 會排除其他項目。</span><span class="sxs-lookup"><span data-stu-id="64e38-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="64e38-113">使用中的運算式`Where`子句必須評估為`Boolean`或相當的`Boolean`，例如評估為整數`False`當其值是零。</span><span class="sxs-lookup"><span data-stu-id="64e38-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="64e38-114">您可以結合多個運算式中的`Where`子句使用邏輯運算子，像是`And`， `Or`， `AndAlso`， `OrElse`， `Is`，和`IsNot`。</span><span class="sxs-lookup"><span data-stu-id="64e38-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="64e38-115">根據預設，查詢運算式才會評估存取 — 比方說，當它們是資料繫結或中逐一`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="64e38-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="64e38-116">如此一來，`Where`存取查詢之前，將不評估子句。</span><span class="sxs-lookup"><span data-stu-id="64e38-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="64e38-117">如果您有外部查詢中所使用的值`Where`子句，確定適當的值用於`Where`子句在執行查詢的時間。</span><span class="sxs-lookup"><span data-stu-id="64e38-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="64e38-118">如需有關查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="64e38-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="64e38-119">您可以呼叫函式內`Where`子句來執行計算或作業的值從集合中目前的項目。</span><span class="sxs-lookup"><span data-stu-id="64e38-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="64e38-120">呼叫函式`Where`子句可能會造成當它定義而不是存取時，立即執行查詢。</span><span class="sxs-lookup"><span data-stu-id="64e38-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="64e38-121">如需有關查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="64e38-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64e38-122">範例</span><span class="sxs-lookup"><span data-stu-id="64e38-122">Example</span></span>  
 <span data-ttu-id="64e38-123">下列查詢運算式使用`From`子句來宣告範圍變數`cust`每個`Customer`物件存放至`customers`集合。</span><span class="sxs-lookup"><span data-stu-id="64e38-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="64e38-124">`Where`子句來限制輸出給客戶，從指定的地區中使用的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="64e38-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="64e38-125">`For Each`迴圈會顯示查詢結果中的每個客戶的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="64e38-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="64e38-126">範例</span><span class="sxs-lookup"><span data-stu-id="64e38-126">Example</span></span>  
 <span data-ttu-id="64e38-127">下列範例會使用`And`和`Or`的邏輯運算子`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="64e38-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="64e38-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64e38-128">See Also</span></span>  
 [<span data-ttu-id="64e38-129">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="64e38-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="64e38-130">查詢</span><span class="sxs-lookup"><span data-stu-id="64e38-130">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="64e38-131">From 子句</span><span class="sxs-lookup"><span data-stu-id="64e38-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="64e38-132">Select 子句</span><span class="sxs-lookup"><span data-stu-id="64e38-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="64e38-133">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="64e38-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
