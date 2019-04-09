---
title: 查詢運算式語法範例：規劃 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 3bd7934cef03df391c1871b8499f911a023d7d3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097586"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="50068-102">查詢運算式語法範例：規劃 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="50068-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="50068-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法並搭配查詢運算式語法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="50068-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="50068-104">`FillDataSet`這些範例中使用的方法指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="50068-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="50068-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="50068-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="50068-106">本主題中的範例使用下列`using` / `Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="50068-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="50068-107">如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 LINQ to DataSet 專案](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="50068-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="50068-108">選用版</span><span class="sxs-lookup"><span data-stu-id="50068-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="50068-109">範例</span><span class="sxs-lookup"><span data-stu-id="50068-109">Example</span></span>  
 <span data-ttu-id="50068-110">這則範例會使用 <xref:System.Linq.Enumerable.Select%2A> 方法來傳回 `Product` 資料表中的所有資料列，並顯示產品名稱。</span><span class="sxs-lookup"><span data-stu-id="50068-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="50068-111">範例</span><span class="sxs-lookup"><span data-stu-id="50068-111">Example</span></span>  
 <span data-ttu-id="50068-112">這則範例會使用 <xref:System.Linq.Enumerable.Select%2A> 來單獨傳回產品名稱的序列 (Sequence)。</span><span class="sxs-lookup"><span data-stu-id="50068-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="50068-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="50068-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="50068-114">範例</span><span class="sxs-lookup"><span data-stu-id="50068-114">Example</span></span>  
 <span data-ttu-id="50068-115">這則範例會使用 `From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> 方法的對等項目) 來選取 `TotalDue` 少於 500.00 的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="50068-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="50068-116">範例</span><span class="sxs-lookup"><span data-stu-id="50068-116">Example</span></span>  
 <span data-ttu-id="50068-117">這則範例會使用 `From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> 方法的對等項目) 來選取在 2002 年 10 月 1 日或之後下單的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="50068-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="50068-118">範例</span><span class="sxs-lookup"><span data-stu-id="50068-118">Example</span></span>  
 <span data-ttu-id="50068-119">這則範例會使用 `From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> 方法的對等項目) 來選取訂單總金額超過 10000.00 的所有訂單，並使用 `From` 指派來避免要求總金額兩次。</span><span class="sxs-lookup"><span data-stu-id="50068-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="50068-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50068-120">See also</span></span>

- [<span data-ttu-id="50068-121">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="50068-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="50068-122">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="50068-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="50068-123">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="50068-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="50068-124">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50068-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
