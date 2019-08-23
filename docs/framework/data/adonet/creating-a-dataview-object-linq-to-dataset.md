---
title: 建立 DataView 物件 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: afa760d890cf2857737372af5a9d3ba7c2749e6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949422"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>建立 DataView 物件 (LINQ to DataSet)
有兩種方式可以<xref:System.Data.DataView>在 LINQ to DataSet 內容中建立。 您可以<xref:System.Data.DataView>從<xref:System.Data.DataTable>上的 LINQ to DataSet 查詢建立, 或是從具類型或不具類型<xref:System.Data.DataTable>的來建立。 在這兩種情況下, <xref:System.Data.DataView>您可以使用其中一個<xref:System.Data.DataTableExtensions.AsDataView%2A>擴充方法來建立:<xref:System.Data.DataView>不會直接在 LINQ to DataSet 內容中可建構。  
  
 在您已經建立 <xref:System.Data.DataView> 之後，就可以將它繫結程序至 Windows Forms 應用程式或 ASP.NET 應用程式中的 UI 控制項，也可以變更篩選和排序設定。  
  
 <xref:System.Data.DataView> 會建構索引，以便大幅增加可使用索引之作業的效能，例如篩選和排序。 在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。 如果您建立 <xref:System.Data.DataView>，然後設定排序或篩選資訊，將會導致系統至少建立索引兩次：一次是建立 <xref:System.Data.DataView> 時，另一次是修改任何排序或篩選屬性時。  
  
 如需使用<xref:System.Data.DataView>進行篩選和排序的詳細資訊, 請參閱[使用 dataview 進行篩選](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)和[使用 dataview 進行排序](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)。  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>從 LINQ to DataSet 查詢中建立 DataView  
 您可以從 LINQ to DataSet 查詢的結果建立<xref:System.Data.DataRow> 物件,其中的結果是物件的投影。<xref:System.Data.DataView> 新建立的 <xref:System.Data.DataView> 會從建立此物件的查詢中繼承篩選和排序資訊。  
  
> [!NOTE]
> 在大部分清況中，用於篩選和排序的運算式不應該具有副作用 (Side Effect) 而且必須具決定性。 此外，這些運算式不應該包含取決於固定執行次數的任何邏輯，因為排序和篩選作業可能會執行任何次數。  
  
 目前不支援從傳回匿名型別的查詢或執行聯結 (Join) 作業的查詢中建立 <xref:System.Data.DataView>。  
  
 在用來建立 <xref:System.Data.DataView> 的查詢中只支援使用下列查詢運算子：  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 請注意, 當<xref:System.Data.DataView>從 LINQ to DataSet 查詢建立時, <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>方法必須是在查詢中呼叫的最後方法。 下列範例會顯示這種情況, 它會建立<xref:System.Data.DataView>依總到期日排序的線上訂單:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 從查詢建立<xref:System.Data.DataView.RowFilter%2A> <xref:System.Data.DataView>之後, 您也可以使用<xref:System.Data.DataView.Sort%2A>以字串為基礎的和屬性來篩選和排序。 請注意，這樣做會清除繼承自查詢的排序和篩選資訊。 下列範例會根據以<xref:System.Data.DataView> ' s ' 開頭的姓氏進行篩選的 LINQ to DataSet 查詢來建立。 以字串為基礎的 <xref:System.Data.DataView.Sort%2A> 屬性會設定為按照遞增順序排序姓氏，然後再按照遞減順序排序名字：  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>從 DataTable 中建立 DataView  
 除了從 LINQ to DataSet 查詢建立之外, 也可以使用<xref:System.Data.DataView> <xref:System.Data.DataTableExtensions.AsDataView%2A>方法, <xref:System.Data.DataTable>從建立物件。  
  
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
