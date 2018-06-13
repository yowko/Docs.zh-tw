---
title: 將資料載入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: c076b19db0acb27b57a31c20d45f619a802ebc88
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767111"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="acda2-102">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="acda2-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="acda2-103"><xref:System.Data.DataSet> 物件必須先填入 (Populate) 資料，然後您才能使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來查詢它。</span><span class="sxs-lookup"><span data-stu-id="acda2-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="acda2-104">目前有許多不同的方式可以填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="acda2-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="acda2-105">例如，您可以使用[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]查詢資料庫，並將結果載入至<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="acda2-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="acda2-106">如需詳細資訊，請參閱 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="acda2-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="acda2-107">另一種將資料載入 <xref:System.Data.DataSet> 的常見方式是使用 <xref:System.Data.Common.DataAdapter> 類別 (Class)，從資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="acda2-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="acda2-108">下列範例將說明這種方式。</span><span class="sxs-lookup"><span data-stu-id="acda2-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acda2-109">範例</span><span class="sxs-lookup"><span data-stu-id="acda2-109">Example</span></span>  
 <span data-ttu-id="acda2-110">這則範例會使用 <xref:System.Data.Common.DataAdapter>，在 AdventureWorks 資料庫中查詢是否有 2002 年的銷售資訊，然後將結果載入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="acda2-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="acda2-111">當 <xref:System.Data.DataSet> 已經填入資料之後，您就可以使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來針對它撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="acda2-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="acda2-112">`FillDataSet`在此範例中的方法在此範例會查詢中用[LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="acda2-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="acda2-113">如需詳細資訊，請參閱[查詢資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="acda2-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="acda2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acda2-114">See Also</span></span>  
 [<span data-ttu-id="acda2-115">LINQ to DataSet 概觀</span><span class="sxs-lookup"><span data-stu-id="acda2-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="acda2-116">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="acda2-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="acda2-117">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="acda2-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
