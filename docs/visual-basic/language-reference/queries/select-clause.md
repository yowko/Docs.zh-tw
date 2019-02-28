---
title: Select 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 591fa664c56383cf8a7b3492e524a9738e065f8a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979602"
---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="f5de5-102">Select 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5de5-102">Select Clause (Visual Basic)</span></span>
<span data-ttu-id="f5de5-103">定義查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="f5de5-103">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5de5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5de5-104">Syntax</span></span>  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="f5de5-105">組件</span><span class="sxs-lookup"><span data-stu-id="f5de5-105">Parts</span></span>  
 `var1`  
 <span data-ttu-id="f5de5-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f5de5-106">Optional.</span></span> <span data-ttu-id="f5de5-107">可用來參考的資料行運算式結果的別名。</span><span class="sxs-lookup"><span data-stu-id="f5de5-107">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="f5de5-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="f5de5-108">Required.</span></span> <span data-ttu-id="f5de5-109">要傳回查詢結果中的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="f5de5-109">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5de5-110">備註</span><span class="sxs-lookup"><span data-stu-id="f5de5-110">Remarks</span></span>  
 <span data-ttu-id="f5de5-111">您可以使用`Select`子句來定義要從查詢傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="f5de5-111">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="f5de5-112">這可讓您定義的查詢所建立的新匿名類型成員，或目標查詢所傳回的具名型別的成員。</span><span class="sxs-lookup"><span data-stu-id="f5de5-112">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="f5de5-113">`Select`子句並不需要查詢。</span><span class="sxs-lookup"><span data-stu-id="f5de5-113">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="f5de5-114">如果沒有`Select`指定子句，查詢會傳回根據識別目前範圍的範圍變數的所有成員的類型。</span><span class="sxs-lookup"><span data-stu-id="f5de5-114">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="f5de5-115">如需詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f5de5-115">For more information, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="f5de5-116">當查詢建立具名型別時，它會傳回類型的結果<xref:System.Collections.Generic.IEnumerable%601>其中`T`已建立的類型。</span><span class="sxs-lookup"><span data-stu-id="f5de5-116">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="f5de5-117">`Select`子句可以參考目前範圍中的任何變數。</span><span class="sxs-lookup"><span data-stu-id="f5de5-117">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="f5de5-118">這包括在中所識別的範圍變數`From`子句 (或`From`子句)。</span><span class="sxs-lookup"><span data-stu-id="f5de5-118">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="f5de5-119">它也包含與別名所建立的任何新變數`Aggregate`， `Let`， `Group By`，或`Group Join`子句或將舊版的變數`Select`查詢運算式中的子句。</span><span class="sxs-lookup"><span data-stu-id="f5de5-119">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="f5de5-120">`Select`子句也可以包含靜態值。</span><span class="sxs-lookup"><span data-stu-id="f5de5-120">The `Select` clause can also include static values.</span></span> <span data-ttu-id="f5de5-121">比方說，下列程式碼範例顯示在其中的查詢運算式`Select`子句會定義查詢結果為四個成員的新匿名類型： `ProductName`， `Price`， `Discount`，和`DiscountedPrice`。</span><span class="sxs-lookup"><span data-stu-id="f5de5-121">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="f5de5-122">`ProductName`並`Price`成員值會從定義於產品範圍變數`From`子句。</span><span class="sxs-lookup"><span data-stu-id="f5de5-122">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="f5de5-123">`DiscountedPrice`成員值會計算在`Let`子句。</span><span class="sxs-lookup"><span data-stu-id="f5de5-123">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="f5de5-124">`Discount`成員是靜態的值。</span><span class="sxs-lookup"><span data-stu-id="f5de5-124">The `Discount` member is a static value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 <span data-ttu-id="f5de5-125">`Select`子句會導入一組新的範圍變數，如後續的查詢子句和前一個範圍變數已不在範圍中。</span><span class="sxs-lookup"><span data-stu-id="f5de5-125">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="f5de5-126">最後一個`Select`中查詢運算式子句會決定查詢的傳回值。</span><span class="sxs-lookup"><span data-stu-id="f5de5-126">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="f5de5-127">例如，下列查詢會傳回公司名稱和訂單總計超過 500 的每個客戶訂單識別碼。</span><span class="sxs-lookup"><span data-stu-id="f5de5-127">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="f5de5-128">第一個`Select`子句會識別的範圍變數`Where`子句和第二個`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="f5de5-128">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="f5de5-129">第二個`Select`子句會識別為新的匿名型別查詢所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="f5de5-129">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 <span data-ttu-id="f5de5-130">如果`Select`子句會識別要傳回的單一項目、 查詢運算式會傳回該單一項目之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="f5de5-130">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="f5de5-131">如果`Select`子句會識別要傳回的多個項目、 查詢運算式會傳回新的匿名類型，根據選取的項目集合。</span><span class="sxs-lookup"><span data-stu-id="f5de5-131">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="f5de5-132">例如，下列兩個查詢會傳回為基礎的兩種不同類型的集合`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="f5de5-132">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="f5de5-133">第一個查詢會傳回字串形式的公司名稱集合。</span><span class="sxs-lookup"><span data-stu-id="f5de5-133">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="f5de5-134">第二個查詢傳回的集合`Customer`填入的公司名稱和位址資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="f5de5-134">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="f5de5-135">範例</span><span class="sxs-lookup"><span data-stu-id="f5de5-135">Example</span></span>  
 <span data-ttu-id="f5de5-136">下列查詢的運算式用法`From`子句來宣告範圍變數`cust`如`customers`集合。</span><span class="sxs-lookup"><span data-stu-id="f5de5-136">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="f5de5-137">`Select`子句選取的客戶名稱和識別碼值，並於其中填入`CompanyName`和`CustomerID`新範圍變數的資料行。</span><span class="sxs-lookup"><span data-stu-id="f5de5-137">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="f5de5-138">`For Each`陳述式傳回的每個物件執行迴圈，並顯示`CompanyName`和`CustomerID`每一筆記錄的資料行。</span><span class="sxs-lookup"><span data-stu-id="f5de5-138">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="f5de5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5de5-139">See also</span></span>
- [<span data-ttu-id="f5de5-140">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="f5de5-140">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f5de5-141">查詢</span><span class="sxs-lookup"><span data-stu-id="f5de5-141">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="f5de5-142">From 子句</span><span class="sxs-lookup"><span data-stu-id="f5de5-142">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="f5de5-143">Where 子句</span><span class="sxs-lookup"><span data-stu-id="f5de5-143">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="f5de5-144">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="f5de5-144">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="f5de5-145">匿名類型</span><span class="sxs-lookup"><span data-stu-id="f5de5-145">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
