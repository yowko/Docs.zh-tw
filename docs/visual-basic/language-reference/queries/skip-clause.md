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
ms.openlocfilehash: db2d79596895505ddaa7778e831082a94c7ad44e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945245"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="ef25c-102">Skip 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef25c-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="ef25c-103">略過集合中指定數目的項目，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="ef25c-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef25c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef25c-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="ef25c-105">組件</span><span class="sxs-lookup"><span data-stu-id="ef25c-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="ef25c-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="ef25c-106">Required.</span></span> <span data-ttu-id="ef25c-107">值或評估運算式，以略過序列的項目數目。</span><span class="sxs-lookup"><span data-stu-id="ef25c-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef25c-108">備註</span><span class="sxs-lookup"><span data-stu-id="ef25c-108">Remarks</span></span>  
 <span data-ttu-id="ef25c-109">`Skip`子句會使查詢，以略過的結果清單開頭的項目，並傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="ef25c-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="ef25c-110">略過的項目數由`count`參數。</span><span class="sxs-lookup"><span data-stu-id="ef25c-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="ef25c-111">您可以使用`Skip`子句搭配`Take`子句傳回的資料範圍查詢的任何區段。</span><span class="sxs-lookup"><span data-stu-id="ef25c-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="ef25c-112">若要這樣做，請將傳遞到的範圍內的第一個元素的索引`Skip`子句和範圍的大小`Take`子句。</span><span class="sxs-lookup"><span data-stu-id="ef25c-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="ef25c-113">當您使用`Skip`查詢中的子句，您可能也需要確定結果傳回的順序，將會啟用`Skip`子句來略過所要的結果。</span><span class="sxs-lookup"><span data-stu-id="ef25c-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="ef25c-114">如需有關如何排序查詢結果的詳細資訊，請參閱 < [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="ef25c-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="ef25c-115">您可以使用`SkipWhile`子句來指定特定項目會忽略，根據提供的條件。</span><span class="sxs-lookup"><span data-stu-id="ef25c-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef25c-116">範例</span><span class="sxs-lookup"><span data-stu-id="ef25c-116">Example</span></span>  
 <span data-ttu-id="ef25c-117">下列程式碼範例會使用`Skip`子句搭配`Take`子句，以從查詢頁面中傳回資料。</span><span class="sxs-lookup"><span data-stu-id="ef25c-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="ef25c-118">`GetCustomers`函式會使用`Skip`子句來略過清單中的客戶，直到提供開始索引值，並使用`Take`子句傳回的客戶，從該索引值開始的頁面。</span><span class="sxs-lookup"><span data-stu-id="ef25c-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ef25c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef25c-119">See also</span></span>

- [<span data-ttu-id="ef25c-120">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="ef25c-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ef25c-121">查詢</span><span class="sxs-lookup"><span data-stu-id="ef25c-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ef25c-122">Select 子句</span><span class="sxs-lookup"><span data-stu-id="ef25c-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="ef25c-123">From 子句</span><span class="sxs-lookup"><span data-stu-id="ef25c-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ef25c-124">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="ef25c-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="ef25c-125">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="ef25c-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="ef25c-126">Take 子句</span><span class="sxs-lookup"><span data-stu-id="ef25c-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
