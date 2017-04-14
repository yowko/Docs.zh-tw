---
title: "排序和篩選資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 排序和篩選資料
<xref:System.Data.DataView> 提供數種可在 <xref:System.Data.DataTable> 中排序和篩選資料的方法：  
  
-   您可以使用 <xref:System.Data.DataView.Sort%2A> 屬性，指定單一或多個資料行的排序順序，並納入 ASC \(遞增\) 和 DESC \(遞減\) 參數。  
  
-   您可以使用 <xref:System.Data.DataView.ApplyDefaultSort%2A> 屬性，依照主索引鍵資料行或資料表之資料行來自動建立遞增的排序順序。  只有在 **Sort** 屬性為 Null 參考或空字串，以及資料表已定義主索引鍵時，才會套用 <xref:System.Data.DataView.ApplyDefaultSort%2A>。  
  
-   您可以使用 <xref:System.Data.DataView.RowFilter%2A> 屬性，依照其資料行的值來指定資料列子集。  如需 **RowFilter** 屬性之有效運算式的詳細資訊，請參閱 <xref:System.Data.DataColumn> 類別之 <xref:System.Data.DataColumn.Expression%2A> 屬性的參考資訊。  
  
     如果您想要傳回特定資料查詢的結果，但不要提供資料子集的動態檢視，請使用 **DataView** 的 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 方法，即可達到最佳效能，而不是設定 **RowFilter** 屬性。  設定 **RowFilter** 屬性會重建資料索引，因而增加應用程式耗用的資源並降低效能。  **RowFilter** 屬性最適於資料繫結應用程式，這種應用程式會用繫結控制項顯示篩選結果。  **Find** 和 **FindRows** 方法則可使用目前的索引，因此不需要重建索引。  如需 **Find** 和 **FindRows** 方法的詳細資訊，請參閱 [尋找資料列](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)。  
  
-   您可以使用 <xref:System.Data.DataView.RowStateFilter%2A> 屬性，指定要檢視的資料列版本。  **DataView** 會視基礎資料列的 **RowState**，隱含管理要公開的資料列版本。  例如，如果 **RowStateFilter** 設定為 **DataViewRowState.Deleted**，則 **DataView** 會公開所有 **Deleted** 資料列的 **Original** 資料列版本，因為已沒有 **Current** 資料列版本。  您可以使用 **DataRowView** 的 **RowVersion** 屬性，判斷公開的資料列版本為何。  
  
     下表顯示 **DataViewRowState** 的選項。  
  
    |DataViewRowState 選項|描述|  
    |-------------------------|--------|  
    |**CurrentRows**|所有 **Unchanged**、**Added** 和 **Modified** 資料列的 **Current** 資料列版本。  這是預設值。|  
    |**Added**|所有 **Added** 資料列的 **Current** 資料列版本。|  
    |**Deleted**|所有 **Deleted** 資料列的 **Original** 資料列版本。|  
    |**ModifiedCurrent**|所有 **Modified** 資料列的 **Current** 資料列版本。|  
    |**ModifiedOriginal**|所有 **Modified** 資料列的 **Original** 資料列版本。|  
    |**無**|無資料列。|  
    |**OriginalRows**|所有 **Unchanged**、**Modified** 和 **Deleted** 資料列的 **Original** 資料列版本。|  
    |**Unchanged**|所有 **Unchanged** 資料列的 **Current** 資料列版本。|  
  
 如需資料列狀態及資料列版本的相關資訊，請參閱 [資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
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
  
## 請參閱  
 <xref:System.Data.DataViewRowState>   
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)