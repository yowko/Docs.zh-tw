---
title: 以方法為基礎的查詢語法範例：彙總運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 1f4090cbffc4177c4b9edd08381e8dd294ae0c41
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740896"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="3cb98-102">以方法為基礎的查詢語法範例：彙總運算子</span><span class="sxs-lookup"><span data-stu-id="3cb98-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="3cb98-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Aggregate%2A>， <xref:System.Linq.Enumerable.Average%2A>， <xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.LongCount%2A>， <xref:System.Linq.Enumerable.Max%2A>， <xref:System.Linq.Enumerable.Min%2A>，以及<xref:System.Linq.Enumerable.Sum%2A>方法來查詢[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)使用以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="3cb98-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="3cb98-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="3cb98-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3cb98-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="3cb98-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="3cb98-106">Average</span><span class="sxs-lookup"><span data-stu-id="3cb98-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb98-107">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-107">Example</span></span>  
 <span data-ttu-id="3cb98-108">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 方法來尋找產品的平均標價。</span><span class="sxs-lookup"><span data-stu-id="3cb98-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-109">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-109">Example</span></span>  
 <span data-ttu-id="3cb98-110">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 方法來尋找每種樣式之產品的平均標價。</span><span class="sxs-lookup"><span data-stu-id="3cb98-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-111">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-111">Example</span></span>  
 <span data-ttu-id="3cb98-112">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 方法來尋找平均總金額。</span><span class="sxs-lookup"><span data-stu-id="3cb98-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-113">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-113">Example</span></span>  
 <span data-ttu-id="3cb98-114">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 方法來取得每個連絡人識別碼的平均總金額。</span><span class="sxs-lookup"><span data-stu-id="3cb98-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-115">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-115">Example</span></span>  
 <span data-ttu-id="3cb98-116">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 方法來取得含有每位連絡人之平均總金額的訂單。</span><span class="sxs-lookup"><span data-stu-id="3cb98-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="3cb98-117">計數</span><span class="sxs-lookup"><span data-stu-id="3cb98-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb98-118">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-118">Example</span></span>  
 <span data-ttu-id="3cb98-119">下列範例會使用 <xref:System.Linq.Enumerable.Count%2A> 方法來傳回 Product 資料表中的產品數目。</span><span class="sxs-lookup"><span data-stu-id="3cb98-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-120">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-120">Example</span></span>  
 <span data-ttu-id="3cb98-121">下列範例會使用 <xref:System.Linq.Enumerable.Count%2A> 方法來傳回連絡人識別碼以及每個連絡人識別碼擁有多少訂單的清單。</span><span class="sxs-lookup"><span data-stu-id="3cb98-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-122">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-122">Example</span></span>  
 <span data-ttu-id="3cb98-123">下列範例會依據色彩來分組產品並使用 <xref:System.Linq.Enumerable.Count%2A> 方法來傳回每個色彩群組中的產品數目。</span><span class="sxs-lookup"><span data-stu-id="3cb98-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="3cb98-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="3cb98-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb98-125">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-125">Example</span></span>  
 <span data-ttu-id="3cb98-126">下列範例會取得連絡人計數當做長整數 (Long Integer)。</span><span class="sxs-lookup"><span data-stu-id="3cb98-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="3cb98-127">最大值</span><span class="sxs-lookup"><span data-stu-id="3cb98-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb98-128">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-128">Example</span></span>  
 <span data-ttu-id="3cb98-129">下列範例會使用 <xref:System.Linq.Enumerable.Max%2A> 方法來取得最大總金額。</span><span class="sxs-lookup"><span data-stu-id="3cb98-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-130">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-130">Example</span></span>  
 <span data-ttu-id="3cb98-131">下列範例會使用 <xref:System.Linq.Enumerable.Max%2A> 方法來取得每個連絡人識別碼的最大應付總額。</span><span class="sxs-lookup"><span data-stu-id="3cb98-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-132">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-132">Example</span></span>  
 <span data-ttu-id="3cb98-133">下列範例會使用 <xref:System.Linq.Enumerable.Max%2A> 方法來取得含有每個連絡人識別碼之最大應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="3cb98-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="3cb98-134">最小值</span><span class="sxs-lookup"><span data-stu-id="3cb98-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb98-135">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-135">Example</span></span>  
 <span data-ttu-id="3cb98-136">下列範例會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來取得最小總金額。</span><span class="sxs-lookup"><span data-stu-id="3cb98-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-137">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-137">Example</span></span>  
 <span data-ttu-id="3cb98-138">下列範例會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來取得每個連絡人識別碼的最小應付總額。</span><span class="sxs-lookup"><span data-stu-id="3cb98-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-139">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-139">Example</span></span>  
 <span data-ttu-id="3cb98-140">下列範例會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來取得含有每位連絡人之最小應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="3cb98-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="3cb98-141">Sum</span><span class="sxs-lookup"><span data-stu-id="3cb98-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cb98-142">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-142">Example</span></span>  
 <span data-ttu-id="3cb98-143">下列範例會使用 <xref:System.Linq.Enumerable.Sum%2A> 方法來取得 SalesOrderDetail 資料表中訂單數量的總數。</span><span class="sxs-lookup"><span data-stu-id="3cb98-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="3cb98-144">範例</span><span class="sxs-lookup"><span data-stu-id="3cb98-144">Example</span></span>  
 <span data-ttu-id="3cb98-145">下列範例會使用 <xref:System.Linq.Enumerable.Sum%2A> 方法來取得每個連絡人識別碼的應付總額。</span><span class="sxs-lookup"><span data-stu-id="3cb98-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="3cb98-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cb98-146">See Also</span></span>  
 [<span data-ttu-id="3cb98-147">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="3cb98-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
