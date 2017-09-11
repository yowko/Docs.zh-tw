---
title: "基本查詢作業 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1ced446d6646bd26b9169f5894138e12a38efde7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="e2754-102">基本查詢作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2754-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="e2754-103">本主題提供簡介[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]運算式在 Visual Basic，和一些您在查詢中執行的作業一般類型。</span><span class="sxs-lookup"><span data-stu-id="e2754-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="e2754-104">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="e2754-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="e2754-105">在 Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="e2754-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="e2754-106">查詢</span><span class="sxs-lookup"><span data-stu-id="e2754-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [<span data-ttu-id="e2754-107">逐步解說︰ 在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="e2754-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="e2754-108">指定資料來源 (From)</span><span class="sxs-lookup"><span data-stu-id="e2754-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="e2754-109">在[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢中，第一個步驟是指定您想要查詢的資料來源。</span><span class="sxs-lookup"><span data-stu-id="e2754-109">In a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="e2754-110">因此，`From`子句的查詢中一律是第一次。</span><span class="sxs-lookup"><span data-stu-id="e2754-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="e2754-111">查詢運算子來選取和塑造結果的來源類型為基礎。</span><span class="sxs-lookup"><span data-stu-id="e2754-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 <span data-ttu-id="e2754-112">[!code-vb[VbLINQBasicOps #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-112">[!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]</span></span>  
  
 <span data-ttu-id="e2754-113">`From`子句指定的資料來源， `customers`，和*範圍變數*， `cust`。</span><span class="sxs-lookup"><span data-stu-id="e2754-113">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="e2754-114">範圍變數是迴圈反覆運算變數之外，像是在查詢運算式中，實際的反覆項目就會發生。</span><span class="sxs-lookup"><span data-stu-id="e2754-114">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="e2754-115">查詢執行時，通常使用`For Each`迴圈中，做為在每個後續項目的參考的範圍變數`customers`。</span><span class="sxs-lookup"><span data-stu-id="e2754-115">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="e2754-116">因為編譯器可以推斷的型別`cust`，您不需要明確指定。</span><span class="sxs-lookup"><span data-stu-id="e2754-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="e2754-117">有關撰寫，而不需要明確輸入查詢的詳細資訊，請參閱[查詢作業 (Visual Basic) 中的型別關聯性](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-117">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="e2754-118">如需有關如何使用`From`子句在 Visual Basic，請參閱[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-118">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="e2754-119">篩選資料 （位置）</span><span class="sxs-lookup"><span data-stu-id="e2754-119">Filtering Data (Where)</span></span>  
 <span data-ttu-id="e2754-120">可能的最常見的查詢作業套用篩選器的布林運算式的形式。</span><span class="sxs-lookup"><span data-stu-id="e2754-120">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="e2754-121">接著，查詢會在運算式為 true 的項目。</span><span class="sxs-lookup"><span data-stu-id="e2754-121">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="e2754-122">A`Where`子句用來執行篩選。</span><span class="sxs-lookup"><span data-stu-id="e2754-122">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="e2754-123">篩選器指定要包含在結果序列中的資料來源中的哪些項目。</span><span class="sxs-lookup"><span data-stu-id="e2754-123">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="e2754-124">在下列範例中，只具有位址，在倫敦的客戶會包含。</span><span class="sxs-lookup"><span data-stu-id="e2754-124">In the following example, only those customers who have an address in London are included.</span></span>  
  
 <span data-ttu-id="e2754-125">[!code-vb[VbLINQBasicOps #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-125">[!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]</span></span>  
  
 <span data-ttu-id="e2754-126">您可以使用邏輯運算子，例如`And`和`Or`結合篩選條件運算式中的`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="e2754-126">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="e2754-127">例如，如果要傳回的只有這些客戶倫敦 （london） 以及其名稱是 Devon，使用下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="e2754-127">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="e2754-128">若要傳回倫敦或巴黎的客戶，使用下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="e2754-128">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="e2754-129">如需有關如何使用`Where`子句在 Visual Basic，請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-129">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="e2754-130">排序資料 (Order By)</span><span class="sxs-lookup"><span data-stu-id="e2754-130">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="e2754-131">通常很方便地為特定的順序排序傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="e2754-131">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="e2754-132">`Order By`子句便會傳回指定之的欄位或欄位排序序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="e2754-132">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="e2754-133">例如，下列查詢會排序結果根據`Name`屬性。</span><span class="sxs-lookup"><span data-stu-id="e2754-133">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="e2754-134">因為`Name`是一個字串，將英文字母順序排序傳回的資料，從 A 到 Z。</span><span class="sxs-lookup"><span data-stu-id="e2754-134">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 <span data-ttu-id="e2754-135">[!code-vb[VbLINQBasicOps #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-135">[!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]</span></span>  
  
 <span data-ttu-id="e2754-136">若要從 Z 到 A，相反的順序排序結果使用`Order By...Descending`子句。</span><span class="sxs-lookup"><span data-stu-id="e2754-136">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="e2754-137">預設值是`Ascending`時都不`Ascending`或`Descending`指定。</span><span class="sxs-lookup"><span data-stu-id="e2754-137">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="e2754-138">如需有關如何使用`Order By`子句在 Visual Basic，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-138">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="e2754-139">選取 (Select) 的資料</span><span class="sxs-lookup"><span data-stu-id="e2754-139">Selecting Data (Select)</span></span>  
 <span data-ttu-id="e2754-140">`Select`子句指定的格式和內容傳回項目。</span><span class="sxs-lookup"><span data-stu-id="e2754-140">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="e2754-141">例如，您可以指定是否您的結果將包含完整`Customer`物件，其中一個`Customer`屬性、 屬性的子集、 從各種資料來源或一些新的結果型別屬性的組合為基礎的計算。</span><span class="sxs-lookup"><span data-stu-id="e2754-141">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="e2754-142">當`Select`子句會產生一份來源項目以外，在呼叫作業*投影*。</span><span class="sxs-lookup"><span data-stu-id="e2754-142">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="e2754-143">若要擷取集合，其中包含完整`Customer`物件選取範圍變數本身︰</span><span class="sxs-lookup"><span data-stu-id="e2754-143">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 <span data-ttu-id="e2754-144">[!code-vb[VbLINQBasicOps #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-144">[!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]</span></span>  
  
 <span data-ttu-id="e2754-145">如果`Customer`執行個體的大型物件，會有許多欄位，以及所有您想要擷取並名稱，您可以選取`cust.Name`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e2754-145">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="e2754-146">這會變更的結果型別集合中的區域類型推斷會辨識`Customer`的字串集合的物件。</span><span class="sxs-lookup"><span data-stu-id="e2754-146">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 <span data-ttu-id="e2754-147">[!code-vb[VbLINQBasicOps #&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-147">[!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]</span></span>  
  
 <span data-ttu-id="e2754-148">若要選取多個欄位從資料來源，您有兩個選擇︰</span><span class="sxs-lookup"><span data-stu-id="e2754-148">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="e2754-149">在`Select`子句，指定您想要包含在結果中的欄位。</span><span class="sxs-lookup"><span data-stu-id="e2754-149">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="e2754-150">編譯器會在定義這些欄位做為其屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="e2754-150">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="e2754-151">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-151">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="e2754-152">傳回的項目，在下列範例中是以匿名型別的執行個體，因為您無法為型別依名稱參考其他位置中您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2754-152">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="e2754-153">編譯器指定類型名稱包含在標準的 Visual Basic 程式碼中無效的字元。</span><span class="sxs-lookup"><span data-stu-id="e2754-153">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="e2754-154">在下列範例中的查詢所傳回的集合中的項目`londonCusts4`匿名型別的執行個體</span><span class="sxs-lookup"><span data-stu-id="e2754-154">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     <span data-ttu-id="e2754-155">[!code-vb[VbLINQBasicOps #&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-155">[!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]</span></span>  
  
     <span data-ttu-id="e2754-156">-或-</span><span class="sxs-lookup"><span data-stu-id="e2754-156">-or-</span></span>  
  
-   <span data-ttu-id="e2754-157">定義具名型別，其中包含您想要包含在結果中，以及建立和初始化中的型別之執行個體的特定欄位`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="e2754-157">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="e2754-158">只有當您需要使用個別的結果，外部集合中傳回，或如果您需要將它們傳遞做為方法呼叫中的參數，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="e2754-158">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="e2754-159">型別`londonCusts5`在下列範例中是 IEnumerable (Of NamePhone)。</span><span class="sxs-lookup"><span data-stu-id="e2754-159">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     <span data-ttu-id="e2754-160">[!code-vb[VbLINQBasicOps #&7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-160">[!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]</span></span>  
  
     <span data-ttu-id="e2754-161">[!code-vb[VbLINQBasicOps #&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-161">[!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]</span></span>  
  
 <span data-ttu-id="e2754-162">如需有關如何使用`Select`子句在 Visual Basic，請參閱[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-162">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="e2754-163">聯結 （聯結和群組聯結） 的資料</span><span class="sxs-lookup"><span data-stu-id="e2754-163">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="e2754-164">您可以結合多個資料來源中的`From`子句以數種方式。</span><span class="sxs-lookup"><span data-stu-id="e2754-164">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="e2754-165">例如，下列程式碼會使用兩個資料來源，並以隱含方式結合這兩者的結果中的屬性。</span><span class="sxs-lookup"><span data-stu-id="e2754-165">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="e2754-166">查詢會選取姓氏開頭為母音的學生。</span><span class="sxs-lookup"><span data-stu-id="e2754-166">The query selects students whose last names start with a vowel.</span></span>  
  
 <span data-ttu-id="e2754-167">[!code-vb[VbLINQBasicOps #&9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-167">[!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2754-168">您可以執行此程式碼中建立的學生清單[How to︰ 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-168">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="e2754-169">`Join`關鍵字相當於`INNER JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="e2754-169">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="e2754-170">它結合了兩個集合中的項目之間的相符索引鍵值為基礎的兩個集合。</span><span class="sxs-lookup"><span data-stu-id="e2754-170">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="e2754-171">查詢會傳回全部或部分有相符的索引鍵值的集合項目。</span><span class="sxs-lookup"><span data-stu-id="e2754-171">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="e2754-172">例如，下列程式碼複製先前的隱含聯結的動作。</span><span class="sxs-lookup"><span data-stu-id="e2754-172">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 <span data-ttu-id="e2754-173">[!code-vb[VbLINQBasicOps #&10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-173">[!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]</span></span>  
  
 <span data-ttu-id="e2754-174">`Group Join`將集合合併成單一的階層式集合，就像是`LEFT JOIN`SQL 中。</span><span class="sxs-lookup"><span data-stu-id="e2754-174">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="e2754-175">如需詳細資訊，請參閱[Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)和[Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-175">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="e2754-176">群組資料 （依群組）</span><span class="sxs-lookup"><span data-stu-id="e2754-176">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="e2754-177">您可以加入`Group By`子句分組查詢結果，根據項目的一或多個欄位中的項目。</span><span class="sxs-lookup"><span data-stu-id="e2754-177">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="e2754-178">例如，下列程式碼會將學生分組類別年。</span><span class="sxs-lookup"><span data-stu-id="e2754-178">For example, the following code groups students by class year.</span></span>  
  
 <span data-ttu-id="e2754-179">[!code-vb[VbLINQBasicOps #&11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-179">[!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]</span></span>  
  
 <span data-ttu-id="e2754-180">如果您執行此程式碼使用的清單中建立的學生[How to︰ 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)，從輸出`For Each`陳述式︰</span><span class="sxs-lookup"><span data-stu-id="e2754-180">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="e2754-181">年份︰ 基礎</span><span class="sxs-lookup"><span data-stu-id="e2754-181">Year: Junior</span></span>  
  
 <span data-ttu-id="e2754-182">Tucker Michael</span><span class="sxs-lookup"><span data-stu-id="e2754-182">Tucker, Michael</span></span>  
  
 <span data-ttu-id="e2754-183">Garcia Hugo</span><span class="sxs-lookup"><span data-stu-id="e2754-183">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="e2754-184">Garcia Debra</span><span class="sxs-lookup"><span data-stu-id="e2754-184">Garcia, Debra</span></span>  
  
 <span data-ttu-id="e2754-185">Tucker 騎士</span><span class="sxs-lookup"><span data-stu-id="e2754-185">Tucker, Lance</span></span>  
  
 <span data-ttu-id="e2754-186">年份︰ 資深</span><span class="sxs-lookup"><span data-stu-id="e2754-186">Year: Senior</span></span>  
  
 <span data-ttu-id="e2754-187">Omelchenko Svetlana</span><span class="sxs-lookup"><span data-stu-id="e2754-187">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="e2754-188">Osada Michiko</span><span class="sxs-lookup"><span data-stu-id="e2754-188">Osada, Michiko</span></span>  
  
 <span data-ttu-id="e2754-189">Fakhouri Fadi</span><span class="sxs-lookup"><span data-stu-id="e2754-189">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="e2754-190">Hanying Feng</span><span class="sxs-lookup"><span data-stu-id="e2754-190">Feng, Hanying</span></span>  
  
 <span data-ttu-id="e2754-191">Adams Terry</span><span class="sxs-lookup"><span data-stu-id="e2754-191">Adams, Terry</span></span>  
  
 <span data-ttu-id="e2754-192">年份︰ 包括新生諮詢人員</span><span class="sxs-lookup"><span data-stu-id="e2754-192">Year: Freshman</span></span>  
  
 <span data-ttu-id="e2754-193">Mortensen Sven</span><span class="sxs-lookup"><span data-stu-id="e2754-193">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="e2754-194">Garcia Cesar</span><span class="sxs-lookup"><span data-stu-id="e2754-194">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="e2754-195">下列程式碼所示的變化年級，並依據姓氏再排序每年的學生。</span><span class="sxs-lookup"><span data-stu-id="e2754-195">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 <span data-ttu-id="e2754-196">[!code-vb[VbLINQBasicOps #&12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2754-196">[!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]</span></span>  
  
 <span data-ttu-id="e2754-197">如需詳細資訊`Group By`，請參閱[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-197">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2754-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2754-198">See Also</span></span>  
 <span data-ttu-id="e2754-199"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="e2754-199"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="e2754-200"> [在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="e2754-200"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="e2754-201"> [查詢](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="e2754-201"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="e2754-202"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e2754-202"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="e2754-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="e2754-203"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)</span></span>
