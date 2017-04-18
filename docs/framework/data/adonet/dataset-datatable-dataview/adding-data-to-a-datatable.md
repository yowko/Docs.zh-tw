---
title: "將資料加入至 DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將資料加入至 DataTable
建立 <xref:System.Data.DataTable> 並使用資料行和條件約束定義其結構之後，即可將新資料列加入資料表。  若要加入新資料列，請將新變數宣告為 <xref:System.Data.DataRow> 型別。  呼叫 <xref:System.Data.DataTable.NewRow%2A> 方法時，會傳回新的 **DataRow** 物件。  然後，**DataTable** 會根據 <xref:System.Data.DataColumnCollection> 所定義的資料表結構建立 **DataRow** 物件。  
  
 下列範例將展示如何呼叫 **NewRow** 方法來建立新的資料列。  
  
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
  
 將資料插入至新資料列之後，可使用 **Add** 方法將資料列加入至 <xref:System.Data.DataRowCollection> \(如下列程式碼所示\)。  
  
```vb  
workTable.Rows.Add(workRow)  
  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 您也可以呼叫 **Add** 方法來加入新資料列，方法是傳入值陣列 \(型別為 <xref:System.Object>\) \(如下列範例所示\)。  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 當您將值陣列 \(**Object** 本身\) 傳遞到 **Add** 方法時，資料表中會建立新的資料列，且其資料行值將設為物件陣列中的值。  請注意，陣列值將根據其在資料表出現的順序，依序和資料行相符。  
  
 下列範例將 10 個資料列加入到新建立的 **Customers** 資料表。  
  
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
  
## 請參閱  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataRowCollection>   
 <xref:System.Data.DataTable>   
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)