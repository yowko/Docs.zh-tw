---
title: 將資料載入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794951"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="c83fc-102">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="c83fc-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="c83fc-103">必須先填入物件，才能使用 LINQ to DataSet 來查詢它。 <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="c83fc-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="c83fc-104">目前有許多不同的方式可以填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="c83fc-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c83fc-105">例如，您可以使用[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]來查詢資料庫，並將結果<xref:System.Data.DataSet>載入。</span><span class="sxs-lookup"><span data-stu-id="c83fc-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c83fc-106">如需詳細資訊，請參閱 [LINQ to SQL](./sql/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c83fc-106">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="c83fc-107">另一種將資料載入 <xref:System.Data.DataSet> 的常見方式是使用 <xref:System.Data.Common.DataAdapter> 類別 (Class)，從資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="c83fc-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="c83fc-108">下列範例可說明此點。</span><span class="sxs-lookup"><span data-stu-id="c83fc-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c83fc-109">範例</span><span class="sxs-lookup"><span data-stu-id="c83fc-109">Example</span></span>  
 <span data-ttu-id="c83fc-110">這則範例會使用 <xref:System.Data.Common.DataAdapter>，在 AdventureWorks 資料庫中查詢是否有 2002 年的銷售資訊，然後將結果載入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="c83fc-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c83fc-111"><xref:System.Data.DataSet>填入之後，您可以使用 LINQ to DataSet 針對它撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="c83fc-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="c83fc-112">此`FillDataSet`範例中的方法用於[LINQ to DataSet 範例](linq-to-dataset-examples.md)中的範例查詢。</span><span class="sxs-lookup"><span data-stu-id="c83fc-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="c83fc-113">如需詳細資訊，請參閱[查詢資料集](querying-datasets-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="c83fc-113">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="c83fc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c83fc-114">See also</span></span>

- [<span data-ttu-id="c83fc-115">LINQ to DataSet 概觀</span><span class="sxs-lookup"><span data-stu-id="c83fc-115">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="c83fc-116">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="c83fc-116">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="c83fc-117">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="c83fc-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
