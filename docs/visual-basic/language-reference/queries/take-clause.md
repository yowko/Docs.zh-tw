---
title: Take 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: f2377d8d1635912885a310b2b0429a6a00083b47
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869676"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="291cd-102">Take 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="291cd-102">Take Clause (Visual Basic)</span></span>

<span data-ttu-id="291cd-103">從集合開頭傳回指定數目的連續項目。</span><span class="sxs-lookup"><span data-stu-id="291cd-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291cd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="291cd-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="291cd-105">組件</span><span class="sxs-lookup"><span data-stu-id="291cd-105">Parts</span></span>  

 `count`  
 <span data-ttu-id="291cd-106">必要。</span><span class="sxs-lookup"><span data-stu-id="291cd-106">Required.</span></span> <span data-ttu-id="291cd-107">值或運算式，這個值會評估為要傳回之序列的元素數。</span><span class="sxs-lookup"><span data-stu-id="291cd-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="291cd-108">備註</span><span class="sxs-lookup"><span data-stu-id="291cd-108">Remarks</span></span>  

 <span data-ttu-id="291cd-109">`Take`子句會讓查詢從結果清單的開頭包含指定數目的連續元素。</span><span class="sxs-lookup"><span data-stu-id="291cd-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="291cd-110">要包含的元素數目是由參數所指定 `count` 。</span><span class="sxs-lookup"><span data-stu-id="291cd-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="291cd-111">您可以使用 `Take` 子句搭配 `Skip` 子句，從查詢的任何區段傳回資料範圍。</span><span class="sxs-lookup"><span data-stu-id="291cd-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="291cd-112">若要這樣做，請將範圍第一個元素的索引傳遞給子句，並將範圍的大小傳遞給 `Skip` `Take` 子句。</span><span class="sxs-lookup"><span data-stu-id="291cd-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="291cd-113">在此情況下， `Take` 子句必須在子句之後指定 `Skip` 。</span><span class="sxs-lookup"><span data-stu-id="291cd-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="291cd-114">當您 `Take` 在查詢中使用子句時，您可能也需要確保結果會以可讓 `Take` 子句包含所需結果的順序傳回。</span><span class="sxs-lookup"><span data-stu-id="291cd-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="291cd-115">如需排序查詢結果的詳細資訊，請參閱 [Order By 子句](order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="291cd-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="291cd-116">您可以使用 `TakeWhile` 子句來指定只傳回特定的元素，視提供的條件而定。</span><span class="sxs-lookup"><span data-stu-id="291cd-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="291cd-117">範例</span><span class="sxs-lookup"><span data-stu-id="291cd-117">Example</span></span>  

 <span data-ttu-id="291cd-118">下列程式碼範例會將 `Take` 子句和子句一起使用， `Skip` 以從頁面中的查詢傳回資料。</span><span class="sxs-lookup"><span data-stu-id="291cd-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="291cd-119">GetCustomers 函式會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值為止，並使用 `Take` 子句傳回從該索引值開始之客戶的頁面。</span><span class="sxs-lookup"><span data-stu-id="291cd-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="291cd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="291cd-120">See also</span></span>

- [<span data-ttu-id="291cd-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="291cd-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="291cd-122">查詢</span><span class="sxs-lookup"><span data-stu-id="291cd-122">Queries</span></span>](index.md)
- [<span data-ttu-id="291cd-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="291cd-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="291cd-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="291cd-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="291cd-125">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="291cd-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="291cd-126">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="291cd-126">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="291cd-127">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="291cd-127">Skip Clause</span></span>](skip-clause.md)
