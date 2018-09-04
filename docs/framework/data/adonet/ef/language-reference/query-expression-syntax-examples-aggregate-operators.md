---
title: 查詢運算式語法範例：彙總運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: 4717f7fe438f67a0d40c64724700f7ea78c4c887
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522722"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="79fc1-102">查詢運算式語法範例：彙總運算子</span><span class="sxs-lookup"><span data-stu-id="79fc1-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="79fc1-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Average%2A>， <xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Max%2A>， <xref:System.Linq.Enumerable.Min%2A>，並<xref:System.Linq.Enumerable.Sum%2A>方法來查詢[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)透過查詢運算式語法。</span><span class="sxs-lookup"><span data-stu-id="79fc1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="79fc1-104">這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。</span><span class="sxs-lookup"><span data-stu-id="79fc1-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="79fc1-105">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="79fc1-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="79fc1-106">平均</span><span class="sxs-lookup"><span data-stu-id="79fc1-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="79fc1-107">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-107">Example</span></span>  
 <span data-ttu-id="79fc1-108">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 方法來尋找每種樣式之產品的平均標價。</span><span class="sxs-lookup"><span data-stu-id="79fc1-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="79fc1-109">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-109">Example</span></span>  
 <span data-ttu-id="79fc1-110">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 來取得每個連絡人識別碼的平均應付總額。</span><span class="sxs-lookup"><span data-stu-id="79fc1-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="79fc1-111">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-111">Example</span></span>  
 <span data-ttu-id="79fc1-112">下列範例會使用 <xref:System.Linq.Enumerable.Average%2A> 來取得含有每位連絡人之平均應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="79fc1-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="79fc1-113">計數</span><span class="sxs-lookup"><span data-stu-id="79fc1-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="79fc1-114">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-114">Example</span></span>  
 <span data-ttu-id="79fc1-115">下列範例會使用 <xref:System.Linq.Enumerable.Count%2A> 來傳回連絡人識別碼以及每個連絡人識別碼擁有多少訂單的清單。</span><span class="sxs-lookup"><span data-stu-id="79fc1-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="79fc1-116">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-116">Example</span></span>  
 <span data-ttu-id="79fc1-117">下列範例會依據色彩來分組產品，並使用 <xref:System.Linq.Enumerable.Count%2A> 來傳回每個色彩群組中的產品數目。</span><span class="sxs-lookup"><span data-stu-id="79fc1-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="79fc1-118">最大值</span><span class="sxs-lookup"><span data-stu-id="79fc1-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="79fc1-119">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-119">Example</span></span>  
 <span data-ttu-id="79fc1-120">下列範例會使用 <xref:System.Linq.Enumerable.Max%2A> 方法來取得每個連絡人識別碼的最大應付總額。</span><span class="sxs-lookup"><span data-stu-id="79fc1-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="79fc1-121">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-121">Example</span></span>  
 <span data-ttu-id="79fc1-122">下列範例會使用 <xref:System.Linq.Enumerable.Max%2A> 方法來取得含有每個連絡人識別碼之最大應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="79fc1-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="79fc1-123">最小值</span><span class="sxs-lookup"><span data-stu-id="79fc1-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="79fc1-124">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-124">Example</span></span>  
 <span data-ttu-id="79fc1-125">下列範例會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來取得每個連絡人識別碼的最小應付總額。</span><span class="sxs-lookup"><span data-stu-id="79fc1-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="79fc1-126">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-126">Example</span></span>  
 <span data-ttu-id="79fc1-127">下列範例會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來取得含有每位連絡人之最小應付總額的訂單。</span><span class="sxs-lookup"><span data-stu-id="79fc1-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="79fc1-128">Sum</span><span class="sxs-lookup"><span data-stu-id="79fc1-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="79fc1-129">範例</span><span class="sxs-lookup"><span data-stu-id="79fc1-129">Example</span></span>  
 <span data-ttu-id="79fc1-130">下列範例會使用 <xref:System.Linq.Enumerable.Sum%2A> 方法來取得每個連絡人識別碼的應付總額。</span><span class="sxs-lookup"><span data-stu-id="79fc1-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="79fc1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79fc1-131">See Also</span></span>  
 [<span data-ttu-id="79fc1-132">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="79fc1-132">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
