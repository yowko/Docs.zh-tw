---
title: 將資料加入至 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 91c635e2bc2ed617e8c45171d9ec7d7359b9ca88
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205486"
---
# <a name="adding-data-to-a-datatable"></a>將資料加入至 DataTable
建立 <xref:System.Data.DataTable> 並使用資料行和條件約束定義其結構之後，即可將新資料列加入資料表。 若要加入新資料列，請將新變數宣告為 <xref:System.Data.DataRow> 型別。 當您呼叫<xref:System.Data.DataTable.NewRow%2A>方法時, 會傳回新的 DataRow 物件。 然後, **DataTable**會根據資料表的結構建立**DataRow**物件, 如所<xref:System.Data.DataColumnCollection>定義。  
  
 下列範例示範如何藉由呼叫**NewRow**方法來建立新的資料列。  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 接下來您可以使用索引或資料行名稱來管理新加入的資料列，如下列範例所示。  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 將資料插入新的資料列之後, 就會使用**add**方法將資料列加入至<xref:System.Data.DataRowCollection>, 如下列程式碼所示。  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 您也可以呼叫**add**方法來加入新的資料列, 方法是傳入值的陣列 (類型為<xref:System.Object>), 如下列範例所示。  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 將值陣列 (類型為**Object**) 傳遞至**Add**方法會在資料表內建立新資料列, 並將其資料行值設定為物件陣列中的值。 請注意，陣列值將根據其在資料表出現的順序，依序和資料行相符。  
  
 下列範例會在新建立的**Customers**資料表中加入10個數據列。  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [在 DataTable 中操作資料](manipulating-data-in-a-datatable.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
