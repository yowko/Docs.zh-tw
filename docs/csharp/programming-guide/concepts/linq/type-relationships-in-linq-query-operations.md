---
title: LINQ 查詢作業中的類型關聯性 (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: b58219a8a4d45ce01f80fd367ed56b13a773e4bc
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483407"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="56a5f-102">LINQ 查詢作業中的類型關聯性 (C#)</span><span class="sxs-lookup"><span data-stu-id="56a5f-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="56a5f-103">若要有效地撰寫查詢，您應該了解完整查詢作業中的變數類型如何彼此相關。</span><span class="sxs-lookup"><span data-stu-id="56a5f-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="56a5f-104">如果您了解這些關聯性，則可更輕鬆地理解文件中的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 範例和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="56a5f-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="56a5f-105">此外，您將了解使用 `var` 讓變數成為隱含類型時的幕後作業。</span><span class="sxs-lookup"><span data-stu-id="56a5f-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="56a5f-106">在資料來源、查詢本身和查詢執行中，[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢作業都是強型別。</span><span class="sxs-lookup"><span data-stu-id="56a5f-106">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="56a5f-107">查詢中的變數類型必須與資料來源中的項目類型以及 `foreach` 陳述式中的反覆運算變數類型相容。</span><span class="sxs-lookup"><span data-stu-id="56a5f-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="56a5f-108">如果類型錯誤可以在使用者遇到它們之前進行更正，則這個強型別可確保在編譯時期攔截到它們。</span><span class="sxs-lookup"><span data-stu-id="56a5f-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="56a5f-109">為了示範這些類型關聯性，後面的大部分範例都會使用所有變數的明確類型。</span><span class="sxs-lookup"><span data-stu-id="56a5f-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="56a5f-110">最後一個範例示範即使使用隱含類型時，還是如何使用 [var](../../../../csharp/language-reference/keywords/var.md) 來套用相同原則。</span><span class="sxs-lookup"><span data-stu-id="56a5f-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../../csharp/language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="56a5f-111">未轉換來源資料的查詢</span><span class="sxs-lookup"><span data-stu-id="56a5f-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="56a5f-112">下圖顯示未對資料執行任何轉換的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects 查詢作業。</span><span class="sxs-lookup"><span data-stu-id="56a5f-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="56a5f-113">來源包含一系列的字串，而且查詢輸出也是一系列的字串。</span><span class="sxs-lookup"><span data-stu-id="56a5f-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![顯示 LINQ 查詢中資料類型關聯的圖表。](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="56a5f-115">資料來源的類型引數決定範圍變數的類型。</span><span class="sxs-lookup"><span data-stu-id="56a5f-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="56a5f-116">所選取物件的類型會決定查詢變數的類型。</span><span class="sxs-lookup"><span data-stu-id="56a5f-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="56a5f-117">`name` 是字串。</span><span class="sxs-lookup"><span data-stu-id="56a5f-117">Here `name` is a string.</span></span> <span data-ttu-id="56a5f-118">因此，查詢變數是 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="56a5f-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="56a5f-119">在 `foreach` 陳述式中，會逐一查看查詢變數。</span><span class="sxs-lookup"><span data-stu-id="56a5f-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="56a5f-120">因為查詢變數是一序列的字串，所以反覆運算變數也是字串。</span><span class="sxs-lookup"><span data-stu-id="56a5f-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="56a5f-121">轉換來源資料的查詢</span><span class="sxs-lookup"><span data-stu-id="56a5f-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="56a5f-122">下圖顯示對資料執行簡單轉換的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查詢作業。</span><span class="sxs-lookup"><span data-stu-id="56a5f-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="56a5f-123">查詢會接受一系列的 `Customer` 物件作為輸出，並只選取結果中的 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="56a5f-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="56a5f-124">因為 `Name` 是字串，所以查詢會產生一系列的字串作為輸出。</span><span class="sxs-lookup"><span data-stu-id="56a5f-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![顯示轉換資料類型查詢的圖表。](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="56a5f-126">資料來源的類型引數決定範圍變數的類型。</span><span class="sxs-lookup"><span data-stu-id="56a5f-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="56a5f-127">`select` 陳述式會傳回 `Name` 屬性，而非完整 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="56a5f-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="56a5f-128">因為 `Name` 是字串，所以 `custNameQuery` 的類型引數是 `string`，而非 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="56a5f-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="56a5f-129">因為 `custNameQuery` 是一序列的字串，所以 `foreach` 迴圈的反覆運算變數也必須是 `string`。</span><span class="sxs-lookup"><span data-stu-id="56a5f-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="56a5f-130">下圖顯示稍微複雜的轉換。</span><span class="sxs-lookup"><span data-stu-id="56a5f-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="56a5f-131">`select` 陳述式會傳回匿名型別，只擷取原始 `Customer` 物件的兩個成員。</span><span class="sxs-lookup"><span data-stu-id="56a5f-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![顯示轉換資料類型更複雜查詢的圖表。](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="56a5f-133">資料來源的類型引數一律是查詢中範圍變數的類型。</span><span class="sxs-lookup"><span data-stu-id="56a5f-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="56a5f-134">因為 `select` 陳述式會產生匿名型別，所以必須使用 `var` 讓查詢變數成為隱含類型。</span><span class="sxs-lookup"><span data-stu-id="56a5f-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="56a5f-135">因為查詢變數的類型是隱含的，所以 `foreach` 迴圈中的反覆運算變數也是隱含的。</span><span class="sxs-lookup"><span data-stu-id="56a5f-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="56a5f-136">讓編譯器推斷類型資訊</span><span class="sxs-lookup"><span data-stu-id="56a5f-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="56a5f-137">雖然您應該了解查詢作業中的類型關聯性，但可以選擇讓編譯器為您執行所有工作。</span><span class="sxs-lookup"><span data-stu-id="56a5f-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="56a5f-138">[var](../../../../csharp/language-reference/keywords/var.md) 關鍵字可以用於查詢作業中的任何區域變數。</span><span class="sxs-lookup"><span data-stu-id="56a5f-138">The keyword [var](../../../../csharp/language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="56a5f-139">下圖與先前討論的範例 2 類似。</span><span class="sxs-lookup"><span data-stu-id="56a5f-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="56a5f-140">不過，編譯器會提供查詢作業中每個變數的強型別。</span><span class="sxs-lookup"><span data-stu-id="56a5f-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![顯示具有隱含類型之類型流程的圖表。](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="56a5f-142">如需 `var` 的詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="56a5f-142">For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
