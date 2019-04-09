---
title: 以方法為基礎的查詢語法範例：轉換運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: e50707155d509b8300966cbba8ee885492e5b815
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108637"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="a03a9-102">以方法為基礎的查詢語法範例：轉換運算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="a03a9-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="a03a9-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法來立即執行查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="a03a9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="a03a9-104">`FillDataSet`這些範例中使用的方法指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="a03a9-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="a03a9-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="a03a9-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a03a9-106">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="a03a9-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="a03a9-107">如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 LINQ to DataSet 專案](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="a03a9-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="a03a9-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="a03a9-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="a03a9-109">範例</span><span class="sxs-lookup"><span data-stu-id="a03a9-109">Example</span></span>  
 <span data-ttu-id="a03a9-110">這則範例會使用 <xref:System.Linq.Enumerable.ToArray%2A> 方法，立即將序列 (Sequence) 評估為陣列。</span><span class="sxs-lookup"><span data-stu-id="a03a9-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="a03a9-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="a03a9-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="a03a9-112">範例</span><span class="sxs-lookup"><span data-stu-id="a03a9-112">Example</span></span>  
 <span data-ttu-id="a03a9-113">這則範例會使用 <xref:System.Linq.Enumerable.ToDictionary%2A> 方法，立即將序列和相關的索引鍵運算式評估為字典。</span><span class="sxs-lookup"><span data-stu-id="a03a9-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="a03a9-114">ToList</span><span class="sxs-lookup"><span data-stu-id="a03a9-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="a03a9-115">範例</span><span class="sxs-lookup"><span data-stu-id="a03a9-115">Example</span></span>  
 <span data-ttu-id="a03a9-116">這則範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 方法，立即將序列評估為 <xref:System.Collections.Generic.List%601>，其中 `T` 的型別為 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="a03a9-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="a03a9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a03a9-117">See also</span></span>

- [<span data-ttu-id="a03a9-118">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="a03a9-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="a03a9-119">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="a03a9-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="a03a9-120">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="a03a9-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a03a9-121">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a03a9-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
