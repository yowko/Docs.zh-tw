---
title: 使用 LINQ 轉換資料 (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: c165f78c53cec0417d39320580b812ff01fef68b
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199307"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="19ebb-102">使用 LINQ 轉換資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="19ebb-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]<span data-ttu-id="19ebb-103"> 不只是關於擷取資料。</span><span class="sxs-lookup"><span data-stu-id="19ebb-103"> is not only about retrieving data.</span></span> <span data-ttu-id="19ebb-104">它也是功能強大的資料轉換工具。</span><span class="sxs-lookup"><span data-stu-id="19ebb-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="19ebb-105">使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢，您可以使用來源序列作為輸入，並在許多方面修改它，以建立新的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="19ebb-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="19ebb-106">藉由排序及群組，您可以修改序列本身，而不修改項目本身。</span><span class="sxs-lookup"><span data-stu-id="19ebb-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="19ebb-107">但或許 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 最強大的功能查詢就是能夠建立新的類型。</span><span class="sxs-lookup"><span data-stu-id="19ebb-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="19ebb-108">這是在 [select](../../../../csharp/language-reference/keywords/select-clause.md) 子句中完成。</span><span class="sxs-lookup"><span data-stu-id="19ebb-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="19ebb-109">例如，您可以進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="19ebb-109">For example, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="19ebb-110">將多個輸入序列合併為具有新類型的單一輸出序列。</span><span class="sxs-lookup"><span data-stu-id="19ebb-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
-   <span data-ttu-id="19ebb-111">建立輸出序列，使其項目只包含來源序列中每個項目的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="19ebb-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
-   <span data-ttu-id="19ebb-112">建立輸出序列，使其項目包含對來源資料執行的作業結果。</span><span class="sxs-lookup"><span data-stu-id="19ebb-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
-   <span data-ttu-id="19ebb-113">以不同格式建立輸出序列。</span><span class="sxs-lookup"><span data-stu-id="19ebb-113">Create output sequences in a different format.</span></span> <span data-ttu-id="19ebb-114">比方說，您可以將資料從 SQL 資料列或文字檔轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="19ebb-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="19ebb-115">這些只是一些範例。</span><span class="sxs-lookup"><span data-stu-id="19ebb-115">These are just several examples.</span></span> <span data-ttu-id="19ebb-116">當然，這些轉換可以用各種方式結合在相同的查詢中。</span><span class="sxs-lookup"><span data-stu-id="19ebb-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="19ebb-117">此外，一個查詢的輸出序列也可用作新查詢的輸入序列。</span><span class="sxs-lookup"><span data-stu-id="19ebb-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="19ebb-118">將多個輸入聯結成一個輸出序列</span><span class="sxs-lookup"><span data-stu-id="19ebb-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="19ebb-119">您可以使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢來建立輸出序列，其中包含來自多個輸入序列的項目。</span><span class="sxs-lookup"><span data-stu-id="19ebb-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="19ebb-120">下列範例示範如何結合兩個記憶體中的資料結構，但相同的原則可以套用以合併 XML 或 SQL 或資料集來源的資料。</span><span class="sxs-lookup"><span data-stu-id="19ebb-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="19ebb-121">假設下列兩個類別類型︰</span><span class="sxs-lookup"><span data-stu-id="19ebb-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 <span data-ttu-id="19ebb-122">下列範例顯示查詢：</span><span class="sxs-lookup"><span data-stu-id="19ebb-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 <span data-ttu-id="19ebb-123">如需詳細資訊，請參閱 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md)和 [select 子句](../../../../csharp/language-reference/keywords/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="19ebb-123">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="19ebb-124">選取每個來源項目的子集</span><span class="sxs-lookup"><span data-stu-id="19ebb-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="19ebb-125">有兩種主要方式，可選取來源序列中每個項目的子集︰</span><span class="sxs-lookup"><span data-stu-id="19ebb-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1.  <span data-ttu-id="19ebb-126">若只要選取來源項目的一個成員，請使用點運算。</span><span class="sxs-lookup"><span data-stu-id="19ebb-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="19ebb-127">在下列範例中，假設 `Customer` 物件包含數個公用屬性，包括名為 `City` 的字串。</span><span class="sxs-lookup"><span data-stu-id="19ebb-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="19ebb-128">在執行時，此查詢會產生字串的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="19ebb-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  <span data-ttu-id="19ebb-129">若要建立包含來自來源項目之多個屬性的項目，您可以使用物件初始設定式與具名物件或匿名型別。</span><span class="sxs-lookup"><span data-stu-id="19ebb-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="19ebb-130">下列範例示範如何使用匿名型別封裝來自每個 `Customer` 項目的兩個屬性︰</span><span class="sxs-lookup"><span data-stu-id="19ebb-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="19ebb-131">如需詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)和[匿名型別](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="19ebb-131">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="19ebb-132">將記憶體中的物件轉換成 XML</span><span class="sxs-lookup"><span data-stu-id="19ebb-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="19ebb-133"> 查詢讓您輕鬆地將資料在記憶體中的資料結構、SQL 資料庫、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] 資料集和 XML 資料流或文件之間轉換。</span><span class="sxs-lookup"><span data-stu-id="19ebb-133"> queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="19ebb-134">下列範例會將記憶體中資料結構的物件轉換成 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="19ebb-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 <span data-ttu-id="19ebb-135">該程式碼會產生下列 XML 輸出：</span><span class="sxs-lookup"><span data-stu-id="19ebb-135">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="19ebb-136">如需詳細資訊，請參閱[在 C# 中建立 XML 樹狀結構 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="19ebb-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="19ebb-137">對來源項目執行作業</span><span class="sxs-lookup"><span data-stu-id="19ebb-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="19ebb-138">輸出序列可能不會包含來自來源序列的任何項目或項目屬性。</span><span class="sxs-lookup"><span data-stu-id="19ebb-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="19ebb-139">輸出可能會是使用來源項目作為輸入引數而計算的值序列。</span><span class="sxs-lookup"><span data-stu-id="19ebb-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="19ebb-140">下列簡單的查詢在執行時，會輸出字串的序列，這些字串的值代表了以 `double` 類型之項目的來源序列為基礎的計算。</span><span class="sxs-lookup"><span data-stu-id="19ebb-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19ebb-141">如果查詢會轉譯成某個其他領域，則不支援在查詢運算式中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="19ebb-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="19ebb-142">例如，您無法在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 呼叫一般 C# 方法，因為 SQL Server 沒有它的內容。</span><span class="sxs-lookup"><span data-stu-id="19ebb-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="19ebb-143">不過，您可以將預存程序對應至方法，並呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="19ebb-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="19ebb-144">如需詳細資訊，請參閱[預存程序](../../../../framework/data/adonet/sql/linq/stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="19ebb-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="19ebb-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="19ebb-145">See Also</span></span>  
 [<span data-ttu-id="19ebb-146">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="19ebb-146">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="19ebb-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="19ebb-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="19ebb-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="19ebb-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
 [<span data-ttu-id="19ebb-149">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="19ebb-149">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [<span data-ttu-id="19ebb-150">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="19ebb-150">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="19ebb-151">select 子句</span><span class="sxs-lookup"><span data-stu-id="19ebb-151">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
