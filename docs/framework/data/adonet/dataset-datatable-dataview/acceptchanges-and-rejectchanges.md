---
title: AcceptChanges 和 RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: c537fa808fc6ba4c740e71bfd70fe9cd1f3bd31a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785569"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="af54c-102">AcceptChanges 和 RejectChanges</span><span class="sxs-lookup"><span data-stu-id="af54c-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="af54c-103">在確認對中<xref:System.Data.DataTable>的資料所做之變更的正確性之後，您可以<xref:System.Data.DataRow> <xref:System.Data.DataRow.AcceptChanges%2A>使用、 <xref:System.Data.DataTable>或<xref:System.Data.DataSet>的方法接受變更，這會將**目前**的資料列值設定為**原始**值，並將**RowState**屬性設定為**未**變更。</span><span class="sxs-lookup"><span data-stu-id="af54c-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="af54c-104">接受或拒絕變更會清除任何**RowError**資訊，並將**HasErrors**屬性設定為**false**。</span><span class="sxs-lookup"><span data-stu-id="af54c-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="af54c-105">接受或拒絕變更也會影響資料來源中的資料更新。</span><span class="sxs-lookup"><span data-stu-id="af54c-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="af54c-106">如需詳細資訊，請參閱[使用 Dataadapter 更新資料來源](../updating-data-sources-with-dataadapters.md)。</span><span class="sxs-lookup"><span data-stu-id="af54c-106">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="af54c-107">如果**DataTable**上有 foreign key 條件約束，使用**AcceptChanges**和**RejectChanges**所接受或**拒絕的變更會根據** **ForeignKeyConstraint. AcceptRejectRule**。</span><span class="sxs-lookup"><span data-stu-id="af54c-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="af54c-108">如需詳細資訊，請參閱[DataTable 條件約束](datatable-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="af54c-108">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="af54c-109">下列範例會檢查發生錯誤的資料列、適當地解決錯誤，並且在無法解決錯誤時拒絕資料列。</span><span class="sxs-lookup"><span data-stu-id="af54c-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="af54c-110">請注意，對於已解決的錯誤， **RowError**值會重設為空字串，導致**HasErrors**屬性設定為**false**。</span><span class="sxs-lookup"><span data-stu-id="af54c-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="af54c-111">當所有具有錯誤的資料列都已解決或被拒時，會呼叫**AcceptChanges**以接受整個**DataTable**的所有變更。</span><span class="sxs-lookup"><span data-stu-id="af54c-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af54c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af54c-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="af54c-113">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="af54c-113">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="af54c-114">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="af54c-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
