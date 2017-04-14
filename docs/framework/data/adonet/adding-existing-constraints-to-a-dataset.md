---
title: "將現有條件約束加入 DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將現有條件約束加入 DataSet
**DataAdapter** 的 **Fill** 方法只使用來自資料來源的資料表資料行和資料列填入 <xref:System.Data.DataSet>；雖然條件約束一般是由資料來源所設定，但 **Fill** 方法預設不會將這個結構描述資訊加入 **DataSet**。  若要以資料來源的現有主索引鍵條件約束資訊填入 **DataSet**，您可以呼叫 **DataAdapter** 的 **FillSchema** 方法，或在呼叫 **Fill** 前先將 **DataAdapter** 的 **MissingSchemaAction** 屬性設定為 **AddWithKey**。  這樣能確保 **DataSet** 內的主索引鍵條件約束反映出資料來源內的主索引鍵條件約束。  不包含外部索引鍵條件約束資訊，且必須明確建立 \(如 [DataTable 條件約束](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md) 所示\)。  
  
 將資料填入 **DataSet** 前先將結構描述資訊加入其中，便能確保 **DataSet** 內的 <xref:System.Data.DataTable> 物件包含主索引鍵條件約束。  這麼一來，再次呼叫以填入 **DataSet** 時，便會使用主索引鍵資料行資訊來比對資料來源的新資料列和每個 **DataTable** 中的目前資料列，然後以資料來源的資料覆寫資料表中的目前資料。  若無結構描述資訊，則來自資料來源的新資料列會附加至 **DataSet**，而造成資料列重複。  
  
> [!NOTE]
>  如果資料來源中的資料行定義為自動遞增，則 **FillSchema** 方法或 **MissingSchemaAction** 為 **AddWithKey** 的 **Fill** 方法，會建立 **DataColumn**，並將其 **AutoIncrement** 屬性設為 `true`。  但是您必須自行設定 **AutoIncrementStep** 和 **AutoIncrementSeed** 的值。  如需自動遞增資料行的詳細資訊，請參閱 [建立 AutoIncrement 資料行](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)。  
  
 若您使用 **FillSchema** 或將 **MissingSchemaAction** 設定為 **AddWithKey**，則資料來源需要進行其他的作業來判斷主索引鍵資料行資訊。  這些其他作業可能會降低效能。  如果您在設計階段就已知道主索引鍵資訊，建議您明確地指定主索引鍵資料行，以達到最佳效能。  如需明確設定資料表之主索引鍵資訊的詳細資訊，請參閱 [定義主索引鍵](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
 下列程式碼範例顯示如何使用 **FillSchema** 將結構描述資訊加入 **DataSet**。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 下列程式碼範例顯示如何使用 **Fill** 方法的 **MissingSchemaAction.AddWithKey** 屬性，將結構描述資訊加入 **DataSet**。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## 處理多重結果集  
 如果 **DataAdapter** 發現從 **SelectCommand** 傳回的多個結果集，它便會在 **DataSet** 內建立多個資料表。  會給予資料表一個以零為基礎的 **Table** *N* 增量預設名稱，從 **Table** 開始，而非 "Table0"。  如果資料表名稱做為引數傳遞至 **FillSchema** 方法，則會給予資料表一個以零為基礎的 **TableName** *N* 增量名稱，從 **TableName** 開始，而非 "TableName0"。  
  
> [!NOTE]
>  若傳回多個結果集的命令呼叫 **OleDbDataAdapter** 物件的 **FillSchema** 方法，則只會傳回來自第一個結果集的結構描述資訊。  使用 **OleDbDataAdapter** 傳回多個結果集的結構描述資訊時，建議您指定 **AddWithKey** 的 **MissingSchemaAction**，並在呼叫 **Fill** 方法時取得結構描述資訊。  
  
## 請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [DataSet、DataTable 及 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)