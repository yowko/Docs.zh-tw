---
title: 逐頁查看查詢結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 2e7fb97e5c0cb42deff43c411f47e8d30e2257ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149384"
---
# <a name="paging-through-a-query-result"></a>逐頁查看查詢結果
將查詢結果分頁是以較小資料子集或頁傳回查詢結果的過程。 這是一種常用的方式，可將結果以小型、易於管理的區塊顯示給使用者。  
  
 **DataAdapter**提供了一個工具，用於通過**填充**方法的重載僅返回一頁數據。 但是，這可能不是通過大型查詢結果分頁的最佳選擇，因為儘管**DataAdapter**填充了目標<xref:System.Data.DataTable>或<xref:System.Data.DataSet>僅包含請求的記錄，但仍使用返回整個查詢的資源。 若您要從資料來源傳回一頁資料，並且不使用傳回整個查詢的資源，請為您的查詢指定其他準則，以將傳回的資料列縮小到必要的範圍內。  
  
 要使用**Fill**方法返回資料頁，請為數據頁中的第一個記錄指定**startRecord**參數，並為數據頁中的記錄數指定**maxRecord**參數。  
  
 以下代碼示例演示如何使用**Fill**方法返回查詢結果的第一頁，其中頁面大小為五條記錄。  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 在前面的示例中 **，DataSet**只填充五條記錄，但返回整個**訂單**表。 要用這五條記錄填充**DataSet，** 但僅返回五條記錄，請使用 SQL 語句中的 TOP 和 WHERE 子句，如以下代碼示例所示。  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 請注意，若以這種方式進行查詢結果的分頁，您必須保留用來排序資料列的唯一識別項，才能將唯一 ID 傳遞給命令以傳回下一頁記錄，如下列程式碼範例所示。  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 要使用取**startRecord**和**maxRecord**參數的**Fill**方法重載返回記錄的下一頁，請按頁大小增加目前記錄索引並填充表。 請記住，資料庫伺服器返回整個查詢結果，即使只向**DataSet**添加了一頁記錄。 下列程式碼範例中，資料表列會先經過清除後，再填入下一頁資料。 您可以在本機快取中保留特定數量的傳回資料列，來降低往返資料庫伺服器的次數。  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 若要在資料庫伺服器不傳回整個查詢的情況下，傳回下一頁記錄，請對 SELECT 陳述式指定限制準則。 由於前面的範例保留了最後傳回的記錄，因此您可以在 WHERE 子句使用它來指定查詢的起始點，如下列範例所示。  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a>另請參閱

- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
