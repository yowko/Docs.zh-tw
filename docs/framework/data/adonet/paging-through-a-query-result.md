---
title: 逐頁查看查詢結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 5d86095586af273f62980fcf8ddf10804b1cfa5a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406806"
---
# <a name="paging-through-a-query-result"></a>逐頁查看查詢結果
將查詢結果分頁是以較小資料子集或頁傳回查詢結果的過程。 這是一種常用的方式，可將結果以小型、易於管理的區塊顯示給使用者。  
  
 **DataAdapter**傳回的資料，從多載的頁面上提供的設備**填滿**方法。 不過，這可能不是最適合逐頁查看大型的查詢結果，因為，雖然**DataAdapter**填入目標<xref:System.Data.DataTable>或<xref:System.Data.DataSet>只要求記錄時，要傳回的資源仍會使用整個查詢。 若您要從資料來源傳回一頁資料，並且不使用傳回整個查詢的資源，請為您的查詢指定其他準則，以將傳回的資料列縮小到必要的範圍內。  
  
 若要使用**填滿**方法來傳回一頁資料，指定**startRecord**參數，第一筆記錄，在頁面中的資料，和**maxRecords**參數的數目資料頁中的記錄。  
  
 下列程式碼範例示範如何使用**填滿**方法傳回查詢結果的第一頁的頁面大小為五筆記錄的位置。  
  
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
  
 在上述範例中，**資料集**只填入了五筆記錄，但整個**訂單**會傳回資料表。 若要填滿**資料集**這些相同的五筆記錄，但只傳回五筆記錄，同時使用 TOP 和 WHERE 子句，在 SQL 陳述式，如下列程式碼範例所示。  
  
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
  
 若要傳回下一頁記錄使用的多載**填滿**採用方法**startRecord**並**maxRecords**參數遞增目前的記錄索引的頁面大小和填滿資料表中。 請記住在資料庫伺服器會傳回整個查詢結果，即使只有一頁記錄新增至**資料集**。 下列程式碼範例中，資料表列會先經過清除後，再填入下一頁資料。 您可以在本機快取中保留特定數量的傳回資料列，來降低往返資料庫伺服器的次數。  
  
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
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
