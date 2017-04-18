---
title: "Entity Framework 的 EntityClient 提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Entity Framework 的 EntityClient 提供者
EntityClient 提供者是 Entity Framework 應用程式用來存取概念模型中所描述之資料的資料提供者。  如需關於概念模型的詳細資訊，請參閱[模型化及對應檔案](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)。  EntityClient 會使用其他 .NET Framework 資料提供者來存取資料來源。  例如，EntityClient 會在存取 SQL Server 資料庫時使用 .NET Framework Data Provider for SQL Server \(SqlClient\)。  如需有關 SqlClient 提供者的詳細資訊，請參閱 [Entity Framework 函式的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)。  EntityClient 提供者是在 <xref:System.Data.EntityClient> 命名空間 \(Namespace\) 中實作的。  
  
## 管理連接  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會提供 <xref:System.Data.EntityClient.EntityConnection> 給基礎資料提供者和關聯式資料庫，利用這種方式建置於儲存體專用 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] 資料提供者之上。  若要建構 <xref:System.Data.EntityClient.EntityConnection> 物件，您必須參考包含必要模型與對應的中繼資料集，以及儲存體專用資料提供者和連接字串。  建構好 <xref:System.Data.EntityClient.EntityConnection> 之後，便可透過從概念模型產生的類別存取實體。  
  
 您可以在 app.config 檔案中指定連接字串。  
  
 <xref:System.Data.EntityClient> 也包含 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 類別。  這個類別可讓開發人員使用此類別的屬性和方法，以程式設計方式建立語法正確的連接字串，以及剖析和重建現有的連接字串。  如需詳細資訊，請參閱[HOW TO：建立 EntityConnection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)。  
  
## 建立查詢  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 語言是與儲存體無關的 SQL Dialect，可直接配合概念實體結構描述運作，並支援 Entity Data Model 概念 \(如繼承與關聯性\)。  <xref:System.Data.EntityClient.EntityCommand> 類別是用來針對實體模型執行 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 命令。  建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢文字。  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會與儲存區特定的資料提供者一起運作，將泛型 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 轉譯成儲存區特定的查詢。  如需有關撰寫 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢的詳細資訊，請參閱 [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)。  
  
 以下範例會建立 <xref:System.Data.EntityClient.EntityCommand> 物件並且將 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢文字指派給它的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=fullName> 屬性。  這個 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢會從概念模型要求依定價排序的產品。  下列程式碼完全不了解儲存模型的相關資訊。  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"` `SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## 執行查詢  
 執行查詢時，會先剖析查詢然後將它轉換成標準命令樹。  所有後續的查詢處理都是在此命令樹上執行。  命令樹是 <xref:System.Data.EntityClient> 與基礎 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 資料提供者 \(例如 <xref:System.Data.SqlClient>\) 之間的通訊方式。  
  
 <xref:System.Data.EntityClient.EntityDataReader> 會公開針對概念模型執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。  若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。  <xref:System.Data.EntityClient.EntityDataReader> 會實作 <xref:System.Data.IExtendedDataRecord> 來描述豐富的結構化結果。  
  
## 異動管理  
 Entity Framework 中有兩種使用交易的方式：自動與明確。  自動交易會使用 <xref:System.Transactions> 命名空間，而明確交易會使用 <xref:System.Data.EntityClient.EntityTransaction> 類別。  
  
 若要更新透過概念模型公開的資料，請參閱 [How to: Manage Transactions in the Entity Framework](http://msdn.microsoft.com/zh-tw/4a55eb7f-f826-4a48-9df1-aebe2352ebef)。  
  
## 本章節內容  
 [HOW TO：建立 EntityConnection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [HOW TO：執行可傳回 PrimitiveType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [HOW TO：執行會傳回 RefType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [HOW TO：執行可傳回複雜類型的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [HOW TO：執行可傳回巢狀集合的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [HOW TO：使用 EntityCommand 執行參數化 Entity SQL 查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [HOW TO：使用 EntityCommand 執行參數化預存程序](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [HOW TO：執行多型查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [HOW TO：使用 Navigate 運算子巡覽關聯性](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## 請參閱  
 [Managing Connections and Transactions](http://msdn.microsoft.com/zh-tw/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)   
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)   
 [語言參考](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)