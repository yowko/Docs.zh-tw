---
title: 以方法為基礎的查詢語法範例：項目運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: e43208d6ae524a1370b936d42508e9c7a7d196e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149503"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="25df5-102">以方法為基礎的查詢語法範例：項目運算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="25df5-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="25df5-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法並搭配查詢運算式語法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。</span><span class="sxs-lookup"><span data-stu-id="25df5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="25df5-104">這些`FillDataSet`示例中使用的方法在[將資料載入到資料集中](loading-data-into-a-dataset.md)指定。</span><span class="sxs-lookup"><span data-stu-id="25df5-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="25df5-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="25df5-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="25df5-106">本主題中的示例使用以下`using`/`Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="25df5-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 <span data-ttu-id="25df5-107">有關詳細資訊，請參閱[如何：在視覺化工作室中創建 LINQ 到資料集組專案](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="25df5-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="25df5-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="25df5-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="25df5-109">範例</span><span class="sxs-lookup"><span data-stu-id="25df5-109">Example</span></span>  
 <span data-ttu-id="25df5-110">這則範例會使用 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來擷取 `PostalCode` == "M4B 1V7" 的第五筆地址。</span><span class="sxs-lookup"><span data-stu-id="25df5-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a><span data-ttu-id="25df5-111">First</span><span class="sxs-lookup"><span data-stu-id="25df5-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="25df5-112">範例</span><span class="sxs-lookup"><span data-stu-id="25df5-112">Example</span></span>  
 <span data-ttu-id="25df5-113">這則範例會使用 <xref:System.Linq.Enumerable.First%2A> 方法來傳回名字為 'Brooke' 的第一位連絡人。</span><span class="sxs-lookup"><span data-stu-id="25df5-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a><span data-ttu-id="25df5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25df5-114">See also</span></span>

- [<span data-ttu-id="25df5-115">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="25df5-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="25df5-116">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="25df5-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="25df5-117">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="25df5-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="25df5-118">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25df5-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
