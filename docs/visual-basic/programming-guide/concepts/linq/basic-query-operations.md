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
ms.openlocfilehash: 6f4c58b15c33d8d2007069df88b2984e692df0a8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078368"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="a933f-102">基本查詢作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a933f-102">Basic Query Operations (Visual Basic)</span></span>

<span data-ttu-id="a933f-103">本主題提供 Visual Basic 中的語言整合式查詢 (LINQ) 運算式的簡介，以及一些您在查詢中執行的一般作業類型。</span><span class="sxs-lookup"><span data-stu-id="a933f-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="a933f-104">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a933f-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="a933f-105">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="a933f-105">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="a933f-106">查詢</span><span class="sxs-lookup"><span data-stu-id="a933f-106">Queries</span></span>](../../../language-reference/queries/index.md)  
  
 [<span data-ttu-id="a933f-107">逐步解說：在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="a933f-107">Walkthrough: Writing Queries in Visual Basic</span></span>](walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="a933f-108">從) 指定資料來源 (</span><span class="sxs-lookup"><span data-stu-id="a933f-108">Specifying the Data Source (From)</span></span>  

 <span data-ttu-id="a933f-109">在 LINQ 查詢中，第一個步驟是指定您要查詢的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a933f-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="a933f-110">因此， `From` 查詢中的子句一律會最先出現。</span><span class="sxs-lookup"><span data-stu-id="a933f-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="a933f-111">查詢運算子會根據來源的類型來選取和塑造結果。</span><span class="sxs-lookup"><span data-stu-id="a933f-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="a933f-112">`From`子句會指定資料來源、 `customers` 和*範圍變數* `cust` 。</span><span class="sxs-lookup"><span data-stu-id="a933f-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="a933f-113">範圍變數就像迴圈反覆運算變數，但在查詢運算式中，不會發生實際的反復專案。</span><span class="sxs-lookup"><span data-stu-id="a933f-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="a933f-114">執行查詢時，通常會使用 `For Each` 迴圈，範圍變數可作為中每個後續元素的參考 `customers` 。</span><span class="sxs-lookup"><span data-stu-id="a933f-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="a933f-115">因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。</span><span class="sxs-lookup"><span data-stu-id="a933f-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="a933f-116">如需以和不具明確類型撰寫的查詢範例，請參閱 [查詢作業中的類型關聯性 (Visual Basic) ](type-relationships-in-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="a933f-117">如需有關如何 `From` 在 Visual Basic 中使用子句的詳細資訊，請參閱 [from 子句](../../../language-reference/queries/from-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="a933f-118">篩選 (的資料) </span><span class="sxs-lookup"><span data-stu-id="a933f-118">Filtering Data (Where)</span></span>  

 <span data-ttu-id="a933f-119">最常見的查詢作業可能是以布林運算式的形式套用篩選。</span><span class="sxs-lookup"><span data-stu-id="a933f-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="a933f-120">然後，查詢只會傳回運算式為 true 的元素。</span><span class="sxs-lookup"><span data-stu-id="a933f-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="a933f-121">`Where`子句是用來執行篩選。</span><span class="sxs-lookup"><span data-stu-id="a933f-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="a933f-122">篩選準則會指定資料來源中要包含在產生的序列中的元素。</span><span class="sxs-lookup"><span data-stu-id="a933f-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="a933f-123">在下列範例中，只會包含在倫敦有位址的客戶。</span><span class="sxs-lookup"><span data-stu-id="a933f-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="a933f-124">您可以使用邏輯運算子（例如 `And` 和） `Or` 來合併子句中的篩選條件運算式 `Where` 。</span><span class="sxs-lookup"><span data-stu-id="a933f-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="a933f-125">例如，若只要傳回來自倫敦且名稱為 Devon 的客戶，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a933f-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="a933f-126">若要傳回倫敦或巴黎的客戶，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a933f-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="a933f-127">如需有關如何 `Where` 在 Visual Basic 中使用子句的詳細資訊，請參閱 [Where 子句](../../../language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="a933f-128">依) 排序資料 (順序</span><span class="sxs-lookup"><span data-stu-id="a933f-128">Ordering Data (Order By)</span></span>  

 <span data-ttu-id="a933f-129">將傳回的資料排序成特定的順序通常很方便。</span><span class="sxs-lookup"><span data-stu-id="a933f-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="a933f-130">`Order By`子句會讓傳回序列中的專案在指定的欄位上排序。</span><span class="sxs-lookup"><span data-stu-id="a933f-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="a933f-131">例如，下列查詢會根據屬性來排序結果 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="a933f-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="a933f-132">因為 `Name` 是字串，所以傳回的資料會依字母順序排序，從 a 到 Z。</span><span class="sxs-lookup"><span data-stu-id="a933f-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="a933f-133">若要以相反順序排序結果 (從 Z 到 A)，請使用 `Order By...Descending` 子句。</span><span class="sxs-lookup"><span data-stu-id="a933f-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="a933f-134">預設值為未 `Ascending` `Ascending` 指定或時 `Descending` 。</span><span class="sxs-lookup"><span data-stu-id="a933f-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="a933f-135">如需有關如何 `Order By` 在 Visual Basic 中使用子句的詳細資訊，請參閱 [Order by 子句](../../../language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="a933f-136">選取資料 (選取) </span><span class="sxs-lookup"><span data-stu-id="a933f-136">Selecting Data (Select)</span></span>  

 <span data-ttu-id="a933f-137">`Select`子句會指定所傳回元素的表單和內容。</span><span class="sxs-lookup"><span data-stu-id="a933f-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="a933f-138">例如，您可以指定您的結果是否包含完整的 `Customer` 物件、只有一個 `Customer` 屬性、屬性的子集、來自各種資料來源的屬性組合，或是根據計算的一些新結果型別。</span><span class="sxs-lookup"><span data-stu-id="a933f-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="a933f-139">`Select` 子句不只產生一份來源項目時，作業稱為「投影」\*\*。</span><span class="sxs-lookup"><span data-stu-id="a933f-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="a933f-140">若要取出由完整物件組成的集合 `Customer` ，請選取範圍變數本身：</span><span class="sxs-lookup"><span data-stu-id="a933f-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="a933f-141">如果 `Customer` 實例是具有許多欄位的大型物件，而且您想要取出的所有都是名稱，您可以選取 `cust.Name` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a933f-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="a933f-142">區欄位型別推斷會將結果類型從物件的集合變更 `Customer` 為字串的集合。</span><span class="sxs-lookup"><span data-stu-id="a933f-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a933f-143">若要選取資料來源中的多個欄位，您有兩個選擇：</span><span class="sxs-lookup"><span data-stu-id="a933f-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="a933f-144">在 `Select` 子句中，指定您想要包含在結果中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a933f-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="a933f-145">編譯器會定義具有這些欄位做為其屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="a933f-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="a933f-146">如需詳細資訊，請參閱 [匿名型別](../../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-146">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="a933f-147">因為下列範例中傳回的元素是匿名型別的實例，所以您無法在程式碼中的其他地方依名稱參考該型別。</span><span class="sxs-lookup"><span data-stu-id="a933f-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="a933f-148">型別的編譯器指定名稱包含了在一般 Visual Basic 程式碼中不正確字元。</span><span class="sxs-lookup"><span data-stu-id="a933f-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="a933f-149">在下列範例中，查詢所傳回之集合中的元素 `londonCusts4` 是匿名型別的實例。</span><span class="sxs-lookup"><span data-stu-id="a933f-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="a933f-150">-或-</span><span class="sxs-lookup"><span data-stu-id="a933f-150">-or-</span></span>  
  
- <span data-ttu-id="a933f-151">定義命名的型別，其中包含您想要包含在結果中的特定欄位，以及在子句中建立和初始化型別的實例 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="a933f-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="a933f-152">只有當您必須在傳回的集合之外使用個別的結果，或是在方法呼叫中將它們傳遞為參數時，才使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a933f-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="a933f-153">`londonCusts5`下列範例中的型別是 NamePhone) 的 IEnumerable (。</span><span class="sxs-lookup"><span data-stu-id="a933f-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="a933f-154">如需有關如何 `Select` 在 Visual Basic 中使用子句的詳細資訊，請參閱 [Select 子句](../../../language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="a933f-155">聯結資料 (聯結和群組聯結) </span><span class="sxs-lookup"><span data-stu-id="a933f-155">Joining Data (Join and Group Join)</span></span>  

 <span data-ttu-id="a933f-156">您可以透過數種方式在子句中結合多個資料來源 `From` 。</span><span class="sxs-lookup"><span data-stu-id="a933f-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="a933f-157">例如，下列程式碼會使用兩個數據源，並在結果中隱含地結合兩個數據源的屬性。</span><span class="sxs-lookup"><span data-stu-id="a933f-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="a933f-158">查詢會選取其姓氏開頭為母音的學生。</span><span class="sxs-lookup"><span data-stu-id="a933f-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="a933f-159">您可以使用在 [如何：建立專案清單](how-to-create-a-list-of-items.md)中建立的學生清單來執行此程式碼。</span><span class="sxs-lookup"><span data-stu-id="a933f-159">You can run this code with the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="a933f-160">`Join`關鍵字相當於 `INNER JOIN` SQL 中的。</span><span class="sxs-lookup"><span data-stu-id="a933f-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="a933f-161">它會根據兩個集合中的專案之間相符的索引鍵值來合併兩個集合。</span><span class="sxs-lookup"><span data-stu-id="a933f-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="a933f-162">此查詢會傳回具有相符索引鍵值的所有或部分集合元素。</span><span class="sxs-lookup"><span data-stu-id="a933f-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="a933f-163">例如，下列程式碼會複製先前隱含聯結的動作。</span><span class="sxs-lookup"><span data-stu-id="a933f-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="a933f-164">`Group Join` 將集合結合成單一階層式集合，就像 `LEFT JOIN` 在 SQL 中一樣。</span><span class="sxs-lookup"><span data-stu-id="a933f-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="a933f-165">如需詳細資訊，請參閱 [聯結子句](../../../language-reference/queries/join-clause.md) 和 [群組聯結子句](../../../language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-165">For more information, see [Join Clause](../../../language-reference/queries/join-clause.md) and [Group Join Clause](../../../language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="a933f-166">依) 將資料群組 (群組</span><span class="sxs-lookup"><span data-stu-id="a933f-166">Grouping Data (Group By)</span></span>  

 <span data-ttu-id="a933f-167">您可以加入 `Group By` 子句，以根據專案的一或多個欄位，將查詢結果中的元素分組。</span><span class="sxs-lookup"><span data-stu-id="a933f-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="a933f-168">例如，下列程式碼會依類別年度分組學生。</span><span class="sxs-lookup"><span data-stu-id="a933f-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="a933f-169">如果您使用在 how [to：建立專案清單](how-to-create-a-list-of-items.md)中建立的學生清單來執行此程式碼，則語句的輸出 `For Each` 為：</span><span class="sxs-lookup"><span data-stu-id="a933f-169">If you run this code using the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="a933f-170">年：初級</span><span class="sxs-lookup"><span data-stu-id="a933f-170">Year: Junior</span></span>  
  
 <span data-ttu-id="a933f-171">Ilsi，Michael</span><span class="sxs-lookup"><span data-stu-id="a933f-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="a933f-172">Garcia、Hugo</span><span class="sxs-lookup"><span data-stu-id="a933f-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="a933f-173">Garcia、Debra</span><span class="sxs-lookup"><span data-stu-id="a933f-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="a933f-174">Ilsi、Lance</span><span class="sxs-lookup"><span data-stu-id="a933f-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="a933f-175">Year：資深</span><span class="sxs-lookup"><span data-stu-id="a933f-175">Year: Senior</span></span>  
  
 <span data-ttu-id="a933f-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="a933f-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="a933f-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="a933f-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="a933f-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="a933f-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="a933f-179">We feng、Hanying</span><span class="sxs-lookup"><span data-stu-id="a933f-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="a933f-180">Adams，Terry</span><span class="sxs-lookup"><span data-stu-id="a933f-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="a933f-181">Year：年級</span><span class="sxs-lookup"><span data-stu-id="a933f-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="a933f-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="a933f-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="a933f-183">Garcia、Cesar</span><span class="sxs-lookup"><span data-stu-id="a933f-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="a933f-184">下列程式碼中顯示的變化會排列類別年度的順序，然後依姓氏在每一年中訂購學生。</span><span class="sxs-lookup"><span data-stu-id="a933f-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="a933f-185">如需的詳細資訊 `Group By` ，請參閱 [Group by 子句](../../../language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="a933f-185">For more information about `Group By`, see [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a933f-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a933f-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="a933f-187">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="a933f-187">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="a933f-188">查詢</span><span class="sxs-lookup"><span data-stu-id="a933f-188">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="a933f-189">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a933f-189">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="a933f-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="a933f-190">LINQ</span></span>](../../language-features/linq/index.md)
