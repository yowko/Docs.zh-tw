---
title: 以方法為基礎的查詢語法範例：聯結 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: ba6e33f98e063aab946db27b97106272c5adef63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783668"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="0ad6e-102">以方法為基礎的查詢語法範例：聯結 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0ad6e-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="0ad6e-103">在以彼此沒有可瀏覽關聯性之資料來源 (例如關聯式資料庫資料表) 為目標的查詢中，聯結 (Join) 是一項重要的作業。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="0ad6e-104">兩個資料來源的聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性之物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="0ad6e-105">如需詳細資訊，請參閱[標準查詢運算子C#總覽（）](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)或[標準查詢運算子總覽（Visual Basic）](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="0ad6e-106">此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Join%2A> 方法並搭配方法查詢語法來查詢 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="0ad6e-107">在`FillDataSet`這些範例中使用的方法，是在將[資料載入至資料集](loading-data-into-a-dataset.md)中時指定。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0ad6e-108">此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0ad6e-109">本主題中的範例會使用下列`using` / `Imports`語句：</span><span class="sxs-lookup"><span data-stu-id="0ad6e-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0ad6e-110">如需詳細資訊，請參閱[如何：在 Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)中建立 LINQ to DataSet 專案。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="0ad6e-111">Join</span><span class="sxs-lookup"><span data-stu-id="0ad6e-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ad6e-112">範例</span><span class="sxs-lookup"><span data-stu-id="0ad6e-112">Example</span></span>  
 <span data-ttu-id="0ad6e-113">這則範例會在 `Contact` 和 `SalesOrderHeader` 資料表上方執行聯結。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="0ad6e-114">範例</span><span class="sxs-lookup"><span data-stu-id="0ad6e-114">Example</span></span>  
 <span data-ttu-id="0ad6e-115">這則範例會在 `Contact` 和 `SalesOrderHeader` 資料表上方執行聯結，並依據連絡人識別碼分組結果。</span><span class="sxs-lookup"><span data-stu-id="0ad6e-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0ad6e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad6e-116">See also</span></span>

- [<span data-ttu-id="0ad6e-117">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="0ad6e-117">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0ad6e-118">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="0ad6e-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="0ad6e-119">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="0ad6e-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0ad6e-120">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ad6e-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0ad6e-121">聯結範例</span><span class="sxs-lookup"><span data-stu-id="0ad6e-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="0ad6e-122">資料集範例</span><span class="sxs-lookup"><span data-stu-id="0ad6e-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
