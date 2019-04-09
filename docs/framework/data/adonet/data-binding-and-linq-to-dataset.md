---
title: 資料繫結和 LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: b081a648023aa21eea3a20ec409600d3bcbe9878
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073555"
---
# <a name="data-binding-and-linq-to-dataset"></a>資料繫結和 LINQ to DataSet
*資料繫結*是應用程式 UI 與商務邏輯之間建立連接的程序。 如果繫結具有正確的設定而且資料提供了適當的通知，當資料變更其值時，繫結至資料的項目就會自動反映變更。 <xref:System.Data.DataSet> 是記憶體中的資料表示，可提供一致的關聯式程式撰寫模型 (Programming Model)，不論它所包含的資料來源為何都一樣。 ADO.NET 2.0 <xref:System.Data.DataView> 可讓您排序和篩選儲存在 <xref:System.Data.DataTable> 中的資料。 這項功能通常用於資料繫結的應用程式。 您可以透過使用 <xref:System.Data.DataView>，以不同排序順序公開 (Expose) 資料表中的資料，而且可以按照資料列狀態或根據篩選條件運算式來篩選資料。 如需詳細資訊<xref:System.Data.DataView>物件，請參閱 < [Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓開發人員建立複雜且功能強大的查詢，透過<xref:System.Data.DataSet>使用[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]。 不過，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢傳回的列舉<xref:System.Data.DataRow>繫結案例中不容易使用的物件。 若要更容易進行繫結，您可以建立<xref:System.Data.DataView>從[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢。 這<xref:System.Data.DataView>使用的篩選和排序查詢中指定，但比較適合資料繫結。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 擴充的功能<xref:System.Data.DataView>藉由提供[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]運算式為基礎的篩選和排序，這可讓您更複雜且功能強大的篩選和排序比字串類篩選和排序作業。  
  
 請注意，<xref:System.Data.DataView> 代表查詢本身而不是查詢頂端的檢視。 <xref:System.Data.DataView> 會繫結至 UI 控制項 (例如 <xref:System.Windows.Forms.DataGrid> 或 <xref:System.Windows.Forms.DataGridView>)，以便提供簡單的資料繫結模型。 <xref:System.Data.DataView> 也可以從 <xref:System.Data.DataTable> 中建立，以便提供該資料表的預設檢視。  
  
## <a name="in-this-section"></a>本節內容  
 [建立 DataView 物件](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 提供有關建立 <xref:System.Data.DataView> 的資訊。  
  
 [使用 DataView 進行篩選](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 說明如何使用 <xref:System.Data.DataView> 進行篩選。  
  
 [使用 DataView 進行排序](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 說明如何使用 <xref:System.Data.DataView> 進行排序。  
  
 [查詢 DataView 中的 DataRowView 集合](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 提供查詢由 <xref:System.Data.DataRowView> 所公開之 <xref:System.Data.DataView> 集合的相關資訊。  
  
 [DataView 效能](../../../../docs/framework/data/adonet/dataview-performance.md)  
 提供有關 <xref:System.Data.DataView> 和效能的資訊。  
  
 [HOW TO：將 DataView 物件繫結至 Windows Forms DataGridView 控制項](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 說明如何將 <xref:System.Data.DataView> 物件繫結至 <xref:System.Windows.Forms.DataGridView>。  
  
## <a name="see-also"></a>另請參閱

- [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
