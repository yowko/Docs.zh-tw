---
title: "查詢 DataView 中的 DataRowView 集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1912526d98dc7872470953e1bf61b72db191de5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="ada95-102">查詢 DataView 中的 DataRowView 集合</span><span class="sxs-lookup"><span data-stu-id="ada95-102">Querying the DataRowView Collection in a DataView</span></span>
<span data-ttu-id="ada95-103"><xref:System.Data.DataView> 公開可列舉之 <xref:System.Data.DataRowView> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ada95-103">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="ada95-104"><xref:System.Data.DataRowView> 代表 <xref:System.Data.DataRow> 的自訂檢視並會在控制項中顯示該 <xref:System.Data.DataRow> 的特定版本。</span><span class="sxs-lookup"><span data-stu-id="ada95-104"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="ada95-105">只有一個 <xref:System.Data.DataRow> 的版本能透過控制項顯示，例如 <xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="ada95-105">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="ada95-106">您可以透過 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRowView> 屬性，存取 <xref:System.Data.DataRowView.Row%2A> 公開的 <xref:System.Data.DataRowView>。</span><span class="sxs-lookup"><span data-stu-id="ada95-106">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="ada95-107">使用 <xref:System.Data.DataRowView> 檢視值時，<xref:System.Data.DataView.RowStateFilter%2A> 屬性會判斷要公開的是哪一個基礎 <xref:System.Data.DataRow> 的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="ada95-107">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="ada95-108">如需有關存取使用不同的資料列版本資訊<xref:System.Data.DataRow>，請參閱[資料列狀態和資料列版本](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="ada95-108">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="ada95-109">因為集合<xref:System.Data.DataRowView>物件所公開<xref:System.Data.DataView>是您可以使用可列舉的[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]對它進行查詢。</span><span class="sxs-lookup"><span data-stu-id="ada95-109">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to query over it.</span></span>  
  
 <span data-ttu-id="ada95-110">下列範例會查詢 `Product` 資料表中以紅色顯示的產品並根據該查詢建立資料表。</span><span class="sxs-lookup"><span data-stu-id="ada95-110">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="ada95-111"><xref:System.Data.DataView> 會根據資料表建立並且 <xref:System.Data.DataView.RowStateFilter%2A> 屬性會設為在刪除和修改的資料行進行篩選。</span><span class="sxs-lookup"><span data-stu-id="ada95-111">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="ada95-112">接著就會使用 <xref:System.Data.DataView> 做為 LINQ 查詢中的來源，而已經修改和刪除的 <xref:System.Data.DataRowView> 物件會繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ada95-112">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="ada95-113">下列範例會從繫結至 <xref:System.Windows.Forms.DataGridView> 控制項的檢視建立產品資料表。</span><span class="sxs-lookup"><span data-stu-id="ada95-113">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ada95-114">針對以紅色顯示的產品查詢會在 <xref:System.Data.DataView> 中進行，並且排序後的結果會繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ada95-114">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="ada95-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ada95-115">See Also</span></span>  
 [<span data-ttu-id="ada95-116">資料繫結和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ada95-116">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
