---
title: AcceptChanges 和 RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: a8589b157bc2579a03d856b73802abc9a4b42855
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204085"
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges 和 RejectChanges
在確認對中<xref:System.Data.DataTable>的資料所做之變更的正確性之後, 您可以<xref:System.Data.DataRow> <xref:System.Data.DataRow.AcceptChanges%2A>使用、 <xref:System.Data.DataTable>或<xref:System.Data.DataSet>的方法接受變更, 這會將**目前**的資料列值設定為**原始**值, 並將**RowState**屬性設定為**未**變更。 接受或拒絕變更會清除任何**RowError**資訊, 並將**HasErrors**屬性設定為**false**。 接受或拒絕變更也會影響資料來源中的資料更新。 如需詳細資訊, 請參閱[使用 Dataadapter 更新資料來源](../updating-data-sources-with-dataadapters.md)。  
  
 如果**DataTable**上有 foreign key 條件約束, 使用**AcceptChanges**和**RejectChanges**所接受或拒絕的變更會根據 **ForeignKeyConstraint. AcceptRejectRule**。 如需詳細資訊, 請參閱[DataTable 條件約束](datatable-constraints.md)。  
  
 下列範例會檢查發生錯誤的資料列、適當地解決錯誤，並且在無法解決錯誤時拒絕資料列。 請注意, 對於已解決的錯誤, **RowError**值會重設為空字串, 導致**HasErrors**屬性設定為**false**。 當所有具有錯誤的資料列都已解決或被拒時, 會呼叫**AcceptChanges**以接受整個**DataTable**的所有變更。  
  
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
- [在 DataTable 中操作資料](manipulating-data-in-a-datatable.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
