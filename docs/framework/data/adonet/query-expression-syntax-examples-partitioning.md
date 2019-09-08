---
title: 查詢運算式語法範例：分割 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 6a00c5d49acc02c476895c999687aa944ba26aff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795095"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="7414a-102">查詢運算式語法範例：分割 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7414a-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>
<span data-ttu-id="7414a-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法並搭配查詢運算式語法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="7414a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="7414a-104">在`FillDataSet`這些範例中使用的方法，是在將[資料載入至資料集](loading-data-into-a-dataset.md)中時指定。</span><span class="sxs-lookup"><span data-stu-id="7414a-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7414a-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="7414a-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7414a-106">本主題中的範例會使用下列`using` / `Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="7414a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7414a-107">如需詳細資訊，請參閱[如何：在 Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)中建立 LINQ to DataSet 專案。</span><span class="sxs-lookup"><span data-stu-id="7414a-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="7414a-108">Skip</span><span class="sxs-lookup"><span data-stu-id="7414a-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="7414a-109">範例</span><span class="sxs-lookup"><span data-stu-id="7414a-109">Example</span></span>  
 <span data-ttu-id="7414a-110">這則範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得西雅圖的所有地址 (前兩筆地址除外)。</span><span class="sxs-lookup"><span data-stu-id="7414a-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="7414a-111">Take</span><span class="sxs-lookup"><span data-stu-id="7414a-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="7414a-112">範例</span><span class="sxs-lookup"><span data-stu-id="7414a-112">Example</span></span>  
 <span data-ttu-id="7414a-113">這則範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法來取得西雅圖的前三筆地址。</span><span class="sxs-lookup"><span data-stu-id="7414a-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="7414a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7414a-114">See also</span></span>

- [<span data-ttu-id="7414a-115">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="7414a-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7414a-116">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="7414a-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7414a-117">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="7414a-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7414a-118">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7414a-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
