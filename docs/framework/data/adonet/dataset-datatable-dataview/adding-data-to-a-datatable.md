---
title: "將資料加入至 DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6e05e8cb0c7de638e0c4efe74ffd27ab0dc45508
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="adding-data-to-a-datatable"></a>將資料加入至 DataTable
建立 <xref:System.Data.DataTable> 並使用資料行和條件約束定義其結構之後，即可將新資料列加入資料表。 若要加入新資料列，請將新變數宣告為 <xref:System.Data.DataRow> 型別。 新**DataRow**呼叫時，會傳回物件<xref:System.Data.DataTable.NewRow%2A>方法。 **DataTable**接著會建立**DataRow**物件基礎的資料表，結構所定義的<xref:System.Data.DataColumnCollection>。  
  
 下列範例示範如何建立新的資料列，藉由呼叫**NewRow**方法。  
  
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
  
 資料會插入新的資料列之後**新增**方法用來新增列<xref:System.Data.DataRowCollection>，下列程式碼所示。  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 您也可以呼叫**新增**方法，藉由傳遞陣列的值，將新的資料列型別為<xref:System.Object>，如下列範例所示。  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 傳遞做為輸入的值的陣列**物件**至**新增**方法會建立新資料表內的資料列，並將其資料行值設定為物件陣列中的值。 請注意，陣列值將根據其在資料表出現的順序，依序和資料行相符。  
  
 下列範例將 10 個資料列加入至新建立**客戶**資料表。  
  
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
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
