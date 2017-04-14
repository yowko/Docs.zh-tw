---
title: "修改 DataView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 修改 DataView
您可以使用 <xref:System.Data.DataView> 加入、刪除或修改基底資料表中的資料列。  **DataView** 有三個布林值 \(Boolean\) 屬性，只要設定其中任一個，就能使用 **DataView** 修改基底資料表的資料。  這些屬性是 <xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> 和 <xref:System.Data.DataView.AllowDelete%2A>。  它們都預設為 **true**。  
  
 如果 **AllowNew** 為 **true**，則可使用 **DataView** 的 <xref:System.Data.DataView.AddNew%2A> 方法來建立新的 <xref:System.Data.DataRowView>。  請注意，除非呼叫 **DataRowView** 的 <xref:System.Data.DataRowView.EndEdit%2A> 方法，否則不會將新資料列確實加入基礎 <xref:System.Data.DataTable> 中。  如果呼叫 **DataRowView** 的 <xref:System.Data.DataRowView.CancelEdit%2A> 方法，則會捨棄新的資料列。  另一點要注意的是您一次只能編輯一項 **DataRowView**。  如果您在暫止資料列存在時，呼叫 **DataRowView** 的 **AddNew** 或 **BeginEdit** 方法，就會在暫止資料列上隱含呼叫 **EndEdit**。  **EndEdit** 被呼叫後，變更會套用至基礎 **DataTable**，而您稍後可使用 **DataTable**、**DataSet** 或 **DataRow** 物件的 **AcceptChanges** 或 **RejectChanges** 方法來認可或拒絕變更。  如果 **AllowNew** 為 **false**，則您呼叫 **DataRowView** 的 **AddNew** 方法時會擲回例外狀況。  
  
 如果 **AllowEdit** 為 **true**，則您可以透過 **DataRowView** 修改 **DataRow** 的內容。  您可以使用 **DataRowView.EndEdit** 將變更確認至基礎資料列中，或是使用 **DataRowView.CancelEdit** 拒絕變更。  請注意您一次只能編輯一筆資料列。  如果您在暫止資料列存在時，呼叫 **DataRowView** 的 **AddNew** 或 **BeginEdit** 方法，就會在暫止資料列上隱含呼叫 **EndEdit**。  **EndEdit** 被呼叫後，建議的變更會放入基礎 **DataRow** 的 **Current** 資料列版本，而您稍後可使用 **DataTable**、**DataSet** 或 **DataRow** 物件的 **AcceptChanges** 或 **RejectChanges** 方法來認可或拒絕變更。  如果 **AllowEdit** 為 **false**，則您嘗試修改 **DataView** 的值時，會擲回例外狀況。  
  
 現有 **DataRowView** 經過編輯後，基礎 **DataTable** 的事件仍會與建議的變更一起被引發。  請注意，如果您呼叫基礎 **DataRow** 的 **EndEdit** 或 **CancelEdit**，則不管 **DataRowView** 上是否有呼叫 **EndEdit** 或 **CancelEdit**，暫止變更仍會被套用或取消。  
  
 如果 **AllowDelete** 為 **true**，則您可以使用 **DataView** 或 **DataRowView** 物件的 **Delete** 方法，從 **DataView** 刪除資料列，這樣資料列就會從基礎 **DataTable** 中刪除。  您稍後可使用 **AcceptChanges** 來認可刪除，或使用 **RejectChanges** 來拒絕刪除。  如果 **AllowDelete** 為 **false**，則您呼叫 **DataView** 或 **DataRowView** 的 **Delete** 方法時會擲回例外狀況。  
  
 下列程式碼範例使用 **DataView** 停用資料列的刪除，並使用 **DataView** 將新資料列加入基底資料表。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## 請參閱  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 <xref:System.Data.DataRowView>   
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)