---
title: Order By 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 05fa720237f4b0185b5c07217362c99b5dbf4303
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869785"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="85930-102">Order By 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85930-102">Order By Clause (Visual Basic)</span></span>

<span data-ttu-id="85930-103">指定查詢結果的排序次序。</span><span class="sxs-lookup"><span data-stu-id="85930-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85930-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="85930-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="85930-105">組件</span><span class="sxs-lookup"><span data-stu-id="85930-105">Parts</span></span>  

 `orderExp1`  
 <span data-ttu-id="85930-106">必要。</span><span class="sxs-lookup"><span data-stu-id="85930-106">Required.</span></span> <span data-ttu-id="85930-107">目前查詢結果中的一或多個欄位，可識別如何排序傳回值。</span><span class="sxs-lookup"><span data-stu-id="85930-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="85930-108">功能變數名稱必須以逗號分隔 (，) 。</span><span class="sxs-lookup"><span data-stu-id="85930-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="85930-109">您可以使用或關鍵字，以遞增或遞減順序來識別每個 `Ascending` 欄位 `Descending` 。</span><span class="sxs-lookup"><span data-stu-id="85930-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="85930-110">如果未 `Ascending` `Descending` 指定或關鍵字，則預設排序次序為遞增。</span><span class="sxs-lookup"><span data-stu-id="85930-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="85930-111">排序次序欄位的優先順序是由左至右。</span><span class="sxs-lookup"><span data-stu-id="85930-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85930-112">備註</span><span class="sxs-lookup"><span data-stu-id="85930-112">Remarks</span></span>  

 <span data-ttu-id="85930-113">您可以使用 `Order By` 子句來排序查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="85930-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="85930-114">`Order By`子句只能根據目前範圍的範圍變數來排序結果。</span><span class="sxs-lookup"><span data-stu-id="85930-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="85930-115">例如， `Select` 子句會在查詢運算式中引入新的範圍，並在該範圍內加入新的反覆運算變數。</span><span class="sxs-lookup"><span data-stu-id="85930-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="85930-116">在查詢中的子句之前定義的範圍變數 `Select` 無法在子句之後使用 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="85930-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="85930-117">因此，如果您想要依子句中不提供的欄位來排序結果 `Select` ，則必須將子句放在 `Order By` `Select` 子句之前。</span><span class="sxs-lookup"><span data-stu-id="85930-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="85930-118">當您想要依未傳回為結果一部分的欄位來排序查詢時，其中一個範例就是。</span><span class="sxs-lookup"><span data-stu-id="85930-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="85930-119">欄位的遞增和遞減順序是由 <xref:System.IComparable> 欄位資料類型的介面實作為決定。</span><span class="sxs-lookup"><span data-stu-id="85930-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="85930-120">如果資料類型不會執行 <xref:System.IComparable> 介面，則會忽略排序次序。</span><span class="sxs-lookup"><span data-stu-id="85930-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85930-121">範例</span><span class="sxs-lookup"><span data-stu-id="85930-121">Example</span></span>  

 <span data-ttu-id="85930-122">下列查詢運算式使用 `From` 子句來宣告集合的範圍變數 `book` `books` 。</span><span class="sxs-lookup"><span data-stu-id="85930-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="85930-123">子句會將 `Order By` 查詢結果依價格以遞增順序排序 (預設) 。</span><span class="sxs-lookup"><span data-stu-id="85930-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="85930-124">具有相同價格的書籍會依標題以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="85930-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="85930-125">`Select`子句會選取 `Title` 和 `Price` 屬性做為查詢所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="85930-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="85930-126">範例</span><span class="sxs-lookup"><span data-stu-id="85930-126">Example</span></span>  

 <span data-ttu-id="85930-127">下列查詢運算式會使用 `Order By` 子句，依價格的遞減順序來排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="85930-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="85930-128">具有相同價格的書籍會依標題以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="85930-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="85930-129">範例</span><span class="sxs-lookup"><span data-stu-id="85930-129">Example</span></span>  

 <span data-ttu-id="85930-130">下列查詢運算式使用 `Select` 子句來選取書籍標題、價格、發行日期和作者。</span><span class="sxs-lookup"><span data-stu-id="85930-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="85930-131">然後，它會 `Title` `Price` `PublishDate` `Author` 針對新的範圍填入範圍變數的、、和欄位。</span><span class="sxs-lookup"><span data-stu-id="85930-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="85930-132">`Order By`子句會依作者名稱、書籍標題和價格來排序新的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="85930-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="85930-133">每個資料行都會依照預設順序排序 (遞增) 。</span><span class="sxs-lookup"><span data-stu-id="85930-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="85930-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85930-134">See also</span></span>

- [<span data-ttu-id="85930-135">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="85930-135">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="85930-136">查詢</span><span class="sxs-lookup"><span data-stu-id="85930-136">Queries</span></span>](index.md)
- [<span data-ttu-id="85930-137">Select 子句</span><span class="sxs-lookup"><span data-stu-id="85930-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="85930-138">From 子句</span><span class="sxs-lookup"><span data-stu-id="85930-138">From Clause</span></span>](from-clause.md)
