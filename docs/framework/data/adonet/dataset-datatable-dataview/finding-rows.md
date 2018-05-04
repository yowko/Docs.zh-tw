---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 57ed6045ca0ea9f9579640839e8198716cf79fe0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="finding-rows"></a>尋找資料列
您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。 區分大小寫的搜尋中的值**尋找**和**FindRows**方法由**CaseSensitive**基礎屬性<xref:System.Data.DataTable>。 搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。  
  
 **尋找**方法會傳回索引的整數<xref:System.Data.DataRowView>符合搜尋準則。 如果多個資料列符合搜尋準則，只有第一個相符的索引**DataRowView**傳回。 如果找不到相符的項目，**尋找**傳回-1。  
  
 若要傳回符合多個資料列的搜尋結果，請使用**FindRows**方法。 **FindRows**運作方式就像**尋找**方法，但是它會傳回**DataRowView**陣列參考中的所有相符資料列**DataView**。 如果找不到相符的項目， **DataRowView**陣列會是空的。  
  
 若要使用**尋找**或**FindRows**方法，您必須指定排序順序**ApplyDefaultSort**至**true**或使用**排序**屬性。 如果沒有指定任何順序，則會擲回例外狀況。  
  
 **尋找**和**FindRows**方法會採用值的陣列做為輸入的長度符合排序順序中的資料行數目。 排序單一資料行時，您可傳遞單一值。 如果排序順序包含多個資料行，則您傳遞的是物件陣列。 請注意，排序多個資料行時，物件陣列中的值必須符合指定之資料行的順序**排序**屬性**DataView**。  
  
 下列程式碼範例示範**尋找**方法呼叫對**DataView**具有單一資料行排序順序。  
  
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
  
 如果您**排序**屬性指定多個資料行時，您必須傳遞具有每個資料行搜尋值的物件陣列中所指定的順序**排序**屬性，如下列程式碼範例所示。  
  
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
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
