---
title: 資料集專屬運算子範例 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 92daf1dff3d473016d92b359ea6f75295a9dbd37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739020"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="e4c51-102">資料集專屬運算子範例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e4c51-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="e4c51-103">此主題中的範例將示範如何使用 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法和 <xref:System.Data.DataRowComparer> 類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="e4c51-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="e4c51-104">`FillDataSet`這些範例中使用的方法指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="e4c51-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="e4c51-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="e4c51-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e4c51-106">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="e4c51-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="e4c51-107">如需詳細資訊，請參閱[＜How to：在 Visual Studio 中建立 LINQ to DataSet 專案](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="e4c51-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="e4c51-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="e4c51-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4c51-109">範例</span><span class="sxs-lookup"><span data-stu-id="e4c51-109">Example</span></span>  
 <span data-ttu-id="e4c51-110">這個範例會使用 <xref:System.Data.DataTable> 方法來載入含有查詢結果的 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>。</span><span class="sxs-lookup"><span data-stu-id="e4c51-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="e4c51-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="e4c51-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4c51-112">範例</span><span class="sxs-lookup"><span data-stu-id="e4c51-112">Example</span></span>  
 <span data-ttu-id="e4c51-113">這則範例會使用 <xref:System.Data.DataRowComparer> 來比較兩個不同的資料列。</span><span class="sxs-lookup"><span data-stu-id="e4c51-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="e4c51-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4c51-114">See also</span></span>
- [<span data-ttu-id="e4c51-115">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="e4c51-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="e4c51-116">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="e4c51-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
