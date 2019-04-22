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
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835007"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="bf059-102">Order By 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf059-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="bf059-103">指定查詢結果的排序次序。</span><span class="sxs-lookup"><span data-stu-id="bf059-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf059-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf059-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="bf059-105">組件</span><span class="sxs-lookup"><span data-stu-id="bf059-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="bf059-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="bf059-106">Required.</span></span> <span data-ttu-id="bf059-107">一或多個欄位從目前的查詢結果，找出如何排序傳回的值。</span><span class="sxs-lookup"><span data-stu-id="bf059-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="bf059-108">欄位名稱必須以逗號 （，） 分隔。</span><span class="sxs-lookup"><span data-stu-id="bf059-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="bf059-109">您可以識別每個欄位，因為依照遞增或遞減順序，使用`Ascending`或`Descending`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bf059-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="bf059-110">如果沒有`Ascending`或`Descending`關鍵字指定，則預設排序順序為遞增。</span><span class="sxs-lookup"><span data-stu-id="bf059-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="bf059-111">排序次序欄位可以從左到右的優先順序。</span><span class="sxs-lookup"><span data-stu-id="bf059-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf059-112">備註</span><span class="sxs-lookup"><span data-stu-id="bf059-112">Remarks</span></span>  
 <span data-ttu-id="bf059-113">您可以使用`Order By`子句來排序查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="bf059-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="bf059-114">`Order By`子句只能排序結果，根據目前的範圍的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="bf059-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="bf059-115">比方說，`Select`子句會導入該範圍與新的反覆項目變數的查詢運算式中的新範圍。</span><span class="sxs-lookup"><span data-stu-id="bf059-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="bf059-116">範圍之前定義的變數`Select`查詢中的子句之後沒有`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="bf059-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="bf059-117">因此，如果您想要排序的欄位，不適用於您結果`Select`子句中，您必須在放置`Order By`子句之前`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="bf059-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="bf059-118">一個您想要排序您的查詢不會傳回為結果一部分的欄位時，當您必須執行這項操作的範例。</span><span class="sxs-lookup"><span data-stu-id="bf059-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="bf059-119">遞增和遞減順序，欄位是由決定藉由實作<xref:System.IComparable>欄位的資料類型的介面。</span><span class="sxs-lookup"><span data-stu-id="bf059-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="bf059-120">如果資料類型未實作<xref:System.IComparable>介面，排序次序會被忽略。</span><span class="sxs-lookup"><span data-stu-id="bf059-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf059-121">範例</span><span class="sxs-lookup"><span data-stu-id="bf059-121">Example</span></span>  
 <span data-ttu-id="bf059-122">下列查詢的運算式用法`From`子句來宣告範圍變數`book`如`books`集合。</span><span class="sxs-lookup"><span data-stu-id="bf059-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="bf059-123">`Order By`子句排序查詢結果，以遞增順序 （預設值） 的定價。</span><span class="sxs-lookup"><span data-stu-id="bf059-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="bf059-124">活頁簿相同的價格會依標題，依遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="bf059-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="bf059-125">`Select`子句選取`Title`和`Price`查詢所傳回的值的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf059-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="bf059-126">範例</span><span class="sxs-lookup"><span data-stu-id="bf059-126">Example</span></span>  
 <span data-ttu-id="bf059-127">下列查詢運算式使用`Order By`子句來排序查詢結果以遞減順序的價格。</span><span class="sxs-lookup"><span data-stu-id="bf059-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="bf059-128">活頁簿相同的價格會依標題，依遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="bf059-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="bf059-129">範例</span><span class="sxs-lookup"><span data-stu-id="bf059-129">Example</span></span>  
 <span data-ttu-id="bf059-130">下列查詢運算式使用`Select`選取的書籍標題、 價格、 發行日期，以及撰寫的子句。</span><span class="sxs-lookup"><span data-stu-id="bf059-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="bf059-131">它接著會填入`Title`， `Price`， `PublishDate`，和`Author`新範圍的範圍變數的欄位。</span><span class="sxs-lookup"><span data-stu-id="bf059-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="bf059-132">`Order By`子句排序新的範圍變數的作者名稱、 書名和價格。</span><span class="sxs-lookup"><span data-stu-id="bf059-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="bf059-133">每個資料行排序 （遞增） 的預設順序。</span><span class="sxs-lookup"><span data-stu-id="bf059-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="bf059-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf059-134">See also</span></span>

- [<span data-ttu-id="bf059-135">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="bf059-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="bf059-136">查詢</span><span class="sxs-lookup"><span data-stu-id="bf059-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="bf059-137">Select 子句</span><span class="sxs-lookup"><span data-stu-id="bf059-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="bf059-138">From 子句</span><span class="sxs-lookup"><span data-stu-id="bf059-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
