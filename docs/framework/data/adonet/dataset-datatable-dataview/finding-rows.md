---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151139"
---
# <a name="finding-rows"></a>尋找資料列
您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。 **Find**和**FindRows**方法中搜索值的區分度由基礎<xref:System.Data.DataTable>的**Case敏感**屬性確定。 搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。  
  
 **Find**方法返回一個整數，該整數與<xref:System.Data.DataRowView>搜尋條件匹配的索引。 如果多行與搜尋條件匹配，則僅返回第一個匹配**DataRowView**的索引。 如果未找到匹配項，**則查找**返回 -1。  
  
 要返回與多行匹配的搜尋結果，請使用**FindRows**方法。 **FindRows**的工作方式與**Find**方法類似，只不過它返回一個**資料羅視圖**陣列，該陣列引用**DataView**中的所有匹配行。 如果未找到匹配項 **，DataRowView**陣列將為空。  
  
 要使用 **"查找**"**或"查找行"** 方法，必須通過將 **"應用預設排序"** 設置為**true**或使用**排序**屬性來指定排序次序。 如果沒有指定任何順序，則會擲回例外狀況。  
  
 **Find**和**FindRows**方法採用一個值陣列作為輸入，其長度與排序次序中的列數匹配。 排序單一資料行時，您可傳遞單一值。 如果排序順序包含多個資料行，則您傳遞的是物件陣列。 請注意，對於對多個列的排序，物件陣列中的值必須與**DataView**的**Sort**屬性中指定的列的順序匹配。  
  
 以下代碼示例顯示針對具有單個列排序次序的**DataView**調用**的 Find**方法。  
  
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
  
 如果**Sort**屬性指定了多個列，則必須按照**Sort**屬性指定的順序傳遞具有每列搜索值的物件陣列，如以下代碼示例所示。  
  
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
