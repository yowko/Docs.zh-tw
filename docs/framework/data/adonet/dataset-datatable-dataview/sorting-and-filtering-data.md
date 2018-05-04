---
title: 排序及篩選資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 02a67a490eb8339663aac08c97c665ffee09f0df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sorting-and-filtering-data"></a>排序及篩選資料
<xref:System.Data.DataView> 提供數種可在 <xref:System.Data.DataTable> 中排序和篩選資料的方法：  
  
-   您可以使用 <xref:System.Data.DataView.Sort%2A> 屬性，指定單一或多個資料行的排序順序，並納入 ASC (遞增) 和 DESC (遞減) 參數。  
  
-   您可以使用 <xref:System.Data.DataView.ApplyDefaultSort%2A> 屬性，依照主索引鍵資料行或資料表之資料行來自動建立遞增的排序順序。 <xref:System.Data.DataView.ApplyDefaultSort%2A> 僅適用於當**排序**屬性為 null 參考或空字串，而當資料表有定義的主索引鍵。  
  
-   您可以使用 <xref:System.Data.DataView.RowFilter%2A> 屬性，依照其資料行的值來指定資料列子集。 如需有效運算式的詳細資訊**RowFilter**屬性，請參閱的參考資訊<xref:System.Data.DataColumn.Expression%2A>屬性<xref:System.Data.DataColumn>類別。  
  
     如果您想要傳回的資料，而不是提供資料子集的動態檢視的特定查詢的結果，請使用<xref:System.Data.DataView.Find%2A>或<xref:System.Data.DataView.FindRows%2A>方法**DataView**達到最佳效能而非設定**RowFilter**屬性。 設定**RowFilter**屬性會重建索引的資料加入至應用程式的額外負荷並降低效能。 **RowFilter**屬性最適合用於資料繫結應用程式繫結的控制項顯示篩選的結果的位置。 **尋找**和**FindRows**方法會使用目前的索引而不需要重建索引。 如需有關**尋找**和**FindRows**方法，請參閱[尋找資料列](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)。  
  
-   您可以使用 <xref:System.Data.DataView.RowStateFilter%2A> 屬性，指定要檢視的資料列版本。 **DataView**隱含管理要公開 （expose） 而定的資料列版本**RowState**基礎資料列。 例如，如果**RowStateFilter**設為**DataViewRowState.Deleted**、 **DataView**公開**原始**的資料列版本所有**刪除**資料列，所以沒有**目前**資料列版本。 您可以判斷資料列版本資料列的正在使用公開**RowVersion**屬性**DataRowView**。  
  
     下表顯示的選項**DataViewRowState**。  
  
    |DataViewRowState 選項|描述|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**目前**的所有資料列版本**Unchanged**， **Added**，和**Modified**資料列。 這是預設值。|  
    |**加入**|**目前**的所有資料列版本**Added**資料列。|  
    |**刪除**|**原始**的所有資料列版本**刪除**資料列。|  
    |**ModifiedCurrent**|**目前**的所有資料列版本**Modified**資料列。|  
    |**ModifiedOriginal**|**原始**的所有資料列版本**Modified**資料列。|  
    |**無**|無資料列。|  
    |**OriginalRows**|**原始**的所有資料列版本**Unchanged**， **Modified**，和**刪除**資料列。|  
    |**不變**|**目前**的所有資料列版本**Unchanged**資料列。|  
  
 如需有關資料列狀態和資料列版本的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
 下列程式碼範例所建立的檢視，可顯示庫存中所有單位數量低於或等於重新訂購層級的產品，而其檢視內容是依序由廠商 ID 和產品名稱進行排序。  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
