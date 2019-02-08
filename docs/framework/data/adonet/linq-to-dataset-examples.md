---
title: LINQ to DataSet 範例
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: ae43111a5b56e1edf3e1b4089902a8ca1d822d0d
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903804"
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="a05b4-102">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="a05b4-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="a05b4-103">本節提供 LINQ to DataSet 使用標準查詢運算子的程式設計範例。</span><span class="sxs-lookup"><span data-stu-id="a05b4-103">This section provides LINQ to DataSet programming examples that use the standard query operators.</span></span> <span data-ttu-id="a05b4-104"><xref:System.Data.DataSet>這些範例中使用由使用擴展`FillDataSet`方法中指定[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="a05b4-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="a05b4-105">如需詳細資訊，請參閱 <<c0> [ 標準查詢運算子概觀 (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)或是[標準查詢運算子概觀 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</c0></span><span class="sxs-lookup"><span data-stu-id="a05b4-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a05b4-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="a05b4-106">In This Section</span></span>  
 [<span data-ttu-id="a05b4-107">查詢運算式範例</span><span class="sxs-lookup"><span data-stu-id="a05b4-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="a05b4-108">包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="a05b4-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="a05b4-109">投影</span><span class="sxs-lookup"><span data-stu-id="a05b4-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="a05b4-110">限制</span><span class="sxs-lookup"><span data-stu-id="a05b4-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="a05b4-111">資料分割</span><span class="sxs-lookup"><span data-stu-id="a05b4-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="a05b4-112">排序</span><span class="sxs-lookup"><span data-stu-id="a05b4-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="a05b4-113">項目運算子</span><span class="sxs-lookup"><span data-stu-id="a05b4-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="a05b4-114">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="a05b4-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="a05b4-115">聯結運算子</span><span class="sxs-lookup"><span data-stu-id="a05b4-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="a05b4-116">以方法為基礎的查詢範例</span><span class="sxs-lookup"><span data-stu-id="a05b4-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="a05b4-117">包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="a05b4-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="a05b4-118">投影</span><span class="sxs-lookup"><span data-stu-id="a05b4-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="a05b4-119">資料分割</span><span class="sxs-lookup"><span data-stu-id="a05b4-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="a05b4-120">排序</span><span class="sxs-lookup"><span data-stu-id="a05b4-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="a05b4-121">集合運算子</span><span class="sxs-lookup"><span data-stu-id="a05b4-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="a05b4-122">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="a05b4-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="a05b4-123">項目運算子</span><span class="sxs-lookup"><span data-stu-id="a05b4-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="a05b4-124">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="a05b4-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="a05b4-125">Join</span><span class="sxs-lookup"><span data-stu-id="a05b4-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="a05b4-126">資料集專屬運算子範例</span><span class="sxs-lookup"><span data-stu-id="a05b4-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="a05b4-127">包含一些示範如何使用 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法和 <xref:System.Data.DataRowComparer> 類別 (Class) 的範例。</span><span class="sxs-lookup"><span data-stu-id="a05b4-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05b4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a05b4-128">See also</span></span>
- [<span data-ttu-id="a05b4-129">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="a05b4-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [<span data-ttu-id="a05b4-130">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="a05b4-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
