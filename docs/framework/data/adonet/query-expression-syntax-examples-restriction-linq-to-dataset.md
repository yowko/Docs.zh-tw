---
title: 查詢運算式語法範例：限制 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: babe923132d8322ec81caae2a94678afea2a8095
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354219"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="8616c-102">查詢運算式語法範例：限制 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8616c-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="8616c-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Where%2A> 方法並搭配查詢運算式語法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="8616c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="8616c-104">`FillDataSet`這些範例中使用的方法會指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="8616c-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="8616c-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="8616c-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8616c-106">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="8616c-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]        
  
 <span data-ttu-id="8616c-107">如需詳細資訊，請參閱[How to： 建立 LINQ to DataSet 專案在 Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="8616c-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="8616c-108">位置</span><span class="sxs-lookup"><span data-stu-id="8616c-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="8616c-109">範例</span><span class="sxs-lookup"><span data-stu-id="8616c-109">Example</span></span>  
 <span data-ttu-id="8616c-110">這則範例會傳回所有線上訂單。</span><span class="sxs-lookup"><span data-stu-id="8616c-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]     
  
### <a name="example"></a><span data-ttu-id="8616c-111">範例</span><span class="sxs-lookup"><span data-stu-id="8616c-111">Example</span></span>  
 <span data-ttu-id="8616c-112">這則範例會傳回訂單數量大於 2 而小於 6 的訂單。</span><span class="sxs-lookup"><span data-stu-id="8616c-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]     
  
### <a name="example"></a><span data-ttu-id="8616c-113">範例</span><span class="sxs-lookup"><span data-stu-id="8616c-113">Example</span></span>  
 <span data-ttu-id="8616c-114">這則範例會傳回所有紅色的產品。</span><span class="sxs-lookup"><span data-stu-id="8616c-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]     
  
### <a name="example"></a><span data-ttu-id="8616c-115">範例</span><span class="sxs-lookup"><span data-stu-id="8616c-115">Example</span></span>  
 <span data-ttu-id="8616c-116">這則範例會使用 <xref:System.Linq.Enumerable.Where%2A> 方法來尋找在 2002 年 12 月 1 日之後下單的訂單，然後使用 <xref:System.Data.DataRow.GetChildRows%2A> 方法來取得每筆訂單的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8616c-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]       
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="8616c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8616c-117">See Also</span></span>  
 [<span data-ttu-id="8616c-118">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="8616c-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="8616c-119">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="8616c-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="8616c-120">標準查詢運算子概觀</span><span class="sxs-lookup"><span data-stu-id="8616c-120">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
