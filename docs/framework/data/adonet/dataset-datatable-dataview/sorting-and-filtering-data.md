---
title: 排序及篩選資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 89e2fdf656fb06ee545ba936f033646ad86182d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183373"
---
# <a name="sorting-and-filtering-data"></a>排序及篩選資料

<xref:System.Data.DataView> 提供數種可在 <xref:System.Data.DataTable> 中排序和篩選資料的方法：  
  
- 您可以使用 <xref:System.Data.DataView.Sort%2A> 屬性，指定單一或多個資料行的排序順序，並納入 ASC (遞增) 和 DESC (遞減) 參數。  
  
- 您可以使用 <xref:System.Data.DataView.ApplyDefaultSort%2A> 屬性，依照主索引鍵資料行或資料表之資料行來自動建立遞增的排序順序。 <xref:System.Data.DataView.ApplyDefaultSort%2A> 只有當 **Sort** 屬性為 null 參考或空字串，以及資料表已定義主鍵時，才適用。  
  
- 您可以使用 <xref:System.Data.DataView.RowFilter%2A> 屬性，依照其資料行的值來指定資料列子集。 如需 **RowFilter** 屬性之有效運算式的詳細資訊，請參閱類別屬性的參考資訊 <xref:System.Data.DataColumn.Expression%2A> <xref:System.Data.DataColumn> 。  
  
     如果您想要傳回特定資料查詢的結果，而不是提供資料子集的動態視圖，請使用 <xref:System.Data.DataView.Find%2A> DataView 的或 <xref:System.Data.DataView.FindRows%2A> 方法來達到最佳效能，而不是**DataView**設定**RowFilter**屬性。 設定 **RowFilter** 屬性會重建資料的索引，並增加應用程式的負荷並降低效能。 **RowFilter**屬性最適合用於資料系結應用程式，其中繫結控制項會顯示篩選的結果。 **Find**和**FindRows**方法會利用目前的索引，而不需要重建索引。 如需 **Find** 和 **FindRows** 方法的詳細資訊，請參閱 [尋找資料列](finding-rows.md)。  
  
- 您可以使用 <xref:System.Data.DataView.RowStateFilter%2A> 屬性，指定要檢視的資料列版本。 **DataView**會根據基礎資料列的**RowState** ，隱含地管理要公開的資料列版本。 例如，如果**RowStateFilter**設定為**DataViewRowState**，則**DataView**會公開所有**已刪除**資料列的**原始**資料列版本，因為沒有**目前**的資料列版本。 您可以使用**DataRowView**的**RowVersion**屬性，判斷要公開的資料列版本。  
  
     下表顯示 **DataViewRowState**的選項。  
  
    |DataViewRowState 選項|描述|  
    |------------------------------|-----------------|  
    |**CurrentRows**|所有**未**變更、**新增**和**修改**資料列的**目前**資料列版本。 此為預設值。|  
    |**已加入**|所有**已加入**資料列的**目前**資料列版本。|  
    |**已刪除**|所有**已刪除**資料列的**原始**資料列版本。|  
    |**ModifiedCurrent**|所有**已修改**資料列的**目前**資料列版本。|  
    |**ModifiedOriginal**|所有**已修改**資料列的**原始**資料列版本。|  
    |**None**|無資料列。|  
    |**OriginalRows**|所有**未**變更、**已修改**和**已刪除**資料列的**原始**資料列版本。|  
    |**未變更**|所有**未**變更資料列的**目前**資料列版本。|  
  
 如需資料列狀態和資料列版本的詳細資訊，請參閱資料 [列狀態和](row-states-and-row-versions.md)資料列版本。  
  
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

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataView](dataviews.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
