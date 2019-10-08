---
title: Skip 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004774"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="8df75-102">Skip 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8df75-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="8df75-103">略過集合中指定數目的項目，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="8df75-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8df75-104">語法</span><span class="sxs-lookup"><span data-stu-id="8df75-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="8df75-105">組件</span><span class="sxs-lookup"><span data-stu-id="8df75-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="8df75-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="8df75-106">Required.</span></span> <span data-ttu-id="8df75-107">值或運算式，評估為要略過的序列元素數目。</span><span class="sxs-lookup"><span data-stu-id="8df75-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8df75-108">備註</span><span class="sxs-lookup"><span data-stu-id="8df75-108">Remarks</span></span>  
 <span data-ttu-id="8df75-109">@No__t 0 子句會使查詢略過結果清單開頭的專案，並傳回剩餘的元素。</span><span class="sxs-lookup"><span data-stu-id="8df75-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="8df75-110">要略過的元素數目是由 `count` 參數所識別。</span><span class="sxs-lookup"><span data-stu-id="8df75-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="8df75-111">您可以使用 `Skip` 子句搭配 `Take` 子句，從查詢的任何區段傳回資料範圍。</span><span class="sxs-lookup"><span data-stu-id="8df75-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="8df75-112">若要這麼做，請將範圍的第一個元素的索引傳遞至 `Skip` 子句，並將範圍的大小傳遞給 `Take` 子句。</span><span class="sxs-lookup"><span data-stu-id="8df75-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="8df75-113">當您在查詢中使用 `Skip` 子句時，您可能也需要確保會以可讓 @no__t 1 子句略過預期結果的順序傳回結果。</span><span class="sxs-lookup"><span data-stu-id="8df75-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="8df75-114">如需排序查詢結果的詳細資訊，請參閱[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="8df75-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="8df75-115">視提供的條件而定，您可以使用 `SkipWhile` 子句來指定只忽略特定元素。</span><span class="sxs-lookup"><span data-stu-id="8df75-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8df75-116">範例</span><span class="sxs-lookup"><span data-stu-id="8df75-116">Example</span></span>  
 <span data-ttu-id="8df75-117">下列程式碼範例會使用 `Skip` 子句搭配 `Take` 子句，以從頁面中的查詢傳回資料。</span><span class="sxs-lookup"><span data-stu-id="8df75-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="8df75-118">@No__t-0 函式會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值，並使用 `Take` 子句來傳回從該索引值開始的客戶頁面。</span><span class="sxs-lookup"><span data-stu-id="8df75-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8df75-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8df75-119">See also</span></span>

- [<span data-ttu-id="8df75-120">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="8df75-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="8df75-121">查詢</span><span class="sxs-lookup"><span data-stu-id="8df75-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="8df75-122">Select 子句</span><span class="sxs-lookup"><span data-stu-id="8df75-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="8df75-123">From 子句</span><span class="sxs-lookup"><span data-stu-id="8df75-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="8df75-124">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="8df75-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="8df75-125">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="8df75-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="8df75-126">Take 子句</span><span class="sxs-lookup"><span data-stu-id="8df75-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
