---
title: Where 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359537"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="ae7f5-102">Where 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae7f5-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="ae7f5-103">指定查詢的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae7f5-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="ae7f5-105">組件</span><span class="sxs-lookup"><span data-stu-id="ae7f5-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="ae7f5-106">必要。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-106">Required.</span></span> <span data-ttu-id="ae7f5-107">運算式，判斷集合中目前專案的值是否包含在輸出集合中。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="ae7f5-108">運算式必須評估為 `Boolean` 值或對等的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="ae7f5-109">如果條件評估為 `True` ，則專案會包含在查詢結果中，否則會從查詢結果中排除元素。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae7f5-110">備註</span><span class="sxs-lookup"><span data-stu-id="ae7f5-110">Remarks</span></span>  
 <span data-ttu-id="ae7f5-111">`Where`子句可讓您只選取符合特定準則的元素來篩選查詢資料。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="ae7f5-112">其值會讓 `Where` 子句評估為的元素 `True` 會包含在查詢結果中，而其他元素則會排除。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="ae7f5-113">子句中使用的運算式 `Where` 必須評估為或的對 `Boolean` 等 `Boolean` ，例如在 `False` 其值為零時評估為的整數。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="ae7f5-114">您可以 `Where` 使用邏輯運算子（例如 `And` 、 `Or` 、 `AndAlso` 、 `OrElse` 、 `Is` 和 `IsNot` ）結合子句中的多個運算式。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="ae7f5-115">根據預設，查詢運算式在存取之前不會進行評估，例如，當資料系結或在迴圈中反復執行時 `For` 。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="ae7f5-116">因此，在 `Where` 存取查詢之前，不會評估子句。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="ae7f5-117">如果您在子句中使用的查詢外部有值 `Where` ，請確定在執行查詢時，子句中使用了適當的值 `Where` 。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="ae7f5-118">如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-118">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="ae7f5-119">您可以在子句內呼叫函式 `Where` ，以從集合中目前專案的值執行計算或運算。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="ae7f5-120">呼叫子句中的函式 `Where` 可能會導致查詢在定義時立即執行，而不是存取時。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="ae7f5-121">如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-121">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae7f5-122">範例</span><span class="sxs-lookup"><span data-stu-id="ae7f5-122">Example</span></span>  
 <span data-ttu-id="ae7f5-123">下列查詢運算式會使用 `From` 子句， `cust` 針對集合中的每個物件宣告範圍變數 `Customer` `customers` 。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="ae7f5-124">`Where`子句會使用範圍變數，將輸出限制為來自指定區域的客戶。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="ae7f5-125">`For Each`迴圈會在查詢結果中顯示每個客戶的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="ae7f5-126">範例</span><span class="sxs-lookup"><span data-stu-id="ae7f5-126">Example</span></span>  
 <span data-ttu-id="ae7f5-127">下列範例會 `And` `Or` 在子句中使用和邏輯運算子 `Where` 。</span><span class="sxs-lookup"><span data-stu-id="ae7f5-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="ae7f5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae7f5-128">See also</span></span>

- [<span data-ttu-id="ae7f5-129">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="ae7f5-129">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ae7f5-130">查詢</span><span class="sxs-lookup"><span data-stu-id="ae7f5-130">Queries</span></span>](index.md)
- [<span data-ttu-id="ae7f5-131">From 子句</span><span class="sxs-lookup"><span data-stu-id="ae7f5-131">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="ae7f5-132">Select 子句</span><span class="sxs-lookup"><span data-stu-id="ae7f5-132">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="ae7f5-133">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="ae7f5-133">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
