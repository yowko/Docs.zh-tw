---
title: "將資料行加入至 DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將資料行加入至 DataTable
<xref:System.Data.DataTable> 包含資料表之 **Columns** 屬性所參考的 <xref:System.Data.DataColumn> 物件集合。  這個資料行集合 \(可搭配任何條件約束\) 可定義資料表的結構描述 \(或結構\)。  
  
 您可以使用 **DataColumn** 建構函式，或是呼叫資料表 \(其為 <xref:System.Data.DataColumnCollection>\) 之 **Columns** 屬性的 **Add** 方法，在資料表內建立 **DataColumn** 物件。  **Add** 方法可接受選擇項 **ColumnName**、**DataType** 和 **Expression** 引數，並建立新的 **DataColumn** 作為集合成員。  它也可接受現有的 **DataColumn** 物件，並將它加入集合中，然後應要求傳回加入之 **DataColumn** 的參考。  由於 **DataTable** 物件並非特定用於任何資料來源，因此指定 **DataColumn** 資料型別時將使用 .NET Framework 型別。  
  
 下列範例加入四個資料行到 **DataTable**。  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 請注意，在本範例中，**CustID** 資料行的屬性已設為不得使用 **DBNull** 值，並且已將值限制為唯一值。  但如果您將 **CustID** 資料行定義為資料表的主索引鍵資料行，**AllowDBNull** 屬性將自動設為 **false**，而 **Unique** 屬性將自動設為 **true**。  如需詳細資訊，請參閱[定義主索引鍵](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
> [!CAUTION]
>  若未提供資料行名稱給資料行，則在資料行加入 **DataColumnCollection** 時，就會指定 Column*N* 的累加預設名稱給資料行，從 Column1 開始。  當您提供資料行名稱時，建議您避免使用 "Column*N*" 的命名規則，因為您提供的名稱可能會與 **DataColumnCollection** 中現有的預設資料行名稱衝突。  如果提供的名稱已經存在，便會發生例外狀況。  
  
 如果您要使用 <xref:System.Xml.XLinq.XElement> 當做 <xref:System.Data.DataTable> 中 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataColumn.DataType%2A>，當您讀入資料時，XML 序列化將無法運作。  例如，如果您使用 `DataTable.WriteXml` 方法來寫出 <xref:System.Xml.XmlDocument>，在序列化至 XML 時，<xref:System.Xml.XLinq.XElement> 就會存在額外的父節點。  若要解決此問題，請使用 <xref:System.Data.SqlTypes.SqlXml> 型別而非 <xref:System.Xml.XLinq.XElement>。  `ReadXml` 和 `WriteXml` 會搭配 <xref:System.Data.SqlTypes.SqlXml> 正確運作。  
  
## 請參閱  
 <xref:System.Data.DataColumn>   
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataTable>   
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)