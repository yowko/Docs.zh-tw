---
title: 在序列中群組項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: 5d812ae9b5fd0a796588d3366b8546ef84c982c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089910"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="9ce56-102">在序列中群組項目</span><span class="sxs-lookup"><span data-stu-id="9ce56-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="9ce56-103"><xref:System.Linq.Enumerable.GroupBy%2A> 運算子會分組序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="9ce56-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="9ce56-104">下列範例使用 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9ce56-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ce56-105"><xref:System.Linq.Enumerable.GroupBy%2A> 查詢中的 Null 資料行值有時會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="9ce56-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="9ce56-106">如需詳細資訊，請參閱的 < GroupBy InvalidOperationException > 一節[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce56-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce56-107">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-107">Example</span></span>  
 <span data-ttu-id="9ce56-108">下列範例會根據 `Products` 來分割 `CategoryID`。</span><span class="sxs-lookup"><span data-stu-id="9ce56-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-109">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-109">Example</span></span>  
 <span data-ttu-id="9ce56-110">下列範例使用 <xref:System.Linq.Enumerable.Max%2A> 來找出每個 `CategoryID` 的最高單價。</span><span class="sxs-lookup"><span data-stu-id="9ce56-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-111">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-111">Example</span></span>  
 <span data-ttu-id="9ce56-112">下列範例使用 Average 來找出每個 `UnitPrice` 的平均 `CategoryID`。</span><span class="sxs-lookup"><span data-stu-id="9ce56-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-113">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-113">Example</span></span>  
 <span data-ttu-id="9ce56-114">下列範例使用 <xref:System.Linq.Queryable.Sum%2A> 來找出每個 `UnitPrice` 的總 `CategoryID`。</span><span class="sxs-lookup"><span data-stu-id="9ce56-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-115">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-115">Example</span></span>  
 <span data-ttu-id="9ce56-116">下列範例使用 <xref:System.Linq.Queryable.Count%2A> 來尋找每個 `Products` 中停產的 `CategoryID` 數。</span><span class="sxs-lookup"><span data-stu-id="9ce56-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-117">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-117">Example</span></span>  
 <span data-ttu-id="9ce56-118">下列範例使用後續 `where` 子句，來尋找所有至少有 10 個產品的類別。</span><span class="sxs-lookup"><span data-stu-id="9ce56-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-119">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-119">Example</span></span>  
 <span data-ttu-id="9ce56-120">下列範例會根據 `CategoryID` 和 `SupplierID` 來分組產品。</span><span class="sxs-lookup"><span data-stu-id="9ce56-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-121">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-121">Example</span></span>  
 <span data-ttu-id="9ce56-122">下列範例會傳回兩個產品序列。</span><span class="sxs-lookup"><span data-stu-id="9ce56-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="9ce56-123">第一個序列包含單價低於或等於 10 的產品。</span><span class="sxs-lookup"><span data-stu-id="9ce56-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="9ce56-124">第二個序列則包含單價高於 10 的產品。</span><span class="sxs-lookup"><span data-stu-id="9ce56-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="9ce56-125">範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-125">Example</span></span>  
 <span data-ttu-id="9ce56-126"><xref:System.Linq.Queryable.GroupBy%2A> 運算子只能採用單一索引鍵引數。</span><span class="sxs-lookup"><span data-stu-id="9ce56-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="9ce56-127">如果需要根據多個索引鍵進行分組，則必須建立匿名型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9ce56-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="9ce56-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ce56-128">See also</span></span>

- [<span data-ttu-id="9ce56-129">查詢範例</span><span class="sxs-lookup"><span data-stu-id="9ce56-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="9ce56-130">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="9ce56-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
