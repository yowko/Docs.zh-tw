---
title: AcceptChanges 和 RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: 65e47bafda3e3e47241405c9c8b8e3b4b0055601
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="b92a2-102">AcceptChanges 和 RejectChanges</span><span class="sxs-lookup"><span data-stu-id="b92a2-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="b92a2-103">在驗證中的資料所做的變更的正確性之後<xref:System.Data.DataTable>，您可以接受變更<xref:System.Data.DataRow.AcceptChanges%2A>方法<xref:System.Data.DataRow>， <xref:System.Data.DataTable>，或<xref:System.Data.DataSet>，它會將設定**目前**資料列值為**原始**值，並將設定**RowState**屬性**Unchanged**。</span><span class="sxs-lookup"><span data-stu-id="b92a2-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="b92a2-104">接受或拒絕變更會清除任何**RowError**資訊，並且**HasErrors**屬性**false**。</span><span class="sxs-lookup"><span data-stu-id="b92a2-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="b92a2-105">接受或拒絕變更也會影響資料來源中的資料更新。</span><span class="sxs-lookup"><span data-stu-id="b92a2-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="b92a2-106">如需詳細資訊，請參閱[以 Dataadapter 更新資料來源](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)。</span><span class="sxs-lookup"><span data-stu-id="b92a2-106">For more information, see [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="b92a2-107">如果 foreign key 條件約束上存在**DataTable**，變更接受或拒絕使用**AcceptChanges**和**RejectChanges**會傳播至子資料列的**DataRow**根據**Datarow**。</span><span class="sxs-lookup"><span data-stu-id="b92a2-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="b92a2-108">如需詳細資訊，請參閱[DataTable 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="b92a2-108">For more information, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="b92a2-109">下列範例會檢查發生錯誤的資料列、適當地解決錯誤，並且在無法解決錯誤時拒絕資料列。</span><span class="sxs-lookup"><span data-stu-id="b92a2-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="b92a2-110">請注意，對於已解決錯誤， **RowError**值會重設為空字串，造成**HasErrors**屬性設定為**false**。</span><span class="sxs-lookup"><span data-stu-id="b92a2-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="b92a2-111">當具有錯誤的所有資料列已解析或拒絕， **AcceptChanges**呼叫以接受所有的變更，對於整個**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="b92a2-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b92a2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b92a2-112">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="b92a2-113">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="b92a2-113">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="b92a2-114">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b92a2-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
