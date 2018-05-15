---
title: 已編譯的查詢 (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 37b80a6a7411bc987beb75ebd62778f9589f67e5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="compiled-queries--linq-to-entities"></a><span data-ttu-id="eaca3-102">已編譯的查詢 (LINQ to Entities)</span><span class="sxs-lookup"><span data-stu-id="eaca3-102">Compiled Queries  (LINQ to Entities)</span></span>
<span data-ttu-id="eaca3-103">當您的應用程式執行了 Entity Framework 中結構類似的查詢多次時，您可經常增加效能，其方式是編譯查詢一次，然後使用不同的參數執行查詢多次。</span><span class="sxs-lookup"><span data-stu-id="eaca3-103">When you have an application that executes structurally similar queries many times in the Entity Framework, you can frequently increase performance by compiling the query one time and executing it several times with different parameters.</span></span> <span data-ttu-id="eaca3-104">例如，應用程式可能必須擷取特定城市中的所有客戶；此城市是使用者在執行階段於表單中所指定。</span><span class="sxs-lookup"><span data-stu-id="eaca3-104">For example, an application might have to retrieve all the customers in a particular city; the city is specified at runtime by the user in a form.</span></span> <span data-ttu-id="eaca3-105">LINQ to Entities 支援針對這個用途所編譯的查詢。</span><span class="sxs-lookup"><span data-stu-id="eaca3-105">LINQ to Entities supports using compiled queries for this purpose.</span></span>  
  
 <span data-ttu-id="eaca3-106">從 .NET Framework 4.5 開始會自動快取 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="eaca3-106">Starting with the .NET Framework 4.5, LINQ queries are cached automatically.</span></span> <span data-ttu-id="eaca3-107">不過，之後執行時您仍可以使用已編譯的 LINQ 查詢減少這種成本，且已編譯查詢可能比自動快取的 LINQ 查詢更有效率。</span><span class="sxs-lookup"><span data-stu-id="eaca3-107">However, you can still use compiled LINQ queries to reduce this cost in later executions and compiled queries can be more efficient than LINQ queries that are automatically cached.</span></span> <span data-ttu-id="eaca3-108">請注意，不會自動快取將 `Enumerable.Contains` 運算子套用至記憶體中集合的 LINQ to Entities 查詢。</span><span class="sxs-lookup"><span data-stu-id="eaca3-108">Note that LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="eaca3-109">此外也不允許在已編譯的 LINQ 查詢中參數化記憶體中的集合。</span><span class="sxs-lookup"><span data-stu-id="eaca3-109">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
 <span data-ttu-id="eaca3-110"><xref:System.Data.Objects.CompiledQuery> 類別提供查詢的編譯和快取以供重複使用。</span><span class="sxs-lookup"><span data-stu-id="eaca3-110">The <xref:System.Data.Objects.CompiledQuery> class provides compilation and caching of queries for reuse.</span></span> <span data-ttu-id="eaca3-111">就概念而言，這個類別包含數個多載之 <xref:System.Data.Objects.CompiledQuery> 的 `Compile` 方法。</span><span class="sxs-lookup"><span data-stu-id="eaca3-111">Conceptually, this class contains a <xref:System.Data.Objects.CompiledQuery>'s `Compile` method with several overloads.</span></span> <span data-ttu-id="eaca3-112">呼叫 `Compile` 方法可建立新委派來代表已編譯的查詢。</span><span class="sxs-lookup"><span data-stu-id="eaca3-112">Call the `Compile` method to create a new delegate to represent the compiled query.</span></span> <span data-ttu-id="eaca3-113">`Compile` 所提供的 <xref:System.Data.Objects.ObjectContext> 方法和參數值會傳回一個產生某個結果 (例如 <xref:System.Linq.IQueryable%601> 執行個體) 的委派。</span><span class="sxs-lookup"><span data-stu-id="eaca3-113">The `Compile` methods, provided with a <xref:System.Data.Objects.ObjectContext> and parameter values, return a delegate that produces some result (such as an <xref:System.Linq.IQueryable%601> instance).</span></span> <span data-ttu-id="eaca3-114">此查詢只會在第一次執行期間編譯一次。</span><span class="sxs-lookup"><span data-stu-id="eaca3-114">The query compiles once during only the first execution.</span></span> <span data-ttu-id="eaca3-115">不過，您之後無法變更在編譯階段中，針對查詢所設定的合併選項。</span><span class="sxs-lookup"><span data-stu-id="eaca3-115">The merge options set for the query at the time of the compilation cannot be changed later.</span></span> <span data-ttu-id="eaca3-116">一旦查詢已編譯之後，您就只能提供基本型別的參數，但是無法取代會變更產生之 SQL 的查詢部分。</span><span class="sxs-lookup"><span data-stu-id="eaca3-116">Once the query is compiled you can only supply parameters of primitive type but you cannot replace parts of the query that would change the generated SQL.</span></span> <span data-ttu-id="eaca3-117">如需詳細資訊，請參閱[Entity Framework 合併選項和編譯的查詢](http://go.microsoft.com/fwlink/?LinkId=199591)</span><span class="sxs-lookup"><span data-stu-id="eaca3-117">For more information, see [Entity Framework Merge Options and Compiled Queries](http://go.microsoft.com/fwlink/?LinkId=199591)</span></span>  
  
 <span data-ttu-id="eaca3-118">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]查詢運算式，<xref:System.Data.Objects.CompiledQuery>的`Compile`方法所編譯由其中一個泛型`Func`委派，例如<xref:System.Func%605>。</span><span class="sxs-lookup"><span data-stu-id="eaca3-118">The [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query expression that the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method compiles is represented by one of the generic `Func` delegates, such as <xref:System.Func%605>.</span></span> <span data-ttu-id="eaca3-119">查詢運算式最多只能封裝一個 `ObjectContext` 參數、一個傳回參數和十六個查詢參數。</span><span class="sxs-lookup"><span data-stu-id="eaca3-119">At most, the query expression can encapsulate an `ObjectContext` parameter, a return parameter, and 16 query parameters.</span></span> <span data-ttu-id="eaca3-120">如果需要使用十六個以上的查詢參數，您可以建立其屬性代表查詢參數的結構。</span><span class="sxs-lookup"><span data-stu-id="eaca3-120">If more than 16 query parameters are required, you can create a structure whose properties represent query parameters.</span></span> <span data-ttu-id="eaca3-121">然後，當您設定這些參數之後，就可以將此結構的屬性用於查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="eaca3-121">You can then use the properties on the structure in the query expression after you set the properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaca3-122">範例</span><span class="sxs-lookup"><span data-stu-id="eaca3-122">Example</span></span>  
 <span data-ttu-id="eaca3-123">下列範例會先編譯然後再叫用接受 <xref:System.Decimal> 輸入參數的查詢，並且傳回訂單序列，其中的總到期金額大於或等於 $200.00：</span><span class="sxs-lookup"><span data-stu-id="eaca3-123">The following example compiles and then invokes a query that accepts a <xref:System.Decimal> input parameter and returns a sequence of orders where the total due is greater than or equal to $200.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a><span data-ttu-id="eaca3-124">範例</span><span class="sxs-lookup"><span data-stu-id="eaca3-124">Example</span></span>  
 <span data-ttu-id="eaca3-125">下列範例會先編譯再叫用傳回 <xref:System.Data.Objects.ObjectQuery%601> 執行個體的查詢：</span><span class="sxs-lookup"><span data-stu-id="eaca3-125">The following example compiles and then invokes a query that returns an <xref:System.Data.Objects.ObjectQuery%601> instance:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a><span data-ttu-id="eaca3-126">範例</span><span class="sxs-lookup"><span data-stu-id="eaca3-126">Example</span></span>  
 <span data-ttu-id="eaca3-127">下列範例會先編譯再叫用一個查詢，此查詢會以 <xref:System.Decimal> 值形式傳回產品標價的平均值。</span><span class="sxs-lookup"><span data-stu-id="eaca3-127">The following example compiles and then invokes a query that returns the average of the product list prices as a <xref:System.Decimal> value:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a><span data-ttu-id="eaca3-128">範例</span><span class="sxs-lookup"><span data-stu-id="eaca3-128">Example</span></span>  
 <span data-ttu-id="eaca3-129">下列範例會編譯，然後再叫用接受查詢<xref:System.String>輸入參數，然後傳回`Contact`其電子郵件地址開頭為指定的字串：</span><span class="sxs-lookup"><span data-stu-id="eaca3-129">The following example compiles and then invokes a query that accepts a <xref:System.String> input parameter and then returns a `Contact` whose email address starts with the specified string:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a><span data-ttu-id="eaca3-130">範例</span><span class="sxs-lookup"><span data-stu-id="eaca3-130">Example</span></span>  
 <span data-ttu-id="eaca3-131">下列範例會先編譯然後再叫用接受 <xref:System.DateTime> 和 <xref:System.Decimal> 輸入參數的查詢，並且傳回訂單序列，其中的訂單日期晚於 2003 年 3 月 8 日，總應付金額則少於 $300.00：</span><span class="sxs-lookup"><span data-stu-id="eaca3-131">The following example compiles and then invokes a query that accepts <xref:System.DateTime> and <xref:System.Decimal> input parameters and returns a sequence of orders where the order date is later than March 8, 2003, and the total due is less than $300.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a><span data-ttu-id="eaca3-132">範例</span><span class="sxs-lookup"><span data-stu-id="eaca3-132">Example</span></span>  
 <span data-ttu-id="eaca3-133">下列範例會先編譯然後再叫用接受 <xref:System.DateTime> 輸入參數的查詢，並且傳回訂單序列，其中的訂單日期晚於 2004 年 3 月 8 日。</span><span class="sxs-lookup"><span data-stu-id="eaca3-133">The following example compiles and then invokes a query that accepts a <xref:System.DateTime> input parameter and returns a sequence of orders where the order date is later than March 8, 2004.</span></span> <span data-ttu-id="eaca3-134">此查詢會傳回匿名型別序列形式的訂單資訊。</span><span class="sxs-lookup"><span data-stu-id="eaca3-134">This query returns the order information as a sequence of anonymous types.</span></span> <span data-ttu-id="eaca3-135">匿名型別是由編譯器所推斷，所以您無法在 <xref:System.Data.Objects.CompiledQuery> 的 `Compile` 方法中指定型別參數，而且此型別會在查詢本身定義。</span><span class="sxs-lookup"><span data-stu-id="eaca3-135">Anonymous types are inferred by the compiler, so you cannot specify type parameters in the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method and the type is defined in the query itself.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a><span data-ttu-id="eaca3-136">範例</span><span class="sxs-lookup"><span data-stu-id="eaca3-136">Example</span></span>  
 <span data-ttu-id="eaca3-137">下列範例會先編譯然後再叫用接受使用者定義結構輸入參數的查詢，並且傳回訂單序列。</span><span class="sxs-lookup"><span data-stu-id="eaca3-137">The following example compiles and then invokes a query that accepts a user-defined structure input parameter and returns a sequence of orders.</span></span> <span data-ttu-id="eaca3-138">此結構會定義開始日期、結束日期和應付總額查詢參數，而且此查詢會傳回在 2003 年 3 月 3 日與 3 月 8 日之間出貨而且應付總額超過 $700.00 的訂單。</span><span class="sxs-lookup"><span data-stu-id="eaca3-138">The structure defines start date, end date, and total due query parameters, and the query returns orders shipped between March 3 and March 8, 2003 with a total due greater than $700.00.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 <span data-ttu-id="eaca3-139">定義查詢參數的結構：</span><span class="sxs-lookup"><span data-stu-id="eaca3-139">The structure that defines the query parameters:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a><span data-ttu-id="eaca3-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaca3-140">See Also</span></span>  
 [<span data-ttu-id="eaca3-141">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="eaca3-141">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="eaca3-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="eaca3-142">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [<span data-ttu-id="eaca3-143">Entity Framework 合併選項和已編譯的查詢</span><span class="sxs-lookup"><span data-stu-id="eaca3-143">Entity Framework Merge Options and Compiled Queries</span></span>](http://go.microsoft.com/fwlink/?LinkId=199591)
