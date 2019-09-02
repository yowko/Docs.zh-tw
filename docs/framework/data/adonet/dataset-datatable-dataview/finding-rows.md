---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 2ff2b6b6d00c854d07f36d37986268a388c7f31b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203711"
---
# <a name="finding-rows"></a>尋找資料列
您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。 **Find**和**FindRows**方法中搜尋值的區分大小寫, 是由基礎<xref:System.Data.DataTable>的**CaseSensitive**屬性所決定。 搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。  
  
 **Find**方法會傳回一個整數, 其中包含符合搜尋<xref:System.Data.DataRowView>條件之的索引。 如果有多個資料列符合搜尋準則, 則只會傳回第一個相符**DataRowView**的索引。 如果找不到相符專案, 則**Find**會傳回-1。  
  
 若要傳回符合多個資料列的搜尋結果, 請使用**FindRows**方法。 **FindRows**的運作方式就像**Find**方法, 不同之處在于它會傳回參考**DataView**中所有相符資料列的**DataRowView**陣列。 如果找不到相符專案, **DataRowView**陣列將會是空的。  
  
 若要使用**Find**或**FindRows**方法, 您必須指定排序次序, 方法是將**ApplyDefaultSort**設定為**true** , 或使用**sort**屬性。 如果沒有指定任何順序，則會擲回例外狀況。  
  
 **Find**和**FindRows**方法會將值的陣列當做輸入, 其長度符合排序次序中的資料行數目。 排序單一資料行時，您可傳遞單一值。 如果排序順序包含多個資料行，則您傳遞的是物件陣列。 請注意, 針對多個資料行進行排序時, 物件陣列中的值必須符合**DataView**的**sort**屬性中所指定的資料行順序。  
  
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
  
 如果您的**Sort**屬性指定多個資料行, 您必須以**Sort**屬性所指定的順序, 以每個資料行的搜尋值傳遞物件陣列, 如下列程式碼範例所示。  
  
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
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
