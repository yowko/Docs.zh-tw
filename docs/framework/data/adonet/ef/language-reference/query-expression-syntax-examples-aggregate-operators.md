---
title: 查詢運算式語法範例：彙總運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: 5090616705c799f2905226b4892fa1fbe50bfbf3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249530"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="6eb3a-102">查詢運算式語法範例：彙總運算子</span><span class="sxs-lookup"><span data-stu-id="6eb3a-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="6eb3a-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Max%2A>、、 <xref:System.Linq.Enumerable.Count%2A>、 <xref:System.Linq.Enumerable.Min%2A>和<xref:System.Linq.Enumerable.Sum%2A>方法, 利用查詢運算式語法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) 。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="6eb3a-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6eb3a-105">本主題中的範例會使用下列`using` / `Imports`語句:</span><span class="sxs-lookup"><span data-stu-id="6eb3a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="6eb3a-106">Average</span><span class="sxs-lookup"><span data-stu-id="6eb3a-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="6eb3a-107">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-107">Example</span></span>  
 <span data-ttu-id="6eb3a-108">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 方法來尋找每種樣式之產品的平均標價。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="6eb3a-109">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-109">Example</span></span>  
 <span data-ttu-id="6eb3a-110">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 來取得每個連絡人識別碼的平均應付總額。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="6eb3a-111">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-111">Example</span></span>  
 <span data-ttu-id="6eb3a-112">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 來取得含有每位連絡人之平均應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="6eb3a-113">Count</span><span class="sxs-lookup"><span data-stu-id="6eb3a-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="6eb3a-114">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-114">Example</span></span>  
 <span data-ttu-id="6eb3a-115">下列範例會使用 <xref:System.Linq.Enumerable.Count%2A> 來傳回連絡人識別碼以及每個連絡人識別碼擁有多少訂單的清單。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="6eb3a-116">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-116">Example</span></span>  
 <span data-ttu-id="6eb3a-117">下列範例會依據色彩來分組產品，並使用 <xref:System.Linq.Enumerable.Count%2A> 來傳回每個色彩群組中的產品數目。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="6eb3a-118">max</span><span class="sxs-lookup"><span data-stu-id="6eb3a-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="6eb3a-119">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-119">Example</span></span>  
 <span data-ttu-id="6eb3a-120">下列範例會使用 <xref:System.Linq.Enumerable.Max%2A> 方法來取得每個連絡人識別碼的最大應付總額。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="6eb3a-121">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-121">Example</span></span>  
 <span data-ttu-id="6eb3a-122">下列範例會使用 <xref:System.Linq.Enumerable.Max%2A> 方法來取得含有每個連絡人識別碼之最大應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="6eb3a-123">Min</span><span class="sxs-lookup"><span data-stu-id="6eb3a-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="6eb3a-124">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-124">Example</span></span>  
 <span data-ttu-id="6eb3a-125">下列範例會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來取得每個連絡人識別碼的最小應付總額。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="6eb3a-126">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-126">Example</span></span>  
 <span data-ttu-id="6eb3a-127">下列範例會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來取得含有每位連絡人之最小應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="6eb3a-128">Sum</span><span class="sxs-lookup"><span data-stu-id="6eb3a-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="6eb3a-129">範例</span><span class="sxs-lookup"><span data-stu-id="6eb3a-129">Example</span></span>  
 <span data-ttu-id="6eb3a-130">下列範例會使用 <xref:System.Linq.Enumerable.Sum%2A> 方法來取得每個連絡人識別碼的應付總額。</span><span class="sxs-lookup"><span data-stu-id="6eb3a-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="6eb3a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eb3a-131">See also</span></span>

- [<span data-ttu-id="6eb3a-132">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="6eb3a-132">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
