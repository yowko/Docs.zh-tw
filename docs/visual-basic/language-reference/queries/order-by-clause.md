---
title: Order By 子句 (Visual Basic)
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
ms.openlocfilehash: 7c60156ee81618530b42d5f61dbcac6f59c4f675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604116"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="83038-102">Order By 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83038-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="83038-103">指定查詢結果的排序次序。</span><span class="sxs-lookup"><span data-stu-id="83038-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83038-104">語法</span><span class="sxs-lookup"><span data-stu-id="83038-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="83038-105">組件</span><span class="sxs-lookup"><span data-stu-id="83038-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="83038-106">必要。</span><span class="sxs-lookup"><span data-stu-id="83038-106">Required.</span></span> <span data-ttu-id="83038-107">一或多個從目前的查詢結果識別欄位如何排序傳回的值。</span><span class="sxs-lookup"><span data-stu-id="83038-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="83038-108">欄位名稱必須以逗號 （，） 分隔。</span><span class="sxs-lookup"><span data-stu-id="83038-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="83038-109">您可以識別每個欄位，為已排序，以遞增或遞減順序，使用`Ascending`或`Descending`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="83038-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="83038-110">如果沒有`Ascending`或`Descending`關鍵字已指定，預設排序次序為遞增。</span><span class="sxs-lookup"><span data-stu-id="83038-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="83038-111">排序次序欄位可以從左到右的優先順序。</span><span class="sxs-lookup"><span data-stu-id="83038-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83038-112">備註</span><span class="sxs-lookup"><span data-stu-id="83038-112">Remarks</span></span>  
 <span data-ttu-id="83038-113">您可以使用`Order By`子句來排序查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="83038-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="83038-114">`Order By`子句只能排序結果，根據目前範圍的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="83038-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="83038-115">例如，`Select`子句會導入新範圍與新的反覆項目變數的查詢運算式中針對該領域。</span><span class="sxs-lookup"><span data-stu-id="83038-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="83038-116">範圍變數之前定義`Select`在查詢中的子句之後沒有`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="83038-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="83038-117">因此，如果您想要排序您的結果來依欄位中都沒有`Select`子句，您必須將`Order By`子句之前`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="83038-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="83038-118">一個範例說明時，您就必須執行這項操作，當您想要排序查詢不會傳回結果的一部分的欄位。</span><span class="sxs-lookup"><span data-stu-id="83038-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="83038-119">遞增和遞減順序的欄位取決於實作<xref:System.IComparable>欄位的資料類型的介面。</span><span class="sxs-lookup"><span data-stu-id="83038-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="83038-120">如果資料類型未實作<xref:System.IComparable>介面，在排序次序會被忽略。</span><span class="sxs-lookup"><span data-stu-id="83038-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83038-121">範例</span><span class="sxs-lookup"><span data-stu-id="83038-121">Example</span></span>  
 <span data-ttu-id="83038-122">下列查詢運算式使用`From`子句來宣告範圍變數`book`如`books`集合。</span><span class="sxs-lookup"><span data-stu-id="83038-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="83038-123">`Order By`子句依照依遞增順序 （預設值） 的價格排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="83038-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="83038-124">使用相同的價格會依標題以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="83038-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="83038-125">`Select`子句選取`Title`和`Price`屬性作為查詢所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="83038-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="83038-126">範例</span><span class="sxs-lookup"><span data-stu-id="83038-126">Example</span></span>  
 <span data-ttu-id="83038-127">下列查詢運算式使用`Order By`子句來排序查詢結果以遞減順序的價格。</span><span class="sxs-lookup"><span data-stu-id="83038-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="83038-128">使用相同的價格會依標題以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="83038-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="83038-129">範例</span><span class="sxs-lookup"><span data-stu-id="83038-129">Example</span></span>  
 <span data-ttu-id="83038-130">下列查詢運算式使用`Select`子句來選取書名、 price、 發行日期，以及撰寫。</span><span class="sxs-lookup"><span data-stu-id="83038-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="83038-131">然後填入`Title`， `Price`， `PublishDate`，和`Author`新範圍的範圍變數的欄位。</span><span class="sxs-lookup"><span data-stu-id="83038-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="83038-132">`Order By`子句排序新的範圍變數的作者名稱、 書籍標題和價格。</span><span class="sxs-lookup"><span data-stu-id="83038-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="83038-133">每個資料行排序 （遞增） 的預設順序。</span><span class="sxs-lookup"><span data-stu-id="83038-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="83038-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83038-134">See Also</span></span>  
 [<span data-ttu-id="83038-135">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="83038-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="83038-136">查詢</span><span class="sxs-lookup"><span data-stu-id="83038-136">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="83038-137">Select 子句</span><span class="sxs-lookup"><span data-stu-id="83038-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="83038-138">From 子句</span><span class="sxs-lookup"><span data-stu-id="83038-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
