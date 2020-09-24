---
title: 將資料載入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: c870cabc875aa0152910ce916819fb1ff1c018f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166708"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="e512c-102">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="e512c-102">Loading Data Into a DataSet</span></span>

<span data-ttu-id="e512c-103"><xref:System.Data.DataSet>必須先填入物件，才能使用 LINQ to DataSet 進行查詢。</span><span class="sxs-lookup"><span data-stu-id="e512c-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="e512c-104">目前有許多不同的方式可以填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="e512c-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e512c-105">例如，您可以使用 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 來查詢資料庫，並將結果載入至 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="e512c-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e512c-106">如需詳細資訊，請參閱 [LINQ to SQL](./sql/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e512c-106">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="e512c-107">另一種將資料載入 <xref:System.Data.DataSet> 的常見方式是使用 <xref:System.Data.Common.DataAdapter> 類別 (Class)，從資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e512c-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="e512c-108">下列範例會加以說明。</span><span class="sxs-lookup"><span data-stu-id="e512c-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e512c-109">範例</span><span class="sxs-lookup"><span data-stu-id="e512c-109">Example</span></span>  

 <span data-ttu-id="e512c-110">這則範例會使用 <xref:System.Data.Common.DataAdapter>，在 AdventureWorks 資料庫中查詢是否有 2002 年的銷售資訊，然後將結果載入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="e512c-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e512c-111">填入之後 <xref:System.Data.DataSet> ，您可以使用 LINQ to DataSet 針對它撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="e512c-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="e512c-112">`FillDataSet`此範例中的方法會在[LINQ to DataSet 範例](linq-to-dataset-examples.md)中的範例查詢中使用。</span><span class="sxs-lookup"><span data-stu-id="e512c-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="e512c-113">如需詳細資訊，請參閱 [查詢資料集](querying-datasets-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="e512c-113">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="e512c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e512c-114">See also</span></span>

- [<span data-ttu-id="e512c-115">LINQ to DataSet 概觀</span><span class="sxs-lookup"><span data-stu-id="e512c-115">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="e512c-116">查詢 DataSet</span><span class="sxs-lookup"><span data-stu-id="e512c-116">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="e512c-117">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="e512c-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
