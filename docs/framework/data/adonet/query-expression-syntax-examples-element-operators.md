---
title: 查詢運算式語法範例：項目運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: fae5a10e1adad7dcd1605115f254894cbf247f3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353595"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="f77e9-102">查詢運算式語法範例：項目運算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f77e9-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="f77e9-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法並搭配查詢運算式語法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。</span><span class="sxs-lookup"><span data-stu-id="f77e9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="f77e9-104">`FillDataSet`這些範例中使用的方法會指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="f77e9-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f77e9-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="f77e9-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f77e9-106">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="f77e9-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f77e9-107">如需詳細資訊，請參閱[How to： 建立 LINQ to DataSet 專案在 Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="f77e9-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="f77e9-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="f77e9-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="f77e9-109">範例</span><span class="sxs-lookup"><span data-stu-id="f77e9-109">Example</span></span>  
 <span data-ttu-id="f77e9-110">這則範例會使用 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來擷取 `PostalCode` == "M4B 1V7" 的第五筆地址。</span><span class="sxs-lookup"><span data-stu-id="f77e9-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="f77e9-111">First</span><span class="sxs-lookup"><span data-stu-id="f77e9-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="f77e9-112">範例</span><span class="sxs-lookup"><span data-stu-id="f77e9-112">Example</span></span>  
 <span data-ttu-id="f77e9-113">這則範例會使用 <xref:System.Linq.Enumerable.First%2A> 方法來傳回名字為 'Brooke' 的第一位連絡人。</span><span class="sxs-lookup"><span data-stu-id="f77e9-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="f77e9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f77e9-114">See Also</span></span>  
 [<span data-ttu-id="f77e9-115">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="f77e9-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="f77e9-116">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="f77e9-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="f77e9-117">標準查詢運算子概觀</span><span class="sxs-lookup"><span data-stu-id="f77e9-117">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
