---
title: "AcceptChanges 和 RejectChanges | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# AcceptChanges 和 RejectChanges
驗證對 <xref:System.Data.DataTable> 中之資料所進行之變更的正確性之後，即可以使用 <xref:System.Data.DataRow>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的 <xref:System.Data.DataRow.AcceptChanges%2A> 方法接受變更，這樣會將 **Current** 資料列值設為 **Original** 值，並將 **RowState** 屬性設為 **Unchanged**。  接受或拒絕變更會清除任何 **RowError** 資訊，並且會將 **HasErrors** 屬性設為 **false**。  接受或拒絕變更也會影響資料來源中的資料更新。  如需詳細資訊，請參閱[以 DataAdapter 更新資料來源](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)。  
  
 如果 **DataTable** 有外部索引鍵條件約束，則使用 **AcceptChanges** 和 **RejectChanges** 接受或拒絕的變更都會根據 **ForeignKeyConstraint.AcceptRejectRule** 傳播至 **DataRow** 的子資料列。  如需詳細資訊，請參閱[DataTable 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。  
  
 下列範例會檢查發生錯誤的資料列、適當地解決錯誤，並且在無法解決錯誤時拒絕資料列。  請注意，對於已解決的錯誤，**RowError** 值將重設為空字串，進而讓 **HasErrors** 屬性設為 **false**。  當發生錯誤的所有資料列都已解決或拒絕後，將會呼叫 **AcceptChanges** 以接受整個 **DataTable** 中的所有變更。  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## 請參閱  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)