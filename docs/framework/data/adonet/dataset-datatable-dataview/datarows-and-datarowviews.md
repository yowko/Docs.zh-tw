---
title: DataRow 和 DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: fba160cb1f6948aa57221ff42ad9b0d673b88749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762867"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="c5eaa-102">DataRow 和 DataRowView</span><span class="sxs-lookup"><span data-stu-id="c5eaa-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="c5eaa-103"><xref:System.Data.DataView> 公開可列舉之 <xref:System.Data.DataRowView> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="c5eaa-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="c5eaa-104">**DataRowView**物件將值公開為物件陣列，會依名稱或序數參考的基礎資料表中的資料行編製索引。</span><span class="sxs-lookup"><span data-stu-id="c5eaa-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="c5eaa-105">您可以存取<xref:System.Data.DataRow>公開**DataRowView**使用<xref:System.Data.DataRowView.Row%2A>屬性**DataRowView**。</span><span class="sxs-lookup"><span data-stu-id="c5eaa-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="c5eaa-106">當使用檢視值**DataRowView**、<xref:System.Data.DataView.RowStateFilter%2A>屬性**DataView**判斷哪一個資料列版本的基礎**DataRow**公開。</span><span class="sxs-lookup"><span data-stu-id="c5eaa-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="c5eaa-107">如需有關存取使用不同的資料列版本資訊**DataRow**，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="c5eaa-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="c5eaa-108">下列程式碼範例顯示資料表內所有的目前值和原始值。</span><span class="sxs-lookup"><span data-stu-id="c5eaa-108">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)      
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5eaa-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5eaa-109">See Also</span></span>  
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="c5eaa-110">DataView</span><span class="sxs-lookup"><span data-stu-id="c5eaa-110">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="c5eaa-111">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c5eaa-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
