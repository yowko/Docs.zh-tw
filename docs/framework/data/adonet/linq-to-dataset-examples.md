---
title: "LINQ to DataSet 範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 808c12ee0f9a52c09fa32a0bdf2cc0177bf8be4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="13db8-102">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="13db8-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="13db8-103">本節提供[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]程式設計使用標準查詢運算子的範例。</span><span class="sxs-lookup"><span data-stu-id="13db8-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples that use the standard query operators.</span></span> <span data-ttu-id="13db8-104"><xref:System.Data.DataSet>這些範例中使用填入的方式是使用`FillDataSet`方法中所指定[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="13db8-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="13db8-105">如需詳細資訊，請參閱[標準查詢運算子概觀](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。</span><span class="sxs-lookup"><span data-stu-id="13db8-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13db8-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="13db8-106">In This Section</span></span>  
 [<span data-ttu-id="13db8-107">查詢運算式範例</span><span class="sxs-lookup"><span data-stu-id="13db8-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="13db8-108">包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="13db8-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="13db8-109">投影</span><span class="sxs-lookup"><span data-stu-id="13db8-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="13db8-110">限制</span><span class="sxs-lookup"><span data-stu-id="13db8-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="13db8-111">資料分割</span><span class="sxs-lookup"><span data-stu-id="13db8-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="13db8-112">排序</span><span class="sxs-lookup"><span data-stu-id="13db8-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="13db8-113">項目運算子</span><span class="sxs-lookup"><span data-stu-id="13db8-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="13db8-114">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="13db8-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="13db8-115">聯結運算子</span><span class="sxs-lookup"><span data-stu-id="13db8-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="13db8-116">以方法為基礎的查詢範例</span><span class="sxs-lookup"><span data-stu-id="13db8-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="13db8-117">包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="13db8-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="13db8-118">投影</span><span class="sxs-lookup"><span data-stu-id="13db8-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="13db8-119">資料分割</span><span class="sxs-lookup"><span data-stu-id="13db8-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="13db8-120">排序</span><span class="sxs-lookup"><span data-stu-id="13db8-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="13db8-121">設定運算子</span><span class="sxs-lookup"><span data-stu-id="13db8-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="13db8-122">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="13db8-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="13db8-123">項目運算子</span><span class="sxs-lookup"><span data-stu-id="13db8-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="13db8-124">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="13db8-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="13db8-125">Join</span><span class="sxs-lookup"><span data-stu-id="13db8-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="13db8-126">資料集專屬運算子範例</span><span class="sxs-lookup"><span data-stu-id="13db8-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="13db8-127">包含一些示範如何使用 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法和 <xref:System.Data.DataRowComparer> 類別 (Class) 的範例。</span><span class="sxs-lookup"><span data-stu-id="13db8-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13db8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13db8-128">See Also</span></span>  
 [<span data-ttu-id="13db8-129">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="13db8-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [<span data-ttu-id="13db8-130">載入資料至資料集</span><span class="sxs-lookup"><span data-stu-id="13db8-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
