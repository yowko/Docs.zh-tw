---
title: Take 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 32a4c7fd7f1e2f6fe640f3f53f15579f014759d5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004710"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="8eb7c-102">Take 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8eb7c-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="8eb7c-103">從集合開頭傳回指定數目的連續項目。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8eb7c-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="8eb7c-105">組件</span><span class="sxs-lookup"><span data-stu-id="8eb7c-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="8eb7c-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-106">Required.</span></span> <span data-ttu-id="8eb7c-107">值或運算式，評估為要傳回之序列的專案數。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eb7c-108">備註</span><span class="sxs-lookup"><span data-stu-id="8eb7c-108">Remarks</span></span>  
 <span data-ttu-id="8eb7c-109">@No__t-0 子句會使查詢在結果清單的開頭包含指定數目的連續元素。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="8eb7c-110">要包含的元素數目是由 `count` 參數所指定。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="8eb7c-111">您可以使用 `Take` 子句搭配 `Skip` 子句，從查詢的任何區段傳回資料範圍。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="8eb7c-112">若要這麼做，請將範圍的第一個元素的索引傳遞至 `Skip` 子句，並將範圍的大小傳遞給 `Take` 子句。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="8eb7c-113">在此情況下，必須在 `Skip` 子句之後指定 `Take` 子句。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="8eb7c-114">當您在查詢中使用 `Take` 子句時，您可能也需要確保會以可讓 `Take` 子句包含預期結果的順序傳回結果。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="8eb7c-115">如需排序查詢結果的詳細資訊，請參閱[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="8eb7c-116">視提供的條件而定，您可以使用 `TakeWhile` 子句來指定只傳回特定的元素。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eb7c-117">範例</span><span class="sxs-lookup"><span data-stu-id="8eb7c-117">Example</span></span>  
 <span data-ttu-id="8eb7c-118">下列程式碼範例會使用 `Take` 子句搭配 `Skip` 子句，以從頁面中的查詢傳回資料。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="8eb7c-119">GetCustomers 函式會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值，並使用 `Take` 子句來傳回從該索引值開始的客戶頁面。</span><span class="sxs-lookup"><span data-stu-id="8eb7c-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8eb7c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eb7c-120">See also</span></span>

- [<span data-ttu-id="8eb7c-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="8eb7c-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="8eb7c-122">查詢</span><span class="sxs-lookup"><span data-stu-id="8eb7c-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="8eb7c-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="8eb7c-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="8eb7c-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="8eb7c-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="8eb7c-125">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="8eb7c-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="8eb7c-126">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="8eb7c-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="8eb7c-127">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="8eb7c-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
