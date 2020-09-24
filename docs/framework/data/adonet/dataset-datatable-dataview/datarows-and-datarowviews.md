---
title: DataRow 和 DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: bce90c1d310178e66da7c758c6df2cd357199c8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153283"
---
# <a name="datarows-and-datarowviews"></a>DataRow 和 DataRowView

<xref:System.Data.DataView> 公開可列舉之 <xref:System.Data.DataRowView> 物件的集合。 **DataRowView**物件會將值公開為物件陣列，這些物件是以基礎資料表中之資料行的名稱或序數參考來編制索引。 您可以 <xref:System.Data.DataRow> 使用 DataRowView 的屬性，存取**DataRowView**所公開的 <xref:System.Data.DataRowView.Row%2A> 。 **DataRowView**  
  
 當您使用 **DataRowView**來查看值時， <xref:System.Data.DataView.RowStateFilter%2A> **DataView** 的屬性會決定要公開基礎 **DataRow** 的資料列版本。 如需使用 **DataRow**存取不同資料列版本的詳細資訊，請參閱資料 [列狀態和資料列版本](row-states-and-row-versions.md)。  
  
 下列程式碼範例顯示資料表內所有的目前值和原始值。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataView](dataviews.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
