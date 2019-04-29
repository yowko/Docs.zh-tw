---
title: 建立 DataView 物件 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 95bc9beed9965bad32118dfafa4a5aa76902ca10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607822"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>建立 DataView 物件 (LINQ to DataSet)
目前有兩種方式可以在 <xref:System.Data.DataView> 內容中建立 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]。 您可以從 <xref:System.Data.DataView> 的 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中建立 <xref:System.Data.DataTable>，也可以從具型別或不具型別的 <xref:System.Data.DataTable> 中建立此物件。 在這兩種情況下，您會建立<xref:System.Data.DataView>使用其中一種<xref:System.Data.DataTableExtensions.AsDataView%2A>擴充方法<xref:System.Data.DataView>不是直接建構在[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]內容。  
  
 在您已經建立 <xref:System.Data.DataView> 之後，就可以將它繫結程序至 Windows Forms 應用程式或 ASP.NET 應用程式中的 UI 控制項，也可以變更篩選和排序設定。  
  
 <xref:System.Data.DataView> 會建構索引，以便大幅增加可使用索引之作業的效能，例如篩選和排序。 在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。 如果您建立 <xref:System.Data.DataView>，然後設定排序或篩選資訊，將會導致系統至少建立索引兩次：一次是建立 <xref:System.Data.DataView> 時，另一次是修改任何排序或篩選屬性時。  
  
 如需有關篩選與排序<xref:System.Data.DataView>，請參閱 <<c2> [ 使用 dataview 進行篩選](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)並[使用 dataview 進行排序](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)。  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>從 LINQ to DataSet 查詢中建立 DataView  
 您可以從 <xref:System.Data.DataView> 查詢的結果中建立 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 物件，而這些結果是 <xref:System.Data.DataRow> 物件的投影。 新建立的 <xref:System.Data.DataView> 會從建立此物件的查詢中繼承篩選和排序資訊。  
  
> [!NOTE]
>  在大部分清況中，用於篩選和排序的運算式不應該具有副作用 (Side Effect) 而且必須具決定性。 此外，這些運算式不應該包含取決於固定執行次數的任何邏輯，因為排序和篩選作業可能會執行任何次數。  
  
 目前不支援從傳回匿名型別的查詢或執行聯結 (Join) 作業的查詢中建立 <xref:System.Data.DataView>。  
  
 在用來建立 <xref:System.Data.DataView> 的查詢中只支援使用下列查詢運算子：  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 請注意，當<xref:System.Data.DataView>從建立[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢<xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>方法必須是最後查詢中呼叫的方法。 這會顯示在下列範例中，這會建立<xref:System.Data.DataView>的線上訂單資訊，請依 總金額排序：  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 您也可以使用以字串為基礎<xref:System.Data.DataView.RowFilter%2A>並<xref:System.Data.DataView.Sort%2A>屬性來篩選和排序<xref:System.Data.DataView>從查詢建立之後。 請注意，這樣做會清除繼承自查詢的排序和篩選資訊。 下列範例會從依據以 'S' 為開頭之姓氏篩選的 <xref:System.Data.DataView> 查詢中建立 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]。 以字串為基礎的 <xref:System.Data.DataView.Sort%2A> 屬性會設定為按照遞增順序排序姓氏，然後再按照遞減順序排序名字：  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>從 DataTable 中建立 DataView  
 除了從建立[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢中，<xref:System.Data.DataView>您可以從建立物件<xref:System.Data.DataTable>使用<xref:System.Data.DataTableExtensions.AsDataView%2A>方法。  
  
 下列範例會從 SalesOrderDetail 資料表中建立 <xref:System.Data.DataView>，然後將它設定為 <xref:System.Windows.Forms.BindingSource> 物件的資料來源。 這個物件會當做 <xref:System.Windows.Forms.DataGridView> 控制項的 Proxy。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 在您已經從 <xref:System.Data.DataView> 中建立 <xref:System.Data.DataTable> 之後，就可以針對它設定篩選和排序。 下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView> 並將 <xref:System.Data.DataView.Sort%2A> 屬性設定為按照遞增順序排序姓氏，然後再按照遞減順序排序名字：  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 不過，在您已經從查詢中建立 <xref:System.Data.DataView.RowFilter%2A> 之後設定 <xref:System.Data.DataView.Sort%2A> 或 <xref:System.Data.DataView> 屬性會發生效能降低的情況，因為 <xref:System.Data.DataView> 會建構索引來支援篩選和排序作業。 設定 <xref:System.Data.DataView.RowFilter%2A> 或 <xref:System.Data.DataView.Sort%2A> 屬性會重建資料索引，因而增加應用程式的負荷並降低效能。 如果可能的話，最好是在您首次建立 <xref:System.Data.DataView> 時指定篩選和排序資訊，並且避免之後修改這項資訊。  
  
## <a name="see-also"></a>另請參閱

- [資料繫結和 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [使用 DataView 進行篩選](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [使用 DataView 進行排序](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
