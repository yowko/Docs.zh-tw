---
title: AcceptChanges 和 RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: bbcc666b99c2bade479e5ee51750b043c820845d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879901"
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges 和 RejectChanges
在驗證中的資料變更的正確性之後<xref:System.Data.DataTable>，您可以接受變更<xref:System.Data.DataRow.AcceptChanges%2A>方法<xref:System.Data.DataRow>， <xref:System.Data.DataTable>，或<xref:System.Data.DataSet>，它會將設定**目前**資料列值必須是**原始**值，並將設定**RowState**屬性設**Unchanged**。 接受或拒絕變更會清除任何**RowError**資訊，並且**HasErrors**屬性設**false**。 接受或拒絕變更也會影響資料來源中的資料更新。 如需詳細資訊，請參閱 <<c0> [ 使用 Dataadapter 更新資料來源](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)。  
  
 如果上存在外部索引鍵條件約束**DataTable**，接受或拒絕使用變更**AcceptChanges**並**RejectChanges**會傳播至子資料列的**DataRow**根據**Datarow**。 如需詳細資訊，請參閱 < [DataTable 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。  
  
 下列範例會檢查發生錯誤的資料列、適當地解決錯誤，並且在無法解決錯誤時拒絕資料列。 請注意，對於已解決錯誤， **RowError**值會重設為空字串，導致**HasErrors**屬性設為**false**。 已解析或拒絕，發生錯誤的所有資料列時**AcceptChanges**呼叫以接受所有的變更，整個**DataTable**。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
