---
title: 以方法為基礎的查詢語法範例：轉換運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 3e2a72a2bb0921828bdd90fe437987fddfc995b5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783700"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="05d4c-102">以方法為基礎的查詢語法範例：轉換運算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="05d4c-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="05d4c-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法來立即執行查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="05d4c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="05d4c-104">在`FillDataSet`這些範例中使用的方法，是在將[資料載入至資料集](loading-data-into-a-dataset.md)中時指定。</span><span class="sxs-lookup"><span data-stu-id="05d4c-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="05d4c-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="05d4c-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="05d4c-106">本主題中的範例會使用下列`using` / `Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="05d4c-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="05d4c-107">如需詳細資訊，請參閱[如何：在 Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)中建立 LINQ to DataSet 專案。</span><span class="sxs-lookup"><span data-stu-id="05d4c-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="05d4c-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="05d4c-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="05d4c-109">範例</span><span class="sxs-lookup"><span data-stu-id="05d4c-109">Example</span></span>  
 <span data-ttu-id="05d4c-110">這則範例會使用 <xref:System.Linq.Enumerable.ToArray%2A> 方法，立即將序列 (Sequence) 評估為陣列。</span><span class="sxs-lookup"><span data-stu-id="05d4c-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="05d4c-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="05d4c-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="05d4c-112">範例</span><span class="sxs-lookup"><span data-stu-id="05d4c-112">Example</span></span>  
 <span data-ttu-id="05d4c-113">這則範例會使用 <xref:System.Linq.Enumerable.ToDictionary%2A> 方法，立即將序列和相關的索引鍵運算式評估為字典。</span><span class="sxs-lookup"><span data-stu-id="05d4c-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="05d4c-114">ToList</span><span class="sxs-lookup"><span data-stu-id="05d4c-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="05d4c-115">範例</span><span class="sxs-lookup"><span data-stu-id="05d4c-115">Example</span></span>  
 <span data-ttu-id="05d4c-116">這則範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 方法，立即將序列評估為 <xref:System.Collections.Generic.List%601>，其中 `T` 的型別為 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="05d4c-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="05d4c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d4c-117">See also</span></span>

- [<span data-ttu-id="05d4c-118">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="05d4c-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="05d4c-119">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="05d4c-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="05d4c-120">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="05d4c-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="05d4c-121">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05d4c-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
