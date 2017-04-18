---
title: "建立 DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 建立 DataTable
<xref:System.Data.DataTable> 表示記憶體中關聯式資料的某個資料表，它可以單獨建立及使用，也可以由其他 .NET Framework 物件所使用，而它最常見用法是做為 <xref:System.Data.DataSet> 的成員。  
  
 您可以使用適當的 **DataTable** 建構函式來建立 **DataTable** 物件。  您可以使用 **Add** 方法將它加入 **DataTable** 物件的 **Tables** 集合中，即可將它加入 **DataSet**。  
  
 您也可以使用 **DataAdapter** 物件的 **Fill** 或 **FillSchema** 方法，在 **DataSet** 中建立 **DataTable** 物件，或是使用 **DataSet** 的 **ReadXml**、**ReadXmlSchema** 或 **InferXmlSchema** 方法，從預先定義或推斷的 XML 結構描述建立 **DataSet** 物件。  請注意，當您將 **DataTable** 加入為某個 **DataSet** 之 **Tables** 集合的成員時，您無法將它加入至任何其他 **DataSet** 的資料表集合。  
  
 當您第一次建立 **DataTable** 時，它並不具有結構描述 \(亦即結構\)。  若要定義資料表的結構描述，則必須建立 <xref:System.Data.DataColumn> 物件，並將其加入資料表的 **Columns** 集合。  您也可以定義資料表的主索引鍵資料行，並且建立和加入 **Constraint** 物件到資料表的 **Constraints** 集合。  當您已定義 **DataTable** 的結構描述後，可以將資料列加入到資料表中，方法是將 **DataRow** 物件加入至資料表的 **Rows** 集合中。  
  
 建立 **DataTable** 時，不需提供 <xref:System.Data.DataTable.TableName%2A> 屬性的值；您可以在其他時候指定該屬性，或者將它保留空白。  然而，當您將不具 **TableName** 值的資料表加入至 **DataSet** 時，該資料表會指定 Table*N* 的累加預設名稱，從 "Table" 的 Table0 開始。  
  
> [!NOTE]
>  當您提供 **TableName** 值時，建議您避免使用 "Table*N*" 命名慣例，因為您所提供的名稱可能會與 **DataSet** 中現有的預設資料表名稱衝突。  如果提供的名稱已經存在，便會發生例外狀況。  
  
 下列範例將建立 **DataTable** 物件的執行個體，並為它指派 "Customers" 名稱。  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 下列範例將建立 **DataTable** 的執行個體，方法是將它加入至 **DataSet** 的 **Tables** 集合。  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## 請參閱  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataTableCollection>   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [從 DataAdapter 填入資料集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)