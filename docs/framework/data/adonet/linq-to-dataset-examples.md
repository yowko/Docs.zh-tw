---
title: LINQ to DataSet 範例
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: f0b836e4f19011dc3d75f0681f7205cec6cb9110
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="eaa33-102">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="eaa33-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="eaa33-103">本節提供[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]程式設計使用標準查詢運算子的範例。</span><span class="sxs-lookup"><span data-stu-id="eaa33-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples that use the standard query operators.</span></span> <span data-ttu-id="eaa33-104"><xref:System.Data.DataSet>這些範例中使用填入的方式是使用`FillDataSet`方法中所指定[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="eaa33-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="eaa33-105">如需詳細資訊，請參閱[標準查詢運算子概觀](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。</span><span class="sxs-lookup"><span data-stu-id="eaa33-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eaa33-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="eaa33-106">In This Section</span></span>  
 [<span data-ttu-id="eaa33-107">查詢運算式範例</span><span class="sxs-lookup"><span data-stu-id="eaa33-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="eaa33-108">包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="eaa33-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="eaa33-109">投影</span><span class="sxs-lookup"><span data-stu-id="eaa33-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="eaa33-110">限制</span><span class="sxs-lookup"><span data-stu-id="eaa33-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="eaa33-111">資料分割</span><span class="sxs-lookup"><span data-stu-id="eaa33-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="eaa33-112">排序</span><span class="sxs-lookup"><span data-stu-id="eaa33-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="eaa33-113">項目運算子</span><span class="sxs-lookup"><span data-stu-id="eaa33-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="eaa33-114">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="eaa33-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="eaa33-115">聯結運算子</span><span class="sxs-lookup"><span data-stu-id="eaa33-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="eaa33-116">以方法為基礎的查詢範例</span><span class="sxs-lookup"><span data-stu-id="eaa33-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="eaa33-117">包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="eaa33-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="eaa33-118">投影</span><span class="sxs-lookup"><span data-stu-id="eaa33-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="eaa33-119">資料分割</span><span class="sxs-lookup"><span data-stu-id="eaa33-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="eaa33-120">排序</span><span class="sxs-lookup"><span data-stu-id="eaa33-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="eaa33-121">集合運算子</span><span class="sxs-lookup"><span data-stu-id="eaa33-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="eaa33-122">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="eaa33-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="eaa33-123">項目運算子</span><span class="sxs-lookup"><span data-stu-id="eaa33-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="eaa33-124">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="eaa33-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="eaa33-125">Join</span><span class="sxs-lookup"><span data-stu-id="eaa33-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="eaa33-126">資料集專屬運算子範例</span><span class="sxs-lookup"><span data-stu-id="eaa33-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="eaa33-127">包含一些示範如何使用 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法和 <xref:System.Data.DataRowComparer> 類別 (Class) 的範例。</span><span class="sxs-lookup"><span data-stu-id="eaa33-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa33-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaa33-128">See Also</span></span>  
 [<span data-ttu-id="eaa33-129">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="eaa33-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [<span data-ttu-id="eaa33-130">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="eaa33-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
