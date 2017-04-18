---
title: "定義主索引鍵 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 定義主索引鍵
資料庫資料表通常會有資料行或資料行群組，可唯一識別資料表的每個資料列。  這個識別欄位或資料行群組又稱為主索引鍵。  
  
 當您將單一 <xref:System.Data.DataColumn> 識別為 <xref:System.Data.DataTable> 的 <xref:System.Data.DataTable.PrimaryKey%2A> 時，資料表會自動將資料行的 <xref:System.Data.DataColumn.AllowDBNull%2A> 屬性設為 **false**，並將 <xref:System.Data.DataColumn.Unique%2A> 屬性設為 **true**。  如果是多重資料行的主索引鍵，則只有 **AllowDBNull** 屬性會自動設為 **false**。  
  
 <xref:System.Data.DataTable> 的 **PrimaryKey** 屬性接收一或多個 **DataColumn** 物件的陣列做為其值，如下列範例所示。  第一個範例定義單一資料行為主索引鍵。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 下列範例定義兩個資料行作為主索引鍵。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## 請參閱  
 <xref:System.Data.DataTable>   
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)