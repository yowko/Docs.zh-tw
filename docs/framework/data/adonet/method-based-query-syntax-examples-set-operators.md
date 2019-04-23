---
title: 以方法為基礎的查詢語法範例：設定運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 48aa6044f39be93f144b6c4af5137b131dda0b30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085814"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="9696e-102">以方法為基礎的查詢語法範例：設定運算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9696e-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="9696e-103">本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.Distinct%2A>， <xref:System.Linq.Enumerable.Except%2A>， <xref:System.Linq.Enumerable.Intersect%2A>，以及<xref:System.Linq.Enumerable.Union%2A>運算子，以執行一組資料列的值為基礎的比較作業。[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)請參閱 <<c12> [ 比較 Datarow](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)如需有關<xref:System.Data.DataRowComparer>。</span><span class="sxs-lookup"><span data-stu-id="9696e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) See [Comparing DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="9696e-104">`FillDataSet`這些範例中使用的方法指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="9696e-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9696e-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="9696e-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9696e-106">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="9696e-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="9696e-107">如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 LINQ to DataSet 專案](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="9696e-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="9696e-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="9696e-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="9696e-109">範例</span><span class="sxs-lookup"><span data-stu-id="9696e-109">Example</span></span>  
 <span data-ttu-id="9696e-110">這則範例會使用 <xref:System.Linq.Enumerable.Distinct%2A> 方法來移除序列 (Sequence) 中的重複項目。</span><span class="sxs-lookup"><span data-stu-id="9696e-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="9696e-111">例外</span><span class="sxs-lookup"><span data-stu-id="9696e-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="9696e-112">範例</span><span class="sxs-lookup"><span data-stu-id="9696e-112">Example</span></span>  
 <span data-ttu-id="9696e-113">這則範例會使用 <xref:System.Linq.Enumerable.Except%2A> 方法來傳回在第一份資料表中出現但沒有在第二份資料表中出現的連絡人。</span><span class="sxs-lookup"><span data-stu-id="9696e-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="9696e-114">交集</span><span class="sxs-lookup"><span data-stu-id="9696e-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="9696e-115">範例</span><span class="sxs-lookup"><span data-stu-id="9696e-115">Example</span></span>  
 <span data-ttu-id="9696e-116">這則範例會使用 <xref:System.Linq.Enumerable.Intersect%2A> 方法來傳回在這兩份資料表中都出現的連絡人。</span><span class="sxs-lookup"><span data-stu-id="9696e-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="9696e-117">聯集</span><span class="sxs-lookup"><span data-stu-id="9696e-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="9696e-118">範例</span><span class="sxs-lookup"><span data-stu-id="9696e-118">Example</span></span>  
 <span data-ttu-id="9696e-119">這則範例會使用 <xref:System.Linq.Enumerable.Union%2A> 方法來傳回在其中一份資料表中出現的唯一連絡人。</span><span class="sxs-lookup"><span data-stu-id="9696e-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="9696e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9696e-120">See also</span></span>

- [<span data-ttu-id="9696e-121">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="9696e-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="9696e-122">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="9696e-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="9696e-123">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="9696e-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9696e-124">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9696e-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
