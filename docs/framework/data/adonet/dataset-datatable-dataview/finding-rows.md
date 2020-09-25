---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: dc0661e29e6d3ee5aa3f54179e8abf265cd67d58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186974"
---
# <a name="finding-rows"></a>尋找資料列

您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。 **Find**和**FindRows**方法中搜尋值的區分大小寫取決於基礎的**CaseSensitive**屬性 <xref:System.Data.DataTable> 。 搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。  
  
 **Find**方法會傳回具有符合搜尋準則之索引的整數 <xref:System.Data.DataRowView> 。 如果有一個以上的資料列符合搜尋準則，則只會傳回第一個符合 **DataRowView** 的索引。 如果找不到相符專案，則 **尋找** 會傳回-1。  
  
 若要傳回符合多個資料列的搜尋結果，請使用 **FindRows** 方法。 **FindRows**的運作方式與**Find**方法相同，不同之處在于它會傳回參考**DataView**中所有相符資料列的**DataRowView**陣列。 如果找不到相符專案， **DataRowView** 陣列將會是空的。  
  
 若要使用 **Find** 或 **FindRows** 方法，您必須指定排序次序，方法是將 **ApplyDefaultSort** 設定為 **true** 或使用 **sort** 屬性。 如果沒有指定任何順序，則會擲回例外狀況。  
  
 **Find**和**FindRows**方法會採用值的陣列作為輸入，其長度會符合排序次序中的資料行數目。 排序單一資料行時，您可傳遞單一值。 如果排序順序包含多個資料行，則您傳遞的是物件陣列。 請注意，對於多個資料行的排序，物件陣列中的值必須符合**DataView**的**sort**屬性中所指定之資料行的順序。  
  
 下列程式碼範例示範如何針對具有單一資料行排序次序的**DataView**呼叫**Find**方法。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 如果您的 **sort** 屬性指定多個資料行，您就必須依照 **Sort** 屬性所指定的順序來傳遞具有每個資料行之搜尋值的物件陣列，如下列程式碼範例所示。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataView](dataviews.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
