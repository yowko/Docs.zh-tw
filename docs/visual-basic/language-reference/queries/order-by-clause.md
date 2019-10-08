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
ms.openlocfilehash: f8ee46b12e84f99629c3a92057fc3a7bb8a3c2e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004948"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="7a0b7-102">Order By 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a0b7-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="7a0b7-103">指定查詢結果的排序次序。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a0b7-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="7a0b7-105">組件</span><span class="sxs-lookup"><span data-stu-id="7a0b7-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="7a0b7-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-106">Required.</span></span> <span data-ttu-id="7a0b7-107">目前查詢結果中的一或多個欄位，可識別如何排序傳回的值。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="7a0b7-108">功能變數名稱必須以逗號（，）分隔。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="7a0b7-109">您可以使用 `Ascending` 或 `Descending` 關鍵字，以遞增或遞減順序將每個欄位識別為排序。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="7a0b7-110">如果未指定 `Ascending` 或 `Descending` 關鍵字，則預設排序次序為遞增。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="7a0b7-111">排序次序欄位的優先順序是由左至右。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a0b7-112">備註</span><span class="sxs-lookup"><span data-stu-id="7a0b7-112">Remarks</span></span>  
 <span data-ttu-id="7a0b7-113">您可以使用 `Order By` 子句來排序查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="7a0b7-114">@No__t-0 子句只能根據目前範圍的範圍變數來排序結果。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="7a0b7-115">例如，`Select` 子句會在查詢運算式中引進新的範圍，其中包含該範圍的新反復專案變數。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="7a0b7-116">在查詢中的 `Select` 子句之前定義的範圍變數，在 `Select` 子句之後無法使用。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="7a0b7-117">因此，如果您想要依據 `Select` 子句中無法使用的欄位來排序結果，則必須將 `Order By` 子句放在 `Select` 子句之前。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="7a0b7-118">當您需要執行這項操作的其中一個範例，就是當您想要依欄位排序查詢，而不會在結果中傳回。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="7a0b7-119">欄位的遞增和遞減順序是由欄位之資料類型的 @no__t 0 介面的執行所決定。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="7a0b7-120">如果資料類型不會執行 <xref:System.IComparable> 介面，則會忽略排序次序。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a0b7-121">範例</span><span class="sxs-lookup"><span data-stu-id="7a0b7-121">Example</span></span>  
 <span data-ttu-id="7a0b7-122">下列查詢運算式會使用 `From` 子句，針對 @no__t 2 集合宣告範圍變數 `book`。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="7a0b7-123">@No__t-0 子句會依價格以遞增順序排序查詢結果（預設值）。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="7a0b7-124">具有相同價格的書籍會依標題以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="7a0b7-125">@No__t-0 子句會選取 `Title` 和 @no__t 2 屬性做為查詢所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="7a0b7-126">範例</span><span class="sxs-lookup"><span data-stu-id="7a0b7-126">Example</span></span>  
 <span data-ttu-id="7a0b7-127">下列查詢運算式會使用 `Order By` 子句，依價格遞減的順序來排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="7a0b7-128">具有相同價格的書籍會依標題以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="7a0b7-129">範例</span><span class="sxs-lookup"><span data-stu-id="7a0b7-129">Example</span></span>  
 <span data-ttu-id="7a0b7-130">下列查詢運算式會使用 `Select` 子句來選取書籍標題、價格、發行日期和作者。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="7a0b7-131">然後，它會在新範圍的範圍變數中，填入 `Title`、`Price`、@no__t 2 和 @no__t 3 欄位。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="7a0b7-132">@No__t-0 子句會依作者名稱、書名和價格來排序新的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="7a0b7-133">每個資料行都會以預設順序排序（遞增）。</span><span class="sxs-lookup"><span data-stu-id="7a0b7-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="7a0b7-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a0b7-134">See also</span></span>

- [<span data-ttu-id="7a0b7-135">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="7a0b7-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7a0b7-136">查詢</span><span class="sxs-lookup"><span data-stu-id="7a0b7-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="7a0b7-137">Select 子句</span><span class="sxs-lookup"><span data-stu-id="7a0b7-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="7a0b7-138">From 子句</span><span class="sxs-lookup"><span data-stu-id="7a0b7-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
