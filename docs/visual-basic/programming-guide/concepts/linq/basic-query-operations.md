---
title: 基本查詢作業 (Visual Basic)
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
ms.openlocfilehash: 5587a60e97464324659b325e38a18ac25488d30d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="e987c-102">基本查詢作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e987c-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="e987c-103">本主題提供簡介[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]運算式在 Visual Basic 中，並且一些您在查詢中執行的作業一般類型。</span><span class="sxs-lookup"><span data-stu-id="e987c-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="e987c-104">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="e987c-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="e987c-105">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="e987c-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="e987c-106">查詢</span><span class="sxs-lookup"><span data-stu-id="e987c-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [<span data-ttu-id="e987c-107">逐步解說： 在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="e987c-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="e987c-108">指定資料來源 （來源）</span><span class="sxs-lookup"><span data-stu-id="e987c-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="e987c-109">在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢中，第一個步驟是指定您想要查詢的資料來源。</span><span class="sxs-lookup"><span data-stu-id="e987c-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="e987c-110">因此，`From`子句的查詢中一律是第一次。</span><span class="sxs-lookup"><span data-stu-id="e987c-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="e987c-111">查詢運算子會選取和圖形的來源類型為基礎的結果。</span><span class="sxs-lookup"><span data-stu-id="e987c-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 <span data-ttu-id="e987c-112">`From`子句指定的資料來源， `customers`，和*範圍變數*， `cust`。</span><span class="sxs-lookup"><span data-stu-id="e987c-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="e987c-113">範圍變數是類似於迴圈的反覆項目變數中，不同之處在於查詢運算式中沒有實際的反覆項目，就會發生。</span><span class="sxs-lookup"><span data-stu-id="e987c-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="e987c-114">查詢執行時，通常使用`For Each`迴圈，做為在每個後續項目參考的範圍變數`customers`。</span><span class="sxs-lookup"><span data-stu-id="e987c-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="e987c-115">因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。</span><span class="sxs-lookup"><span data-stu-id="e987c-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="e987c-116">寫入逾時或無明確輸入查詢的範例，請參閱[查詢作業 (Visual Basic) 中的類型關聯性](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="e987c-117">如需有關如何使用`From`子句在 Visual Basic，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="e987c-118">篩選資料 （位置）</span><span class="sxs-lookup"><span data-stu-id="e987c-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="e987c-119">可能最常見的查詢作業套用篩選的布林運算式的形式。</span><span class="sxs-lookup"><span data-stu-id="e987c-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="e987c-120">然後查詢會傳回只在運算式為 true 的元素。</span><span class="sxs-lookup"><span data-stu-id="e987c-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="e987c-121">A`Where`子句用來執行的篩選。</span><span class="sxs-lookup"><span data-stu-id="e987c-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="e987c-122">篩選器會指定要包含在結果序列中的資料來源中的哪些項目。</span><span class="sxs-lookup"><span data-stu-id="e987c-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="e987c-123">在下列範例中，只有這些客戶在倫敦 （london） 的位址會包含。</span><span class="sxs-lookup"><span data-stu-id="e987c-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 <span data-ttu-id="e987c-124">您可以使用邏輯運算子，例如`And`和`Or`結合篩選條件運算式中的`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="e987c-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="e987c-125">例如，若要傳回只有那些客戶從倫敦 （london） 以及其名稱是 Devon，使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e987c-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="e987c-126">若要從倫敦 （london） 或巴黎傳回客戶，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e987c-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="e987c-127">如需有關如何使用`Where`子句在 Visual Basic，請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="e987c-128">排序資料 (Order By)</span><span class="sxs-lookup"><span data-stu-id="e987c-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="e987c-129">通常很方便地排序傳回的資料排列成非特定順序。</span><span class="sxs-lookup"><span data-stu-id="e987c-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="e987c-130">`Order By`子句便會傳回指定的欄位或欄位排序序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="e987c-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="e987c-131">例如，下列查詢會排序結果根據`Name`屬性。</span><span class="sxs-lookup"><span data-stu-id="e987c-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="e987c-132">因為`Name`是一個字串，將依照字母順序排序傳回的資料，從 A 到 Z。</span><span class="sxs-lookup"><span data-stu-id="e987c-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 <span data-ttu-id="e987c-133">若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。</span><span class="sxs-lookup"><span data-stu-id="e987c-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="e987c-134">預設值是`Ascending`當兩者皆非`Ascending`也`Descending`指定。</span><span class="sxs-lookup"><span data-stu-id="e987c-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="e987c-135">如需有關如何使用`Order By`子句在 Visual Basic，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="e987c-136">選取的資料 （選取）</span><span class="sxs-lookup"><span data-stu-id="e987c-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="e987c-137">`Select`子句會指定表單並傳回項目的內容。</span><span class="sxs-lookup"><span data-stu-id="e987c-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="e987c-138">例如，您可以指定是否將結果將會包含完整`Customer`物件，其中一個`Customer`屬性、 屬性的子集、 從各種資料來源或某些新的結果型別屬性的組合為基礎的計算。</span><span class="sxs-lookup"><span data-stu-id="e987c-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="e987c-139">`Select` 子句不只產生一份來源項目時，作業稱為「投影」。</span><span class="sxs-lookup"><span data-stu-id="e987c-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="e987c-140">若要擷取集合，其中包含完整`Customer`物件，選取本身的範圍變數：</span><span class="sxs-lookup"><span data-stu-id="e987c-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 <span data-ttu-id="e987c-141">如果`Customer`執行個體是大型物件，有許多欄位，以及所有您想要擷取是的名稱，您可以選取`cust.Name`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e987c-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="e987c-142">這會變更結果型別集合中的區域類型推斷會辨識`Customer`的字串集合的物件。</span><span class="sxs-lookup"><span data-stu-id="e987c-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 <span data-ttu-id="e987c-143">若要選取多個欄位從資料來源，您有兩個選擇：</span><span class="sxs-lookup"><span data-stu-id="e987c-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="e987c-144">在`Select`子句，指定您想要包含在結果中的欄位。</span><span class="sxs-lookup"><span data-stu-id="e987c-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="e987c-145">編譯器會在定義的那些欄位做為其屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="e987c-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="e987c-146">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="e987c-147">在下列範例傳回的元素是匿名類型的執行個體，因為您無法為型別依名稱參考其他地方程式碼中。</span><span class="sxs-lookup"><span data-stu-id="e987c-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="e987c-148">編譯器指定類型名稱包含在標準的 Visual Basic 程式碼中無效的字元。</span><span class="sxs-lookup"><span data-stu-id="e987c-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="e987c-149">在下列範例中，在集合中的查詢所傳回的項目`londonCusts4`是匿名類型的執行個體</span><span class="sxs-lookup"><span data-stu-id="e987c-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     <span data-ttu-id="e987c-150">-或-</span><span class="sxs-lookup"><span data-stu-id="e987c-150">-or-</span></span>  
  
-   <span data-ttu-id="e987c-151">定義包含您想要包含在結果中，以及建立和初始化中的型別之執行個體的特定欄位的具名的類型`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="e987c-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="e987c-152">只有當您必須使用個別結果之外的記憶體回收會傳回這些，或如果您必須將其傳遞做為方法呼叫中的參數，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="e987c-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="e987c-153">型別`londonCusts5`在下列範例中是 IEnumerable (Of NamePhone)。</span><span class="sxs-lookup"><span data-stu-id="e987c-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 <span data-ttu-id="e987c-154">如需有關如何使用`Select`子句在 Visual Basic，請參閱[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="e987c-155">聯結 （聯結和群組聯結） 的資料</span><span class="sxs-lookup"><span data-stu-id="e987c-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="e987c-156">您可以結合多個資料來源中的`From`子句數種方式。</span><span class="sxs-lookup"><span data-stu-id="e987c-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="e987c-157">例如，下列程式碼會使用兩個資料來源，並隱含地結合來自這兩種結果中的屬性。</span><span class="sxs-lookup"><span data-stu-id="e987c-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="e987c-158">查詢會選取的學生姓氏開頭為母音。</span><span class="sxs-lookup"><span data-stu-id="e987c-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="e987c-159">您可以執行此程式碼中建立的學員清單[How to： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="e987c-160">`Join`關鍵字相當於`INNER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="e987c-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="e987c-161">它結合了兩個集合中的項目之間的比對索引鍵值為基礎的兩個集合。</span><span class="sxs-lookup"><span data-stu-id="e987c-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="e987c-162">查詢會傳回全部或部分有相符的索引鍵的值的集合項目。</span><span class="sxs-lookup"><span data-stu-id="e987c-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="e987c-163">例如，下列程式碼複製先前的隱含聯結的動作。</span><span class="sxs-lookup"><span data-stu-id="e987c-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 <span data-ttu-id="e987c-164">`Group Join` 將集合合併成單一階層式實體集合，就像是`LEFT JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="e987c-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="e987c-165">如需詳細資訊，請參閱[Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)和[Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="e987c-166">群組 (Group By) 的資料</span><span class="sxs-lookup"><span data-stu-id="e987c-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="e987c-167">您可以加入`Group By`子句分組查詢結果，根據一個或多個欄位的項目中的項目。</span><span class="sxs-lookup"><span data-stu-id="e987c-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="e987c-168">例如，下列程式碼會將學生分組類別年。</span><span class="sxs-lookup"><span data-stu-id="e987c-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 <span data-ttu-id="e987c-169">如果您執行此程式碼使用的學生在中建立清單[How to： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)，從輸出`For Each`陳述式：</span><span class="sxs-lookup"><span data-stu-id="e987c-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="e987c-170">年份： Junior</span><span class="sxs-lookup"><span data-stu-id="e987c-170">Year: Junior</span></span>  
  
 <span data-ttu-id="e987c-171">Tucker Michael</span><span class="sxs-lookup"><span data-stu-id="e987c-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="e987c-172">Garcia Hugo</span><span class="sxs-lookup"><span data-stu-id="e987c-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="e987c-173">Garcia 蔡</span><span class="sxs-lookup"><span data-stu-id="e987c-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="e987c-174">Tucker 騎士</span><span class="sxs-lookup"><span data-stu-id="e987c-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="e987c-175">年份： 資深</span><span class="sxs-lookup"><span data-stu-id="e987c-175">Year: Senior</span></span>  
  
 <span data-ttu-id="e987c-176">Omelchenko Svetlana</span><span class="sxs-lookup"><span data-stu-id="e987c-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="e987c-177">Osada Michiko</span><span class="sxs-lookup"><span data-stu-id="e987c-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="e987c-178">Fakhouri Fadi</span><span class="sxs-lookup"><span data-stu-id="e987c-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="e987c-179">Hanying Feng</span><span class="sxs-lookup"><span data-stu-id="e987c-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="e987c-180">Adams Terry</span><span class="sxs-lookup"><span data-stu-id="e987c-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="e987c-181">年份： 包括新生諮詢人員</span><span class="sxs-lookup"><span data-stu-id="e987c-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="e987c-182">Mortensen Sven</span><span class="sxs-lookup"><span data-stu-id="e987c-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="e987c-183">Garcia Cesar</span><span class="sxs-lookup"><span data-stu-id="e987c-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="e987c-184">下列程式碼所示的變化年級，，然後每年排列學生的姓氏。</span><span class="sxs-lookup"><span data-stu-id="e987c-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 <span data-ttu-id="e987c-185">如需有關`Group By`，請參閱[群組 By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e987c-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e987c-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e987c-186">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="e987c-187">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="e987c-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="e987c-188">查詢</span><span class="sxs-lookup"><span data-stu-id="e987c-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="e987c-189">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e987c-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="e987c-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="e987c-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
