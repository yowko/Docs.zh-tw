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
ms.openlocfilehash: 12f10f30dd767f3435044f2bbebe0eb865c29d0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939370"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="f62a5-102">基本查詢作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f62a5-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="f62a5-103">本主題提供 Visual Basic 中的[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]運算式, 以及您在查詢中執行的一些一般作業類型的簡介。</span><span class="sxs-lookup"><span data-stu-id="f62a5-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="f62a5-104">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="f62a5-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="f62a5-105">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="f62a5-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="f62a5-106">查詢</span><span class="sxs-lookup"><span data-stu-id="f62a5-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="f62a5-107">逐步解說：在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="f62a5-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="f62a5-108">指定資料來源 (從)</span><span class="sxs-lookup"><span data-stu-id="f62a5-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="f62a5-109">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]在查詢中, 第一個步驟是指定您想要查詢的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f62a5-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="f62a5-110">因此, 查詢`From`中的子句一律會先出現。</span><span class="sxs-lookup"><span data-stu-id="f62a5-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="f62a5-111">查詢運算子會根據來源的類型來選取和塑造結果。</span><span class="sxs-lookup"><span data-stu-id="f62a5-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="f62a5-112">子句會指定資料`customers`源`cust`和*範圍變數。* `From`</span><span class="sxs-lookup"><span data-stu-id="f62a5-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="f62a5-113">範圍變數就像迴圈反覆運算變數, 不同的是, 在查詢運算式中, 不會發生實際的反復專案。</span><span class="sxs-lookup"><span data-stu-id="f62a5-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="f62a5-114">執行查詢時, 通常會使用`For Each`迴圈, 範圍變數會當做中`customers`每個後續元素的參考。</span><span class="sxs-lookup"><span data-stu-id="f62a5-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="f62a5-115">因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。</span><span class="sxs-lookup"><span data-stu-id="f62a5-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="f62a5-116">如需使用和而不明確輸入來撰寫之查詢的範例, 請參閱[查詢作業中的類型關聯性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="f62a5-117">如需如何在 Visual Basic 中使用`From`子句的詳細資訊, 請參閱[from 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="f62a5-118">篩選資料 (Where)</span><span class="sxs-lookup"><span data-stu-id="f62a5-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="f62a5-119">最常見的查詢作業可能是以布林運算式的形式套用篩選。</span><span class="sxs-lookup"><span data-stu-id="f62a5-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="f62a5-120">然後, 此查詢只會傳回運算式為 true 的元素。</span><span class="sxs-lookup"><span data-stu-id="f62a5-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="f62a5-121">`Where`子句是用來執行篩選。</span><span class="sxs-lookup"><span data-stu-id="f62a5-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="f62a5-122">篩選器會指定要在結果序列中包含的資料來源中的哪些元素。</span><span class="sxs-lookup"><span data-stu-id="f62a5-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="f62a5-123">在下列範例中, 只會包含在倫敦具有位址的客戶。</span><span class="sxs-lookup"><span data-stu-id="f62a5-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="f62a5-124">您可以使用邏輯運算子 (例如`And`和`Or` ) 來結合子句中的`Where`篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="f62a5-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="f62a5-125">例如, 若只要傳回來自倫敦且其名稱為 Devon 的客戶, 請使用下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="f62a5-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="f62a5-126">若要傳回來自倫敦或巴黎的客戶, 請使用下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="f62a5-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="f62a5-127">如需如何在 Visual Basic 中使用`Where`子句的詳細資訊, 請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="f62a5-128">排序資料 (Order By)</span><span class="sxs-lookup"><span data-stu-id="f62a5-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="f62a5-129">將傳回的資料排序為特定的順序, 通常是很方便的方式。</span><span class="sxs-lookup"><span data-stu-id="f62a5-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="f62a5-130">`Order By`子句會使傳回序列中的專案在指定的欄位上進行排序。</span><span class="sxs-lookup"><span data-stu-id="f62a5-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="f62a5-131">例如, 下列查詢會根據`Name`屬性來排序結果。</span><span class="sxs-lookup"><span data-stu-id="f62a5-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="f62a5-132">因為`Name`是字串, 所以傳回的資料會依字母順序從 a 到 Z 排序。</span><span class="sxs-lookup"><span data-stu-id="f62a5-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="f62a5-133">若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。</span><span class="sxs-lookup"><span data-stu-id="f62a5-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="f62a5-134">當沒有指定`Ascending` 或`Descending`時, 預設值為。 `Ascending`</span><span class="sxs-lookup"><span data-stu-id="f62a5-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="f62a5-135">如需如何在 Visual Basic 中使用`Order By`子句的詳細資訊, 請參閱[Order by 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="f62a5-136">選取資料 (選取)</span><span class="sxs-lookup"><span data-stu-id="f62a5-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="f62a5-137">`Select`子句會指定傳回元素的表單和內容。</span><span class="sxs-lookup"><span data-stu-id="f62a5-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="f62a5-138">例如, 您可以指定您的結果是否包含完整`Customer`的物件、只有一個`Customer`屬性、屬性的子集、來自各種資料來源的屬性組合, 或是以計算為基礎的一些新結果型別。</span><span class="sxs-lookup"><span data-stu-id="f62a5-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="f62a5-139">`Select` 子句不只產生一份來源項目時，作業稱為「投影」。</span><span class="sxs-lookup"><span data-stu-id="f62a5-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="f62a5-140">若要取出由完整`Customer`物件所組成的集合, 請選取範圍變數本身:</span><span class="sxs-lookup"><span data-stu-id="f62a5-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="f62a5-141">如果實例是具有許多欄位的大型物件, 而您想要取出的是名稱, 您可以選取`cust.Name`, 如下列範例所示。 `Customer`</span><span class="sxs-lookup"><span data-stu-id="f62a5-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="f62a5-142">區欄位型別推斷會辨識這項`Customer`工作會將結果類型從物件集合變更為字串的集合。</span><span class="sxs-lookup"><span data-stu-id="f62a5-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="f62a5-143">若要從資料來源選取多個欄位, 您有兩個選擇:</span><span class="sxs-lookup"><span data-stu-id="f62a5-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="f62a5-144">`Select`在子句中, 指定您想要包含在結果中的欄位。</span><span class="sxs-lookup"><span data-stu-id="f62a5-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="f62a5-145">編譯器會定義具有這些欄位做為其屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="f62a5-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="f62a5-146">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="f62a5-147">因為下列範例中傳回的元素是匿名型別的實例, 所以您無法在程式碼中的其他地方依名稱參考該型別。</span><span class="sxs-lookup"><span data-stu-id="f62a5-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="f62a5-148">類型的編譯器指定名稱包含在一般 Visual Basic 程式碼中不正確字元。</span><span class="sxs-lookup"><span data-stu-id="f62a5-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="f62a5-149">在下列範例中, 查詢`londonCusts4`所傳回之集合中的元素是匿名型別的實例。</span><span class="sxs-lookup"><span data-stu-id="f62a5-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="f62a5-150">-或-</span><span class="sxs-lookup"><span data-stu-id="f62a5-150">-or-</span></span>  
  
- <span data-ttu-id="f62a5-151">定義名為的型別, 其中包含您想要包含在結果中的特定欄位, 並在`Select`子句中建立和初始化型別的實例。</span><span class="sxs-lookup"><span data-stu-id="f62a5-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="f62a5-152">只有當您必須在傳回的集合以外的個別結果, 或是您必須將它們當做方法呼叫中的參數傳遞時, 才使用此選項。</span><span class="sxs-lookup"><span data-stu-id="f62a5-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="f62a5-153">下列範例`londonCusts5`中的類型是 IEnumerable (of NamePhone)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="f62a5-154">如需如何在 Visual Basic 中使用`Select`子句的詳細資訊, 請參閱[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="f62a5-155">聯結資料 (聯結和群組聯結)</span><span class="sxs-lookup"><span data-stu-id="f62a5-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="f62a5-156">您可以用數種方式在子句中結合`From`一個以上的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f62a5-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="f62a5-157">例如, 下列程式碼會使用兩個數據源, 並在結果中隱含結合兩者的屬性。</span><span class="sxs-lookup"><span data-stu-id="f62a5-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="f62a5-158">查詢會選取姓氏以母音開頭的學生。</span><span class="sxs-lookup"><span data-stu-id="f62a5-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="f62a5-159">您可以使用下列[方式來執行此程式碼: 建立的學生清單建立專案](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)清單。</span><span class="sxs-lookup"><span data-stu-id="f62a5-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="f62a5-160">關鍵字相當於 SQL 中的`INNER JOIN`。 `Join`</span><span class="sxs-lookup"><span data-stu-id="f62a5-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="f62a5-161">它會根據兩個集合中元素之間相符的索引鍵值, 結合兩個集合。</span><span class="sxs-lookup"><span data-stu-id="f62a5-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="f62a5-162">此查詢會傳回具有相符索引鍵值的全部或部分集合元素。</span><span class="sxs-lookup"><span data-stu-id="f62a5-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="f62a5-163">例如, 下列程式碼會重複先前的隱含聯結動作。</span><span class="sxs-lookup"><span data-stu-id="f62a5-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="f62a5-164">`Group Join`將集合結合成單一階層式集合, 就像`LEFT JOIN` SQL 中的一樣。</span><span class="sxs-lookup"><span data-stu-id="f62a5-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="f62a5-165">如需詳細資訊, 請參閱[聯結子句](../../../../visual-basic/language-reference/queries/join-clause.md)和[群組聯結子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="f62a5-166">群組資料 (分組依據)</span><span class="sxs-lookup"><span data-stu-id="f62a5-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="f62a5-167">您可以加入`Group By`子句, 根據元素的一或多個欄位, 將查詢結果中的專案分組。</span><span class="sxs-lookup"><span data-stu-id="f62a5-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="f62a5-168">例如, 下列程式碼會依類別年度來分組學生。</span><span class="sxs-lookup"><span data-stu-id="f62a5-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="f62a5-169">如果您使用下列[方式建立的程式碼:建立專案](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)清單, `For Each`語句的輸出為:</span><span class="sxs-lookup"><span data-stu-id="f62a5-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="f62a5-170">歷年初級</span><span class="sxs-lookup"><span data-stu-id="f62a5-170">Year: Junior</span></span>  
  
 <span data-ttu-id="f62a5-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="f62a5-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="f62a5-172">Garcia、Hugo</span><span class="sxs-lookup"><span data-stu-id="f62a5-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="f62a5-173">Garcia、Debra</span><span class="sxs-lookup"><span data-stu-id="f62a5-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="f62a5-174">Tucker、Lance</span><span class="sxs-lookup"><span data-stu-id="f62a5-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="f62a5-175">歷年高</span><span class="sxs-lookup"><span data-stu-id="f62a5-175">Year: Senior</span></span>  
  
 <span data-ttu-id="f62a5-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="f62a5-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="f62a5-177">Osada、包括 michiko</span><span class="sxs-lookup"><span data-stu-id="f62a5-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="f62a5-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="f62a5-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="f62a5-179">We feng、Hanying</span><span class="sxs-lookup"><span data-stu-id="f62a5-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="f62a5-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="f62a5-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="f62a5-181">歷年Freshman</span><span class="sxs-lookup"><span data-stu-id="f62a5-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="f62a5-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="f62a5-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="f62a5-183">Garcia、Cesar</span><span class="sxs-lookup"><span data-stu-id="f62a5-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="f62a5-184">下列程式碼中顯示的變化會排序類別年份, 然後依姓氏排序每年中的學生。</span><span class="sxs-lookup"><span data-stu-id="f62a5-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="f62a5-185">如需的詳細`Group By`資訊, 請參閱[group by 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f62a5-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f62a5-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f62a5-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="f62a5-187">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="f62a5-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="f62a5-188">查詢</span><span class="sxs-lookup"><span data-stu-id="f62a5-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="f62a5-189">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f62a5-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f62a5-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="f62a5-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
