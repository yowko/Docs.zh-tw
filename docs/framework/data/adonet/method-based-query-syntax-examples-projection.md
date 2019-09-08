---
title: 以方法為基礎的查詢語法範例：投射（LINQ to DataSet）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 6617531c8a236eb034e6a063b7a1530c02d6e37b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794805"
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="c7ae5-102">以方法為基礎的查詢語法範例：投射（LINQ to DataSet）</span><span class="sxs-lookup"><span data-stu-id="c7ae5-102">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>
<span data-ttu-id="c7ae5-103">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法並搭配以方法為基礎的查詢語法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="c7ae5-104">在`FillDataSet`這些範例中使用的方法，是在將[資料載入至資料集](loading-data-into-a-dataset.md)中時指定。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="c7ae5-105">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c7ae5-106">本主題中的範例會使用下列`using` / `Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="c7ae5-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="c7ae5-107">如需詳細資訊，請參閱[如何：在 Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)中建立 LINQ to DataSet 專案。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="c7ae5-108">Select</span><span class="sxs-lookup"><span data-stu-id="c7ae5-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="c7ae5-109">範例</span><span class="sxs-lookup"><span data-stu-id="c7ae5-109">Example</span></span>  
 <span data-ttu-id="c7ae5-110">這則範例會使用 <xref:System.Linq.Enumerable.Select%2A> 方法，將 `Name`、`ProductNumber` 和 `ListPrice` 屬性規劃成匿名型別的序列 (Sequence)。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="c7ae5-111">`ListPrice` 屬性也會重新命名為結果型別中的 `Price`。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-111">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="c7ae5-112">SelectMany</span><span class="sxs-lookup"><span data-stu-id="c7ae5-112">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="c7ae5-113">範例</span><span class="sxs-lookup"><span data-stu-id="c7ae5-113">Example</span></span>  
 <span data-ttu-id="c7ae5-114">這則範例會使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來選取 `TotalDue` 少於 500.00 的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-114">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="c7ae5-115">範例</span><span class="sxs-lookup"><span data-stu-id="c7ae5-115">Example</span></span>  
 <span data-ttu-id="c7ae5-116">這則範例會使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來選取在 2002 年 10 月 1 日或之後下單的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="c7ae5-116">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="c7ae5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7ae5-117">See also</span></span>

- [<span data-ttu-id="c7ae5-118">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="c7ae5-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="c7ae5-119">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="c7ae5-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="c7ae5-120">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="c7ae5-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="c7ae5-121">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7ae5-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
