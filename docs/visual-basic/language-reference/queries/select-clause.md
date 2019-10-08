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
ms.openlocfilehash: 087472c51d203be083fea0d39ade6f12066cfcb4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004744"
---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="af138-102">Select 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af138-102">Select Clause (Visual Basic)</span></span>
<span data-ttu-id="af138-103">定義查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="af138-103">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af138-104">語法</span><span class="sxs-lookup"><span data-stu-id="af138-104">Syntax</span></span>  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="af138-105">組件</span><span class="sxs-lookup"><span data-stu-id="af138-105">Parts</span></span>  
 `var1`  
 <span data-ttu-id="af138-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="af138-106">Optional.</span></span> <span data-ttu-id="af138-107">可以用來參考資料行運算式結果的別名。</span><span class="sxs-lookup"><span data-stu-id="af138-107">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="af138-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="af138-108">Required.</span></span> <span data-ttu-id="af138-109">要在查詢結果中傳回之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="af138-109">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af138-110">備註</span><span class="sxs-lookup"><span data-stu-id="af138-110">Remarks</span></span>  
 <span data-ttu-id="af138-111">您可以使用 `Select` 子句來定義要從查詢傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="af138-111">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="af138-112">這可讓您定義由查詢所建立之新匿名型別的成員，或是以查詢所傳回之命名型別的成員為目標。</span><span class="sxs-lookup"><span data-stu-id="af138-112">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="af138-113">查詢不需要 `Select` 子句。</span><span class="sxs-lookup"><span data-stu-id="af138-113">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="af138-114">如果未指定任何 `Select` 子句，則查詢會根據目前範圍所識別之範圍變數的所有成員，傳回型別。</span><span class="sxs-lookup"><span data-stu-id="af138-114">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="af138-115">如需詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="af138-115">For more information, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="af138-116">當查詢建立名為的型別時，它會傳回型別為 <xref:System.Collections.Generic.IEnumerable%601> 的結果，其中 `T` 是所建立的型別。</span><span class="sxs-lookup"><span data-stu-id="af138-116">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="af138-117">@No__t-0 子句可以參考目前範圍中的任何變數。</span><span class="sxs-lookup"><span data-stu-id="af138-117">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="af138-118">這包括在 `From` 子句（或 `From` 子句）中識別的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="af138-118">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="af138-119">它也包含以 `Aggregate`、`Let`、`Group By` 或 `Group Join` 子句的別名建立的新變數，或查詢運算式中先前 `Select` 子句的變數。</span><span class="sxs-lookup"><span data-stu-id="af138-119">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="af138-120">@No__t-0 子句也可以包含靜態值。</span><span class="sxs-lookup"><span data-stu-id="af138-120">The `Select` clause can also include static values.</span></span> <span data-ttu-id="af138-121">例如，下列程式碼範例顯示一個查詢運算式，其中 `Select` 子句會將查詢結果定義為具有四個成員的新匿名型別： `ProductName`、`Price`、`Discount` 和 `DiscountedPrice`。</span><span class="sxs-lookup"><span data-stu-id="af138-121">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="af138-122">@No__t-0 和 @no__t 1 成員值取自在 `From` 子句中定義的產品範圍變數。</span><span class="sxs-lookup"><span data-stu-id="af138-122">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="af138-123">在 `Let` 子句中，會計算 @no__t 0 的成員值。</span><span class="sxs-lookup"><span data-stu-id="af138-123">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="af138-124">@No__t 0 成員是靜態值。</span><span class="sxs-lookup"><span data-stu-id="af138-124">The `Discount` member is a static value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 <span data-ttu-id="af138-125">@No__t-0 子句為後續的查詢子句導入了一組新的範圍變數，而先前的範圍變數已不再在範圍內。</span><span class="sxs-lookup"><span data-stu-id="af138-125">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="af138-126">查詢運算式中的最後一個 `Select` 子句會決定查詢的傳回值。</span><span class="sxs-lookup"><span data-stu-id="af138-126">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="af138-127">例如，下列查詢會傳回總計超過500的每個客戶訂單的公司名稱和訂單識別碼。</span><span class="sxs-lookup"><span data-stu-id="af138-127">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="af138-128">第一個 `Select` 子句會識別 `Where` 子句和第二個 `Select` 子句的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="af138-128">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="af138-129">第二個 `Select` 子句會將查詢所傳回的值識別為新的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="af138-129">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 <span data-ttu-id="af138-130">如果 `Select` 子句識別要傳回的單一專案，則查詢運算式會傳回該單一專案之類型的集合。</span><span class="sxs-lookup"><span data-stu-id="af138-130">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="af138-131">如果 `Select` 子句識別要傳回的多個專案，則查詢運算式會根據選取的專案，傳回新匿名型別的集合。</span><span class="sxs-lookup"><span data-stu-id="af138-131">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="af138-132">例如，下列兩個查詢會根據 `Select` 子句傳回兩個不同類型的集合。</span><span class="sxs-lookup"><span data-stu-id="af138-132">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="af138-133">第一個查詢會以字串形式傳回公司名稱的集合。</span><span class="sxs-lookup"><span data-stu-id="af138-133">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="af138-134">第二個查詢會傳回以公司名稱和位址資訊填入之 @no__t 0 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="af138-134">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="af138-135">範例</span><span class="sxs-lookup"><span data-stu-id="af138-135">Example</span></span>  
 <span data-ttu-id="af138-136">下列查詢運算式會使用 `From` 子句，針對 @no__t 2 集合宣告範圍變數 `cust`。</span><span class="sxs-lookup"><span data-stu-id="af138-136">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="af138-137">@No__t-0 子句會選取 [客戶名稱] 和 [識別碼] 值，並填入新範圍變數的 `CompanyName` 和 @no__t 2 資料行。</span><span class="sxs-lookup"><span data-stu-id="af138-137">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="af138-138">@No__t-0 語句會在每個傳回的物件上迴圈，並顯示每一筆記錄的 `CompanyName` 和 @no__t 2 資料行。</span><span class="sxs-lookup"><span data-stu-id="af138-138">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="af138-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af138-139">See also</span></span>

- [<span data-ttu-id="af138-140">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="af138-140">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="af138-141">查詢</span><span class="sxs-lookup"><span data-stu-id="af138-141">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="af138-142">From 子句</span><span class="sxs-lookup"><span data-stu-id="af138-142">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="af138-143">Where 子句</span><span class="sxs-lookup"><span data-stu-id="af138-143">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="af138-144">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="af138-144">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="af138-145">匿名類型</span><span class="sxs-lookup"><span data-stu-id="af138-145">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
