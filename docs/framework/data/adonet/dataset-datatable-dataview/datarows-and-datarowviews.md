---
title: DataRow 和 DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 8a98dc44eda9ebda09235193c58bd831fc52d04d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205098"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="fb2c2-102">DataRow 和 DataRowView</span><span class="sxs-lookup"><span data-stu-id="fb2c2-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="fb2c2-103"><xref:System.Data.DataView> 公開可列舉之 <xref:System.Data.DataRowView> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="fb2c2-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="fb2c2-104">**DataRowView**物件會將值公開為物件陣列, 這些是根據基礎資料表中的資料行名稱或序數參考來編制索引。</span><span class="sxs-lookup"><span data-stu-id="fb2c2-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="fb2c2-105"><xref:System.Data.DataRow>您可以使用**DataRowView 的**屬性, 存取 DataRowView 所公開的。 <xref:System.Data.DataRowView.Row%2A></span><span class="sxs-lookup"><span data-stu-id="fb2c2-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="fb2c2-106">當您使用**DataRowView**來查看值時, <xref:System.Data.DataView.RowStateFilter%2A> **DataView**的屬性會決定要公開基礎**DataRow**的哪個資料列版本。</span><span class="sxs-lookup"><span data-stu-id="fb2c2-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="fb2c2-107">如需使用**DataRow**存取不同資料列版本的詳細資訊, 請參閱資料[列狀態和資料列版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="fb2c2-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="fb2c2-108">下列程式碼範例顯示資料表內所有的目前值和原始值。</span><span class="sxs-lookup"><span data-stu-id="fb2c2-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb2c2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb2c2-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="fb2c2-110">DataView</span><span class="sxs-lookup"><span data-stu-id="fb2c2-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="fb2c2-111">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="fb2c2-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
