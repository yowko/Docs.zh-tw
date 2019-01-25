---
title: 查詢 DataView 中的 DataRowView 集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 1890ab2fcc7e1427d9c74f6c981e232802b0eb1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643737"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>查詢 DataView 中的 DataRowView 集合
<xref:System.Data.DataView> 公開可列舉之 <xref:System.Data.DataRowView> 物件的集合。 <xref:System.Data.DataRowView> 代表 <xref:System.Data.DataRow> 的自訂檢視並會在控制項中顯示該 <xref:System.Data.DataRow> 的特定版本。 只有一個 <xref:System.Data.DataRow> 的版本能透過控制項顯示，例如 <xref:System.Windows.Forms.DataGridView>。 您可以透過 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRowView> 屬性，存取 <xref:System.Data.DataRowView.Row%2A> 公開的 <xref:System.Data.DataRowView>。 使用 <xref:System.Data.DataRowView> 檢視值時，<xref:System.Data.DataView.RowStateFilter%2A> 屬性會判斷要公開的是哪一個基礎 <xref:System.Data.DataRow> 的資料列版本。 如需有關存取使用不同的資料列版本資訊<xref:System.Data.DataRow>，請參閱 <<c2> [ 資料列狀態和資料列版本](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。 因為集合<xref:System.Data.DataRowView>所公開的物件<xref:System.Data.DataView>是您可以使用可列舉，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]來對它進行反覆查詢。  
  
 下列範例會查詢 `Product` 資料表中以紅色顯示的產品並根據該查詢建立資料表。 <xref:System.Data.DataView> 會根據資料表建立並且 <xref:System.Data.DataView.RowStateFilter%2A> 屬性會設為在刪除和修改的資料行進行篩選。 接著就會使用 <xref:System.Data.DataView> 做為 LINQ 查詢中的來源，而已經修改和刪除的 <xref:System.Data.DataRowView> 物件會繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 下列範例會從繫結至 <xref:System.Windows.Forms.DataGridView> 控制項的檢視建立產品資料表。 針對以紅色顯示的產品查詢會在 <xref:System.Data.DataView> 中進行，並且排序後的結果會繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>另請參閱
- [資料繫結和 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
