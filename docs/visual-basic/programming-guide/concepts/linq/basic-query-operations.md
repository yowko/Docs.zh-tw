---
title: 基本查詢作業
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266374"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="d4ef1-102">基本查詢作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4ef1-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="d4ef1-103">本主題簡要介紹了視覺化基礎知識中的語言集成查詢 （LINQ） 運算式，以及您在查詢中執行的一些典型操作類型。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="d4ef1-104">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d4ef1-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="d4ef1-105">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="d4ef1-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="d4ef1-106">查詢</span><span class="sxs-lookup"><span data-stu-id="d4ef1-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="d4ef1-107">逐步解說：在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="d4ef1-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="d4ef1-108">指定資料來源（來自）</span><span class="sxs-lookup"><span data-stu-id="d4ef1-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="d4ef1-109">在 LINQ 查詢中，第一步是指定要查詢的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="d4ef1-110">因此，`From`查詢中的子句始終排在第一位。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="d4ef1-111">查詢運算子根據源的類型選擇和塑造結果。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="d4ef1-112">子`From`句指定資料來源`customers`和*範圍變數*。 `cust`</span><span class="sxs-lookup"><span data-stu-id="d4ef1-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="d4ef1-113">範圍變數類似于迴圈反覆運算變數，只不過在查詢運算式中，不會發生實際反覆運算。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="d4ef1-114">執行查詢時（通常通過使用`For Each`迴圈）時，範圍變數充當 對 中每個連續元素的`customers`引用。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="d4ef1-115">因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="d4ef1-116">有關使用顯式鍵入和未進行顯式鍵入的查詢的示例，請參閱[查詢操作中的類型關係（可視基本）。](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)</span><span class="sxs-lookup"><span data-stu-id="d4ef1-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="d4ef1-117">有關如何在 Visual Basic 中使用`From`子句的詳細資訊，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="d4ef1-118">篩選資料（在哪裡）</span><span class="sxs-lookup"><span data-stu-id="d4ef1-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="d4ef1-119">最常見的查詢操作可能是以布林運算式的形式應用篩選器。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="d4ef1-120">然後，查詢僅返回運算式為 true 的元素。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="d4ef1-121">子`Where`句用於執行篩選。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="d4ef1-122">篩選器指定資料來源中要包含在結果序列中的元素。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="d4ef1-123">在下面的示例中，僅包括在倫敦有位址的客戶。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="d4ef1-124">可以使用邏輯運算子（如 和`And``Or`）在`Where`子句中組合篩選器運算式。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="d4ef1-125">例如，要僅返回來自倫敦且名稱為 Devon 的客戶，請使用以下代碼：</span><span class="sxs-lookup"><span data-stu-id="d4ef1-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="d4ef1-126">要從倫敦或巴黎返回客戶，請使用以下代碼：</span><span class="sxs-lookup"><span data-stu-id="d4ef1-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="d4ef1-127">有關如何在 Visual Basic 中使用`Where`子句的詳細資訊，請參閱[子句](../../../../visual-basic/language-reference/queries/where-clause.md)的位置 。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="d4ef1-128">訂購資料（按訂單）</span><span class="sxs-lookup"><span data-stu-id="d4ef1-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="d4ef1-129">將返回的資料按特定順序排序通常很方便。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="d4ef1-130">子`Order By`句將導致返回序列中的元素在指定的欄位或欄位上進行排序。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="d4ef1-131">例如，以下查詢根據`Name`屬性對結果進行排序。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="d4ef1-132">因為`Name`是一個字串，返回的資料將按字母順序排序，從 A 到 Z。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="d4ef1-133">若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="d4ef1-134">預設值為`Ascending`既不`Ascending`指定也不`Descending`指定時。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="d4ef1-135">有關如何在視覺化基本版中使用`Order By`子句的詳細資訊，請參閱[按子句排序](../../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="d4ef1-136">選擇資料（選擇）</span><span class="sxs-lookup"><span data-stu-id="d4ef1-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="d4ef1-137">子`Select`句指定返回元素的形式和內容。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="d4ef1-138">例如，可以指定結果是包含完整的`Customer`物件、一個`Customer`屬性、屬性子集、來自各種資料來源的屬性的組合，還是基於計算的一些新的結果類型。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="d4ef1-139">`Select` 子句不只產生一份來源項目時，作業稱為「投影」\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="d4ef1-140">要檢索由完整`Customer`物件組成的集合，請選擇範圍變數本身：</span><span class="sxs-lookup"><span data-stu-id="d4ef1-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="d4ef1-141">如果`Customer`實例是具有許多欄位的大型物件，並且要檢索的只是名稱，則可以選擇`cust.Name`，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="d4ef1-142">本地型別推斷認識到，這將結果類型從`Customer`物件集合更改為字串集合。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="d4ef1-143">要從資料來源中選擇多個欄位，有兩種選擇：</span><span class="sxs-lookup"><span data-stu-id="d4ef1-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="d4ef1-144">在子`Select`句中，指定要包含在結果中的欄位。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="d4ef1-145">編譯器將定義一個匿名型別，該類型以這些欄位作為其屬性。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="d4ef1-146">有關詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="d4ef1-147">由於以下示例中返回的元素是匿名型別的實例，因此無法按代碼的其他位置參考型別。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="d4ef1-148">類型的編譯器指定名稱包含在正常 Visual Basic 代碼中不正確字元。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="d4ef1-149">在下面的示例中，查詢返回的集合中的元素`londonCusts4`是匿名型別的實例</span><span class="sxs-lookup"><span data-stu-id="d4ef1-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="d4ef1-150">-或-</span><span class="sxs-lookup"><span data-stu-id="d4ef1-150">-or-</span></span>  
  
- <span data-ttu-id="d4ef1-151">定義包含要包含在結果中的特定欄位的命名類型，並在`Select`子句中創建和初始化該類型的實例。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="d4ef1-152">僅當必須使用返回結果的集合之外的單個結果，或者您必須在方法調用中將它們作為參數傳遞時，才使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="d4ef1-153">以下示例中的類型`londonCusts5`為 IE無枚（NamePhone）。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="d4ef1-154">有關如何在 Visual Basic 中使用`Select`子句的詳細資訊，請參閱[選擇子句](../../../../visual-basic/language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="d4ef1-155">加入資料（加入和組加入）</span><span class="sxs-lookup"><span data-stu-id="d4ef1-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="d4ef1-156">您可以通過多種方式將`From`子句中的多個資料來源合併。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="d4ef1-157">例如，以下代碼使用兩個數據源，並在結果中隱式合併兩個數據源的屬性。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="d4ef1-158">查詢選擇姓氏以母音開頭的學生。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="d4ef1-159">您可以使用在["如何：創建專案清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)"中創建的學生清單運行此代碼。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="d4ef1-160">關鍵字`Join`等效于 SQL`INNER JOIN`中。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="d4ef1-161">它基於兩個集合中元素之間的匹配鍵值組合兩個集合。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="d4ef1-162">查詢返回具有匹配鍵值的全部或部分集合元素。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="d4ef1-163">例如，以下代碼複製前一個隱式聯接的操作。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="d4ef1-164">`Group Join`將集合合併到單個分層集合中，就像`LEFT JOIN`SQL 中的集合一樣。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="d4ef1-165">有關詳細資訊，請參閱[加入子句](../../../../visual-basic/language-reference/queries/join-clause.md)和[組加入子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="d4ef1-166">分組資料（分組）</span><span class="sxs-lookup"><span data-stu-id="d4ef1-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="d4ef1-167">您可以根據元素的`Group By`一個或多個欄位添加子句來對查詢結果中的元素進行分組。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="d4ef1-168">例如，以下代碼按班級年份對學生進行分組。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="d4ef1-169">如果使用"[如何創建：創建專案清單"](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)中創建的學生清單運行此代碼，則語句中的`For Each`輸出為：</span><span class="sxs-lookup"><span data-stu-id="d4ef1-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="d4ef1-170">年： 初級</span><span class="sxs-lookup"><span data-stu-id="d4ef1-170">Year: Junior</span></span>  
  
 <span data-ttu-id="d4ef1-171">塔克， 邁克爾</span><span class="sxs-lookup"><span data-stu-id="d4ef1-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="d4ef1-172">加西亞， 雨果</span><span class="sxs-lookup"><span data-stu-id="d4ef1-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="d4ef1-173">加西亞， 黛布拉</span><span class="sxs-lookup"><span data-stu-id="d4ef1-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="d4ef1-174">塔克， 蘭斯</span><span class="sxs-lookup"><span data-stu-id="d4ef1-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="d4ef1-175">年份： 高級</span><span class="sxs-lookup"><span data-stu-id="d4ef1-175">Year: Senior</span></span>  
  
 <span data-ttu-id="d4ef1-176">奧梅利琴科， 斯韋特蘭娜</span><span class="sxs-lookup"><span data-stu-id="d4ef1-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="d4ef1-177">奧薩達， 米奇科</span><span class="sxs-lookup"><span data-stu-id="d4ef1-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="d4ef1-178">法庫裡， 法迪</span><span class="sxs-lookup"><span data-stu-id="d4ef1-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="d4ef1-179">馮漢英</span><span class="sxs-lookup"><span data-stu-id="d4ef1-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="d4ef1-180">亞當斯， 特裡</span><span class="sxs-lookup"><span data-stu-id="d4ef1-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="d4ef1-181">年份： 新生</span><span class="sxs-lookup"><span data-stu-id="d4ef1-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="d4ef1-182">莫滕森， 斯文</span><span class="sxs-lookup"><span data-stu-id="d4ef1-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="d4ef1-183">加西亞， 塞薩爾</span><span class="sxs-lookup"><span data-stu-id="d4ef1-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="d4ef1-184">以下代碼中顯示的變體對班級年數進行排序，然後按姓氏每年對學生進行訂單。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="d4ef1-185">有關 的詳細資訊`Group By`，請參閱[按子項分組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ef1-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ef1-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ef1-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="d4ef1-187">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="d4ef1-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="d4ef1-188">查詢</span><span class="sxs-lookup"><span data-stu-id="d4ef1-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d4ef1-189">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4ef1-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d4ef1-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="d4ef1-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
