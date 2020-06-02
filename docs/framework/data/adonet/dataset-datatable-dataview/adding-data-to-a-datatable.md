---
title: 將資料加入至 DataTable
description: 請參閱此範例程式碼，在您建立 DataTable 並使用資料行和條件約束定義其結構之後，將新的資料列加入至 ADO.NET 中的資料表。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 94ebc97d5f90b5bb92186ba6f33015633bd01127
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286930"
---
# <a name="adding-data-to-a-datatable"></a>將資料加入至 DataTable
建立 <xref:System.Data.DataTable> 並使用資料行和條件約束定義其結構之後，即可將新資料列加入資料表。 若要加入新資料列，請將新變數宣告為 <xref:System.Data.DataRow> 型別。 當您呼叫方法時，會傳回新的**DataRow**物件 <xref:System.Data.DataTable.NewRow%2A> 。 然後， **DataTable**會根據資料表的結構建立**DataRow**物件，如所定義 <xref:System.Data.DataColumnCollection> 。  
  
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
  
 將資料插入新的資料列之後，就會使用**add**方法將資料列加入至 <xref:System.Data.DataRowCollection> ，如下列程式碼所示。  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 您也可以呼叫**add**方法來加入新的資料列，方法是傳入值的陣列（類型為 <xref:System.Object> ），如下列範例所示。  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 將值陣列（類型為**Object**）傳遞至**Add**方法會在資料表內建立新資料列，並將其資料行值設定為物件陣列中的值。 請注意，陣列值將根據其在資料表出現的順序，依序和資料行相符。  
  
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
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
