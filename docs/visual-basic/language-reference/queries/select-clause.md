---
title: Select 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: d96423efbee075a7ad257df72471c71e38e09b63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875747"
---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="4a082-102">Select 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a082-102">Select Clause (Visual Basic)</span></span>

<span data-ttu-id="4a082-103">定義查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="4a082-103">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a082-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a082-104">Syntax</span></span>  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="4a082-105">組件</span><span class="sxs-lookup"><span data-stu-id="4a082-105">Parts</span></span>  

 `var1`  
 <span data-ttu-id="4a082-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4a082-106">Optional.</span></span> <span data-ttu-id="4a082-107">別名，可用來參考資料行運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="4a082-107">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="4a082-108">必要。</span><span class="sxs-lookup"><span data-stu-id="4a082-108">Required.</span></span> <span data-ttu-id="4a082-109">要在查詢結果中傳回之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a082-109">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a082-110">備註</span><span class="sxs-lookup"><span data-stu-id="4a082-110">Remarks</span></span>  

 <span data-ttu-id="4a082-111">您可以使用 `Select` 子句來定義要從查詢傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="4a082-111">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="4a082-112">這可讓您定義查詢所建立之新匿名型別的成員，或以查詢所傳回之命名類型的成員為目標。</span><span class="sxs-lookup"><span data-stu-id="4a082-112">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="4a082-113">`Select`查詢不需要子句。</span><span class="sxs-lookup"><span data-stu-id="4a082-113">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="4a082-114">如果未 `Select` 指定子句，則查詢會根據針對目前範圍所識別之範圍變數的所有成員，傳回型別。</span><span class="sxs-lookup"><span data-stu-id="4a082-114">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="4a082-115">如需詳細資訊，請參閱 [匿名型別](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4a082-115">For more information, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="4a082-116">當查詢建立已命名的型別時，它會傳回類型的結果， <xref:System.Collections.Generic.IEnumerable%601> 其中 `T` 是所建立的型別。</span><span class="sxs-lookup"><span data-stu-id="4a082-116">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="4a082-117">`Select`子句可以參考目前範圍中的任何變數。</span><span class="sxs-lookup"><span data-stu-id="4a082-117">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="4a082-118">這包括子句中所識別的範圍變數 `From` (或 `From` 子句) 。</span><span class="sxs-lookup"><span data-stu-id="4a082-118">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="4a082-119">它也包含使用、、或子句中的別名建立的任何新變數 `Aggregate` `Let` `Group By` `Group Join` ，或查詢運算式中上一個子句中的變數 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="4a082-119">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="4a082-120">`Select`子句也可以包含靜態值。</span><span class="sxs-lookup"><span data-stu-id="4a082-120">The `Select` clause can also include static values.</span></span> <span data-ttu-id="4a082-121">例如，下列程式碼範例會顯示查詢運算式，其中子句會將 `Select` 查詢結果定義為具有四個成員的新匿名型別： `ProductName` 、 `Price` 、 `Discount` 和 `DiscountedPrice` 。</span><span class="sxs-lookup"><span data-stu-id="4a082-121">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="4a082-122">`ProductName`和 `Price` 成員值取自在子句中定義的產品範圍變數 `From` 。</span><span class="sxs-lookup"><span data-stu-id="4a082-122">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="4a082-123">`DiscountedPrice`成員值是在子句中計算 `Let` 。</span><span class="sxs-lookup"><span data-stu-id="4a082-123">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="4a082-124">`Discount`成員是靜態值。</span><span class="sxs-lookup"><span data-stu-id="4a082-124">The `Discount` member is a static value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 <span data-ttu-id="4a082-125">`Select`子句會為後續的查詢子句引進一組新的範圍變數，而先前的範圍變數不再位於範圍內。</span><span class="sxs-lookup"><span data-stu-id="4a082-125">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="4a082-126">`Select`查詢運算式中的最後一個子句會判斷查詢的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4a082-126">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="4a082-127">例如，下列查詢會傳回總計超過500的每個客戶訂單的公司名稱和訂單識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a082-127">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="4a082-128">第一個 `Select` 子句會識別 `Where` 子句和第二個子句的範圍變數 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="4a082-128">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="4a082-129">第二個子句會將 `Select` 查詢所傳回的值識別為新的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="4a082-129">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 <span data-ttu-id="4a082-130">如果 `Select` 子句識別要傳回的單一專案，查詢運算式會傳回該單一專案之型別的集合。</span><span class="sxs-lookup"><span data-stu-id="4a082-130">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="4a082-131">如果 `Select` 子句識別要傳回的多個專案，則查詢運算式會根據選取的專案，傳回新匿名型別的集合。</span><span class="sxs-lookup"><span data-stu-id="4a082-131">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="4a082-132">例如，下列兩個查詢會根據子句傳回兩個不同類型的集合 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="4a082-132">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="4a082-133">第一個查詢會以字串形式傳回公司名稱的集合。</span><span class="sxs-lookup"><span data-stu-id="4a082-133">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="4a082-134">第二個查詢會傳回 `Customer` 以公司名稱和位址資訊填入的物件集合。</span><span class="sxs-lookup"><span data-stu-id="4a082-134">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="4a082-135">範例</span><span class="sxs-lookup"><span data-stu-id="4a082-135">Example</span></span>  

 <span data-ttu-id="4a082-136">下列查詢運算式使用 `From` 子句來宣告集合的範圍變數 `cust` `customers` 。</span><span class="sxs-lookup"><span data-stu-id="4a082-136">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="4a082-137">`Select`子句會選取 [客戶名稱] 和 [識別碼] 值，並填入 `CompanyName` `CustomerID` 新範圍變數的和資料行。</span><span class="sxs-lookup"><span data-stu-id="4a082-137">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="4a082-138">語句會在 `For Each` 每個傳回的物件上進行迴圈，並顯示 `CompanyName` 每一筆記錄的和資料 `CustomerID` 行。</span><span class="sxs-lookup"><span data-stu-id="4a082-138">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="4a082-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a082-139">See also</span></span>

- [<span data-ttu-id="4a082-140">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="4a082-140">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4a082-141">查詢</span><span class="sxs-lookup"><span data-stu-id="4a082-141">Queries</span></span>](index.md)
- [<span data-ttu-id="4a082-142">From 子句</span><span class="sxs-lookup"><span data-stu-id="4a082-142">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="4a082-143">Where 子句</span><span class="sxs-lookup"><span data-stu-id="4a082-143">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="4a082-144">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="4a082-144">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="4a082-145">匿名類型</span><span class="sxs-lookup"><span data-stu-id="4a082-145">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
