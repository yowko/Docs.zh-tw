---
title: "DataAdapter DataTable 和 DataColumn 對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DataAdapter DataTable 和 DataColumn 對應
**DataAdapter** 的 **TableMappings** 屬性包含零或多個 <xref:System.Data.Common.DataTableMapping> 物件的集合。  **DataTableMapping** 提供查詢資料來源所傳回的資料與 <xref:System.Data.DataTable> 之間的主要對應。  您可傳遞 **DataTableMapping** 名稱，將 **DataTable** 名稱取代為 **DataAdapter** 的 **Fill** 方法。  下列範例為 **Authors** 資料表建立名為 **AuthorsMapping** 的 **DataTableMapping**。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping** 可讓您在 **DataTable** 中使用與資料庫中不同的資料行名稱。  資料表更新後，**DataAdapter** 便使用對應來比對資料行。  
  
 若未指定 **TableName** 或 **DataTableMapping** 名稱就呼叫 **DataAdapter** 的 **Fill** 或 **Update** 方法，**DataAdapter** 會尋找名為 "Table" 的 **DataTableMapping**。  如果 **DataTableMapping** 不存在，則 **DataTable** 的 **TableName** 為 "Table"。  您可以建立名為 "Table" 的 **DataTableMapping** 來指定預設 **DataTableMapping**。  
  
 下列程式碼範例從 <xref:System.Data.Common> 命名空間建立 **DataTableMapping**，並將其命名為 "Table"，使它成為所指定 **DataAdapter** 的預設對應。  接著，範例將查詢結果中之第一個資料表的資料行 \(**Northwind** 資料庫的 **Customers** 資料表\) 對應至 <xref:System.Data.DataSet> 之 **Northwind Customers** 資料表內一組更方便使用的名稱。  未被對應的資料行會使用來自資料來源的資料行名稱。  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 在更為進階的情況中，您可能決定要以同一個 **DataAdapter** 載入具有不同對應的不同資料表。  您只要另外加上 **DataTableMapping** 物件即可完成這項作業。  
  
 當您將 **DataSet** 的執行個體和 **DataTableMapping** 名稱傳遞給 **Fill** 方法時，除非使用具有該名稱的對應，否則便會使用具有這個名稱的 **DataTable**。  
  
 下列範例使用 **Customers** 名稱建立 **DataTableMapping**，並以 **BizTalkSchema** 名稱建立 **DataTable**。  接著，範例將 SELECT 陳述式傳回的資料列對應至 **BizTalkSchema** **DataTable**。  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
>  若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。  如果沒有來源資料行提供給資料行對應，該資料行對應會指定 **SourceColumn** *N* 的遞增預設名稱，從 **SourceColumn1** 開始。  如果沒有來源資料表提供給資料表對應，該資料表對應會指定 **SourceTable** *N* 的遞增預設名稱，從 **SourceTable1** 開始。  
  
> [!NOTE]
>  若為資料行對應，我們建議您避免命名慣例 **SourceColumn** *N*；若為資料表對應，我們建議您避免命名慣例 **SourceTable** *N*，因為您提供的名稱，可能與 **ColumnMappingCollection** 中的現有預設資料行對應名稱發生衝突，或與 **DataTableMappingCollection** 中的資料表對應名稱衝突。  如果提供的名稱已經存在，便會擲回例外狀況。  
  
## 處理多重結果集  
 如果您的 **SelectCommand** 傳回多個資料表，**Fill** 會自動針對 **DataSet** 中的資料表產生具遞增值的資料表名稱，從特定資料表名稱開始 \(從 **TableName1** 開始\)，並且以形式 **TableName** *N* 繼續。  您可以使用資料表對應，將自動產生的資料表名稱對應至您要指定給**DataSet**內資料表的名稱。  例如，如果是針對傳回兩個資料表 **Customers** 和 **Orders** 的 **SelectCommand**，請對 **Fill** 發出下列呼叫。  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 這兩個資料表建立於 **DataSet** 中：**Customers** 與 **Customers1**。  您可以使用資料對應來確保第二個資料表名為 **Orders**，而不是 **Customers1**。  若要執行這項作業，請將來源資料表 **Customers1** 對應至 **DataSet** 資料表 **Orders**，如下列範例所示。  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## 請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)