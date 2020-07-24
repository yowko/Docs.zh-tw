---
title: 使用 LINQ 轉換資料 (C#)
description: '瞭解如何在 c # 中使用 LINQ 查詢來轉換資料。 您可以使用 select 子句來排序和群組，並建立新的類型來修改序列。'
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
ms.openlocfilehash: 6844cf2aa589f7516a9e40bc604c5f907ec6d311
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104018"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="8a74b-104">使用 LINQ 轉換資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="8a74b-104">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="8a74b-105">語言整合式查詢（LINQ）不只是用來抓取資料。</span><span class="sxs-lookup"><span data-stu-id="8a74b-105">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="8a74b-106">它也是功能強大的資料轉換工具。</span><span class="sxs-lookup"><span data-stu-id="8a74b-106">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="8a74b-107">藉由使用 LINQ 查詢，您可以使用來源序列做為輸入，並以許多方式加以修改以建立新的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="8a74b-107">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="8a74b-108">藉由排序及群組，您可以修改序列本身，而不修改項目本身。</span><span class="sxs-lookup"><span data-stu-id="8a74b-108">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="8a74b-109">但是 LINQ 查詢最強大的功能就是建立新類型的能力。</span><span class="sxs-lookup"><span data-stu-id="8a74b-109">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="8a74b-110">這是在 [select](../../../language-reference/keywords/select-clause.md) 子句中完成。</span><span class="sxs-lookup"><span data-stu-id="8a74b-110">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="8a74b-111">例如，您可以進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="8a74b-111">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="8a74b-112">將多個輸入序列合併為具有新類型的單一輸出序列。</span><span class="sxs-lookup"><span data-stu-id="8a74b-112">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="8a74b-113">建立輸出序列，使其項目只包含來源序列中每個項目的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="8a74b-113">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="8a74b-114">建立輸出序列，使其項目包含對來源資料執行的作業結果。</span><span class="sxs-lookup"><span data-stu-id="8a74b-114">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="8a74b-115">以不同格式建立輸出序列。</span><span class="sxs-lookup"><span data-stu-id="8a74b-115">Create output sequences in a different format.</span></span> <span data-ttu-id="8a74b-116">比方說，您可以將資料從 SQL 資料列或文字檔轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="8a74b-116">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="8a74b-117">這些只是一些範例。</span><span class="sxs-lookup"><span data-stu-id="8a74b-117">These are just several examples.</span></span> <span data-ttu-id="8a74b-118">當然，這些轉換可以用各種方式結合在相同的查詢中。</span><span class="sxs-lookup"><span data-stu-id="8a74b-118">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="8a74b-119">此外，一個查詢的輸出序列也可用作新查詢的輸入序列。</span><span class="sxs-lookup"><span data-stu-id="8a74b-119">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="8a74b-120">將多個輸入聯結成一個輸出序列</span><span class="sxs-lookup"><span data-stu-id="8a74b-120">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="8a74b-121">您可以使用 LINQ 查詢來建立輸出序列，其中包含來自多個輸入序列的元素。</span><span class="sxs-lookup"><span data-stu-id="8a74b-121">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="8a74b-122">下列範例示範如何結合兩個記憶體中的資料結構，但相同的原則可以套用以合併 XML 或 SQL 或資料集來源的資料。</span><span class="sxs-lookup"><span data-stu-id="8a74b-122">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="8a74b-123">假設下列兩個類別類型︰</span><span class="sxs-lookup"><span data-stu-id="8a74b-123">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="8a74b-124">下列範例顯示查詢：</span><span class="sxs-lookup"><span data-stu-id="8a74b-124">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="8a74b-125">如需詳細資訊，請參閱 [join 子句](../../../language-reference/keywords/join-clause.md)和 [select 子句](../../../language-reference/keywords/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="8a74b-125">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="8a74b-126">選取每個來源項目的子集</span><span class="sxs-lookup"><span data-stu-id="8a74b-126">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="8a74b-127">有兩種主要方式，可選取來源序列中每個項目的子集︰</span><span class="sxs-lookup"><span data-stu-id="8a74b-127">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="8a74b-128">若只要選取來源項目的一個成員，請使用點運算。</span><span class="sxs-lookup"><span data-stu-id="8a74b-128">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="8a74b-129">在下列範例中，假設 `Customer` 物件包含數個公用屬性，包括名為 `City` 的字串。</span><span class="sxs-lookup"><span data-stu-id="8a74b-129">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="8a74b-130">在執行時，此查詢會產生字串的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="8a74b-130">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="8a74b-131">若要建立包含來自來源項目之多個屬性的項目，您可以使用物件初始設定式與具名物件或匿名型別。</span><span class="sxs-lookup"><span data-stu-id="8a74b-131">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="8a74b-132">下列範例示範如何使用匿名型別封裝來自每個 `Customer` 項目的兩個屬性︰</span><span class="sxs-lookup"><span data-stu-id="8a74b-132">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="8a74b-133">如需詳細資訊，請參閱[物件和集合初始設定式](../../classes-and-structs/object-and-collection-initializers.md)和[匿名型別](../../classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="8a74b-133">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="8a74b-134">將記憶體中的物件轉換成 XML</span><span class="sxs-lookup"><span data-stu-id="8a74b-134">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="8a74b-135">LINQ 查詢可讓您輕鬆地在記憶體中的資料結構、SQL 資料庫、ADO.NET 資料集和 XML 資料流程或檔之間轉換資料。</span><span class="sxs-lookup"><span data-stu-id="8a74b-135">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="8a74b-136">下列範例會將記憶體中資料結構的物件轉換成 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="8a74b-136">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="8a74b-137">該程式碼會產生下列 XML 輸出：</span><span class="sxs-lookup"><span data-stu-id="8a74b-137">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="8a74b-138">如需詳細資訊，請參閱[在 C# 中建立 XML 樹狀結構 (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="8a74b-138">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="8a74b-139">對來源項目執行作業</span><span class="sxs-lookup"><span data-stu-id="8a74b-139">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="8a74b-140">輸出序列可能不會包含來自來源序列的任何項目或項目屬性。</span><span class="sxs-lookup"><span data-stu-id="8a74b-140">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="8a74b-141">輸出可能會是使用來源項目作為輸入引數而計算的值序列。</span><span class="sxs-lookup"><span data-stu-id="8a74b-141">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="8a74b-142">下列查詢會採用一連串數位來代表圓形的半徑、計算每個半徑的面積，以及傳回包含以匯出區域格式化之字串的輸出序列。</span><span class="sxs-lookup"><span data-stu-id="8a74b-142">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="8a74b-143">輸出序列的每個字串都會使用[字串插補](../../../language-reference/tokens/interpolated.md)來格式化。</span><span class="sxs-lookup"><span data-stu-id="8a74b-143">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="8a74b-144">插補字串 `$` 前面會加上字串的左引號，而且可以在插入字串內的大括弧內執行運算。</span><span class="sxs-lookup"><span data-stu-id="8a74b-144">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="8a74b-145">這些作業一旦執行，就會串連結果。</span><span class="sxs-lookup"><span data-stu-id="8a74b-145">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8a74b-146">如果查詢會轉譯成某個其他領域，則不支援在查詢運算式中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="8a74b-146">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="8a74b-147">例如，您無法在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 呼叫一般 C# 方法，因為 SQL Server 沒有它的內容。</span><span class="sxs-lookup"><span data-stu-id="8a74b-147">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="8a74b-148">不過，您可以將預存程序對應至方法，並呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="8a74b-148">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="8a74b-149">如需詳細資訊，請參閱[預存程序](../../../../framework/data/adonet/sql/linq/stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="8a74b-149">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="8a74b-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a74b-150">See also</span></span>

- [<span data-ttu-id="8a74b-151">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8a74b-151">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="8a74b-152">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8a74b-152">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="8a74b-153">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8a74b-153">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="8a74b-154">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8a74b-154">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="8a74b-155">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="8a74b-155">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="8a74b-156">select 子句</span><span class="sxs-lookup"><span data-stu-id="8a74b-156">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
