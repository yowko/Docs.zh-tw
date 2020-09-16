---
title: 使用 LINQ 轉換資料 (C#)
description: '瞭解如何在 c # 中使用 LINQ 查詢來轉換資料。 您可以使用 select 子句來排序和分組，並建立新的類型，以修改序列。'
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
ms.openlocfilehash: af08938b6b8f169ded2180529c2b4aadebefef55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558806"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="14102-104">使用 LINQ 轉換資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="14102-104">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="14102-105"> (LINQ) 的語言整合式查詢，不只是要抓取資料。</span><span class="sxs-lookup"><span data-stu-id="14102-105">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="14102-106">它也是功能強大的資料轉換工具。</span><span class="sxs-lookup"><span data-stu-id="14102-106">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="14102-107">藉由使用 LINQ 查詢，您可以使用來源序列作為輸入，並以許多方式修改它，以建立新的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="14102-107">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="14102-108">藉由排序及群組，您可以修改序列本身，而不修改項目本身。</span><span class="sxs-lookup"><span data-stu-id="14102-108">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="14102-109">但 LINQ 查詢最強大的功能是能夠建立新的類型。</span><span class="sxs-lookup"><span data-stu-id="14102-109">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="14102-110">這是在 [select](../../../language-reference/keywords/select-clause.md) 子句中完成。</span><span class="sxs-lookup"><span data-stu-id="14102-110">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="14102-111">例如，您可以進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="14102-111">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="14102-112">將多個輸入序列合併為具有新類型的單一輸出序列。</span><span class="sxs-lookup"><span data-stu-id="14102-112">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="14102-113">建立輸出序列，使其項目只包含來源序列中每個項目的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="14102-113">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="14102-114">建立輸出序列，使其項目包含對來源資料執行的作業結果。</span><span class="sxs-lookup"><span data-stu-id="14102-114">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="14102-115">以不同格式建立輸出序列。</span><span class="sxs-lookup"><span data-stu-id="14102-115">Create output sequences in a different format.</span></span> <span data-ttu-id="14102-116">比方說，您可以將資料從 SQL 資料列或文字檔轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="14102-116">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="14102-117">這些只是一些範例。</span><span class="sxs-lookup"><span data-stu-id="14102-117">These are just several examples.</span></span> <span data-ttu-id="14102-118">當然，這些轉換可以用各種方式結合在相同的查詢中。</span><span class="sxs-lookup"><span data-stu-id="14102-118">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="14102-119">此外，一個查詢的輸出序列也可用作新查詢的輸入序列。</span><span class="sxs-lookup"><span data-stu-id="14102-119">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="14102-120">將多個輸入聯結成一個輸出序列</span><span class="sxs-lookup"><span data-stu-id="14102-120">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="14102-121">您可以使用 LINQ 查詢來建立包含來自多個輸入序列之元素的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="14102-121">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="14102-122">下列範例示範如何結合兩個記憶體中的資料結構，但相同的原則可以套用以合併 XML 或 SQL 或資料集來源的資料。</span><span class="sxs-lookup"><span data-stu-id="14102-122">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="14102-123">假設下列兩個類別類型︰</span><span class="sxs-lookup"><span data-stu-id="14102-123">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="14102-124">下列範例顯示查詢：</span><span class="sxs-lookup"><span data-stu-id="14102-124">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="14102-125">如需詳細資訊，請參閱 [join 子句](../../../language-reference/keywords/join-clause.md)和 [select 子句](../../../language-reference/keywords/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="14102-125">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="14102-126">選取每個來源項目的子集</span><span class="sxs-lookup"><span data-stu-id="14102-126">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="14102-127">有兩種主要方式，可選取來源序列中每個項目的子集︰</span><span class="sxs-lookup"><span data-stu-id="14102-127">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="14102-128">若只要選取來源項目的一個成員，請使用點運算。</span><span class="sxs-lookup"><span data-stu-id="14102-128">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="14102-129">在下列範例中，假設 `Customer` 物件包含數個公用屬性，包括名為 `City` 的字串。</span><span class="sxs-lookup"><span data-stu-id="14102-129">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="14102-130">在執行時，此查詢會產生字串的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="14102-130">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="14102-131">若要建立包含來自來源項目之多個屬性的項目，您可以使用物件初始設定式與具名物件或匿名型別。</span><span class="sxs-lookup"><span data-stu-id="14102-131">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="14102-132">下列範例示範如何使用匿名型別封裝來自每個 `Customer` 項目的兩個屬性︰</span><span class="sxs-lookup"><span data-stu-id="14102-132">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="14102-133">如需詳細資訊，請參閱[物件和集合初始設定式](../../classes-and-structs/object-and-collection-initializers.md)和[匿名型別](../../classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="14102-133">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="14102-134">將記憶體中的物件轉換成 XML</span><span class="sxs-lookup"><span data-stu-id="14102-134">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="14102-135">LINQ 查詢可讓您輕鬆地在記憶體中的資料結構、SQL 資料庫、ADO.NET 資料集和 XML 資料流程或檔之間轉換資料。</span><span class="sxs-lookup"><span data-stu-id="14102-135">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="14102-136">下列範例會將記憶體中資料結構的物件轉換成 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="14102-136">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="14102-137">該程式碼會產生下列 XML 輸出：</span><span class="sxs-lookup"><span data-stu-id="14102-137">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="14102-138">如需詳細資訊，請參閱[在 C# 中建立 XML 樹狀結構 (LINQ to XML)](../../../../standard/linq/create-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="14102-138">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../standard/linq/create-xml-trees.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="14102-139">對來源項目執行作業</span><span class="sxs-lookup"><span data-stu-id="14102-139">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="14102-140">輸出序列可能不會包含來自來源序列的任何項目或項目屬性。</span><span class="sxs-lookup"><span data-stu-id="14102-140">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="14102-141">輸出可能會是使用來源項目作為輸入引數而計算的值序列。</span><span class="sxs-lookup"><span data-stu-id="14102-141">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="14102-142">下列查詢會採用一連串的數位來表示圓形的半徑、計算每個半徑的區域，並傳回包含以計算區域格式化之字串的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="14102-142">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="14102-143">輸出序列的每個字串都會使用 [字串插補](../../../language-reference/tokens/interpolated.md)來格式化。</span><span class="sxs-lookup"><span data-stu-id="14102-143">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="14102-144">內插字串的 `$` 左引號前面會有一個，而且可以在插入字串內的大括弧內執行作業。</span><span class="sxs-lookup"><span data-stu-id="14102-144">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="14102-145">一旦執行這些作業，就會串連結果。</span><span class="sxs-lookup"><span data-stu-id="14102-145">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="14102-146">如果查詢會轉譯成某個其他領域，則不支援在查詢運算式中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="14102-146">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="14102-147">例如，您無法在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 呼叫一般 C# 方法，因為 SQL Server 沒有它的內容。</span><span class="sxs-lookup"><span data-stu-id="14102-147">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="14102-148">不過，您可以將預存程序對應至方法，並呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="14102-148">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="14102-149">如需詳細資訊，請參閱[預存程序](../../../../framework/data/adonet/sql/linq/stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="14102-149">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="14102-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14102-150">See also</span></span>

- [<span data-ttu-id="14102-151">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="14102-151">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="14102-152">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="14102-152">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="14102-153">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="14102-153">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="14102-154">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="14102-154">LINQ to XML (C#)</span></span>](../../../../standard/linq/linq-xml-overview.md)
- [<span data-ttu-id="14102-155">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="14102-155">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="14102-156">select 子句</span><span class="sxs-lookup"><span data-stu-id="14102-156">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
