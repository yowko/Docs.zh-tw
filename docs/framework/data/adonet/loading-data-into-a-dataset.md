---
title: 將資料載入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 26b77269b21e1b365f81746ba2df66d7df91677e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504325"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="8c120-102">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="8c120-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="8c120-103">A<xref:System.Data.DataSet>您可以使用 LINQ to DataSet 查詢透過它之前，必須先填入物件。</span><span class="sxs-lookup"><span data-stu-id="8c120-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="8c120-104">目前有許多不同的方式可以填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="8c120-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8c120-105">例如，您可以使用[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]來查詢資料庫，並將結果載入<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="8c120-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8c120-106">如需詳細資訊，請參閱 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8c120-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="8c120-107">另一種將資料載入 <xref:System.Data.DataSet> 的常見方式是使用 <xref:System.Data.Common.DataAdapter> 類別 (Class)，從資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="8c120-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="8c120-108">下列範例可說明此點。</span><span class="sxs-lookup"><span data-stu-id="8c120-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c120-109">範例</span><span class="sxs-lookup"><span data-stu-id="8c120-109">Example</span></span>  
 <span data-ttu-id="8c120-110">這則範例會使用 <xref:System.Data.Common.DataAdapter>，在 AdventureWorks 資料庫中查詢是否有 2002 年的銷售資訊，然後將結果載入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="8c120-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8c120-111">之後<xref:System.Data.DataSet>已填入，您可以針對它撰寫查詢使用 LINQ to DataSet。</span><span class="sxs-lookup"><span data-stu-id="8c120-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="8c120-112">`FillDataSet`方法，在此範例中用於在此範例會查詢[LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="8c120-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="8c120-113">如需詳細資訊，請參閱 <<c0> [ 查詢的資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="8c120-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="8c120-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c120-114">See also</span></span>

- [<span data-ttu-id="8c120-115">LINQ to DataSet 概觀</span><span class="sxs-lookup"><span data-stu-id="8c120-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="8c120-116">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="8c120-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="8c120-117">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="8c120-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
