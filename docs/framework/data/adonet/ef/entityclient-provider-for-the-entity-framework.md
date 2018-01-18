---
title: "Entity Framework 的 EntityClient 提供者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eaccace7a333903e236107a72dbc17e19dc8d48a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework 的 EntityClient 提供者
EntityClient 提供者是 Entity Framework 應用程式用來存取概念模型中所描述之資料的資料提供者。 概念模型的相關資訊，請參閱[模型和對應](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)。 EntityClient 會使用其他 .NET Framework 資料提供者來存取資料來源。 例如，EntityClient 會在存取 SQL Server 資料庫時使用 .NET Framework Data Provider for SQL Server (SqlClient)。 如需 SqlClient 提供者資訊，請參閱[適用於 Entity Framework 的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)。 EntityClient 提供者是在 <xref:System.Data.EntityClient> 命名空間 (Namespace) 中實作的。  
  
## <a name="managing-connections"></a>管理連接  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]是建置基礎儲存區特定[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]藉由提供資料提供者<xref:System.Data.EntityClient.EntityConnection>到基礎資料提供者和關聯式資料庫。 若要建構<xref:System.Data.EntityClient.EntityConnection>物件，您必須參考一組包含必要的模型和對應，以及儲存體專用資料提供者名稱和連接字串的中繼資料。 之後<xref:System.Data.EntityClient.EntityConnection>為就地，實體可以存取透過從概念模型產生的類別。  
  
 您可以在 app.config 檔案中指定連接字串。  
  
 <xref:System.Data.EntityClient> 也包含 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 類別。 這個類別可讓開發人員使用此類別的屬性和方法，以程式設計方式建立語法正確的連接字串，以及剖析和重建現有的連接字串。 如需詳細資訊，請參閱[如何： 建置 Entitycollection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)。  
  
## <a name="creating-queries"></a>建立查詢  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)]語言是儲存體無關的 SQL dialect，直接搭配概念實體結構描述運作，且支援 Entity Data Model 概念，例如繼承和關聯性。 <xref:System.Data.EntityClient.EntityCommand>類別用來執行[!INCLUDE[esql](../../../../../includes/esql-md.md)]命令針對實體模型。 建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢文字。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會與儲存區特定的資料提供者一起運作，將泛型 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 轉譯成儲存區特定的查詢。 如需有關撰寫[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢，請參閱[Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)。  
  
 下列範例會建立<xref:System.Data.EntityClient.EntityCommand>物件，並指派[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢文字，以其<xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>屬性。 這[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢要求排序依據標價，從概念模型的產品。 下列程式碼完全不了解儲存模型的相關資訊。  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"` `SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>執行查詢  
 執行查詢時，會先剖析查詢然後將它轉換成標準命令樹。 所有後續的查詢處理都是在此命令樹上執行。 命令樹是 <xref:System.Data.EntityClient> 與基礎 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 資料提供者 (例如 <xref:System.Data.SqlClient>) 之間的通訊方式。  
  
 <xref:System.Data.EntityClient.EntityDataReader> 會公開針對概念模型執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。 若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。 <xref:System.Data.EntityClient.EntityDataReader> 會實作 <xref:System.Data.IExtendedDataRecord> 來描述豐富的結構化結果。  
  
## <a name="managing-transactions"></a>異動管理  
 Entity Framework 中有兩種使用交易的方式：自動與明確。 自動交易會使用 <xref:System.Transactions> 命名空間，而明確交易會使用 <xref:System.Data.EntityClient.EntityTransaction> 類別。  
  
 若要更新概念模型中; 透過公開的資料請參閱[如何： 管理 Entity Framework 中的交易](http://msdn.microsoft.com/en-us/4a55eb7f-f826-4a48-9df1-aebe2352ebef)。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建置 EntityCollection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [如何：執行可傳回 PrimitiveType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [如何：執行可傳回 RefType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [如何：執行可傳回複雜類型的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [如何：執行可傳回巢狀集合的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [如何：使用 EntityCommand 執行參數化 Entity SQL 查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [如何：使用 EntityCommand 執行參數化預存程序](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [如何：執行多型查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [如何：使用 Navigate 運算子導覽關聯性 ](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>請參閱  
 [管理連接與交易](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [語言參考](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
