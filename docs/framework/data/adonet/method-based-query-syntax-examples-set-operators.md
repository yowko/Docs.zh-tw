---
title: 以方法為基礎的查詢語法範例：集合運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: f91d009e66f1f0da25e508994040d7e9f80fc681
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147862"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="7f499-102">以方法為基礎的查詢語法範例：集合運算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7f499-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="7f499-103">本主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Distinct%2A> 、 <xref:System.Linq.Enumerable.Except%2A> 、 <xref:System.Linq.Enumerable.Intersect%2A> 和運算子， <xref:System.Linq.Enumerable.Union%2A> 在一組資料列上執行以值為基礎的比較作業。[將資料載入資料集](loading-data-into-a-dataset.md) 的詳細資訊，請參閱 [比較 datarow](comparing-datarows-linq-to-dataset.md) <xref:System.Data.DataRowComparer> 。</span><span class="sxs-lookup"><span data-stu-id="7f499-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="7f499-104">`FillDataSet`這些範例中使用的方法是在將[資料載入資料集](loading-data-into-a-dataset.md)時指定。</span><span class="sxs-lookup"><span data-stu-id="7f499-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7f499-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="7f499-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7f499-106">本主題中的範例使用下列 `using` / `Imports` 語句：</span><span class="sxs-lookup"><span data-stu-id="7f499-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7f499-107">如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 LINQ to DataSet 專案](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="7f499-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="7f499-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="7f499-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="7f499-109">範例</span><span class="sxs-lookup"><span data-stu-id="7f499-109">Example</span></span>  

 <span data-ttu-id="7f499-110">這則範例會使用 <xref:System.Linq.Enumerable.Distinct%2A> 方法來移除序列 (Sequence) 中的重複項目。</span><span class="sxs-lookup"><span data-stu-id="7f499-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="7f499-111">Except</span><span class="sxs-lookup"><span data-stu-id="7f499-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="7f499-112">範例</span><span class="sxs-lookup"><span data-stu-id="7f499-112">Example</span></span>  

 <span data-ttu-id="7f499-113">這則範例會使用 <xref:System.Linq.Enumerable.Except%2A> 方法來傳回在第一份資料表中出現但沒有在第二份資料表中出現的連絡人。</span><span class="sxs-lookup"><span data-stu-id="7f499-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="7f499-114">Intersect</span><span class="sxs-lookup"><span data-stu-id="7f499-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="7f499-115">範例</span><span class="sxs-lookup"><span data-stu-id="7f499-115">Example</span></span>  

 <span data-ttu-id="7f499-116">這則範例會使用 <xref:System.Linq.Enumerable.Intersect%2A> 方法來傳回在這兩份資料表中都出現的連絡人。</span><span class="sxs-lookup"><span data-stu-id="7f499-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="7f499-117">Union</span><span class="sxs-lookup"><span data-stu-id="7f499-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="7f499-118">範例</span><span class="sxs-lookup"><span data-stu-id="7f499-118">Example</span></span>  

 <span data-ttu-id="7f499-119">這則範例會使用 <xref:System.Linq.Enumerable.Union%2A> 方法來傳回在其中一份資料表中出現的唯一連絡人。</span><span class="sxs-lookup"><span data-stu-id="7f499-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="7f499-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f499-120">See also</span></span>

- [<span data-ttu-id="7f499-121">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="7f499-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7f499-122">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="7f499-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7f499-123">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f499-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7f499-124">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f499-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
