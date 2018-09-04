---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: daa8097bc5dfee203f988915b1e4a8bdcd2c50e0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515408"
---
# <a name="finding-rows"></a>尋找資料列
您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。 中值的搜尋區分大小寫**尋找**並**FindRows**取決於方法**CaseSensitive**基礎屬性<xref:System.Data.DataTable>。 搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。  
  
 **尋找**方法會傳回索引的整數<xref:System.Data.DataRowView>符合搜尋準則。 如果多個資料列符合搜尋準則，只有第一個相符的索引**DataRowView**會傳回。 如果找不到任何相符項目，**尋找**會傳回-1。  
  
 若要傳回符合多個資料列的搜尋結果，請使用**FindRows**方法。 **FindRows**運作方式就像**尋找**方法，但是它會傳回**DataRowView**參考中的所有相符資料列的陣列**DataView**。 如果找不到任何相符項目， **DataRowView**陣列會是空的。  
  
 若要使用**尋找**或**FindRows**方法，您必須指定排序順序： **ApplyDefaultSort**至**true**或使用**排序**屬性。 如果沒有指定任何順序，則會擲回例外狀況。  
  
 **尋找**並**FindRows**方法會採用值的陣列做為輸入的長度符合排序次序中的資料行數目。 排序單一資料行時，您可傳遞單一值。 如果排序順序包含多個資料行，則您傳遞的是物件陣列。 請注意，針對多個資料行排序，物件陣列中的值必須符合指定之資料行的順序**排序**屬性**DataView**。  
  
 下列程式碼範例所示**尋找**針對正在呼叫的方法**DataView**具有單一資料行排序次序。  
  
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
  
 如果您**排序**屬性會指定多個資料行，您都必須通過每個資料行搜尋值的物件陣列中所指定的順序**排序**屬性，如下列程式碼範例所示。  
  
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
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
