---
title: Entity Framework 的 EntityClient 提供者
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 268608c82070e60007bc09f97a775918e0d950f3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583703"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework 的 EntityClient 提供者
EntityClient 提供者是 Entity Framework 應用程式用來存取概念模型中所描述之資料的資料提供者。 如需概念模型的資訊，請參閱[模型和對應](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)。 EntityClient 會使用其他 .NET Framework 資料提供者來存取資料來源。 例如，EntityClient 會在存取 SQL Server 資料庫時使用 .NET Framework Data Provider for SQL Server (SqlClient)。 SqlClient 提供者的相關資訊，請參閱[適用於 Entity Framework 的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)。 EntityClient 提供者是在 <xref:System.Data.EntityClient> 命名空間 (Namespace) 中實作的。  
  
## <a name="managing-connections"></a>管理連接  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]建置在儲存體專用[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]資料提供者，藉由提供<xref:System.Data.EntityClient.EntityConnection>到基礎資料提供者和關聯式資料庫。 若要建構<xref:System.Data.EntityClient.EntityConnection>物件，您必須參考一組包含必要模型和對應，以及儲存專用的資料提供者名稱和連接字串的中繼資料。 之後<xref:System.Data.EntityClient.EntityConnection>是就地的情況下，實體可以透過從概念模型產生的類別。  
  
 您可以在 app.config 檔案中指定連接字串。  
  
 <xref:System.Data.EntityClient> 也包含 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 類別。 這個類別可讓開發人員使用此類別的屬性和方法，以程式設計方式建立語法正確的連接字串，以及剖析和重建現有的連接字串。 如需詳細資訊，請參閱[如何：建置 Entitycollection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)。  
  
## <a name="creating-queries"></a>建立查詢  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)]語言是與儲存體無關的 SQL dialect，可直接配合概念實體結構描述運作，並支援 Entity Data Model 概念，例如繼承和關聯性。 <xref:System.Data.EntityClient.EntityCommand>類別用來執行[!INCLUDE[esql](../../../../../includes/esql-md.md)]命令針對實體模型。 建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢文字。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會與儲存區特定的資料提供者一起運作，將泛型 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 轉譯成儲存區特定的查詢。 如需有關撰寫[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢，請參閱[Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)。  
  
 下列範例會建立<xref:System.Data.EntityClient.EntityCommand>物件，並指派[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢文字，以其<xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>屬性。 這[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢要求排序依據標價，從概念模型的產品。 下列程式碼完全不了解儲存模型的相關資訊。  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>執行查詢  
 執行查詢時，會先剖析查詢然後將它轉換成標準命令樹。 所有後續的查詢處理都是在此命令樹上執行。 命令樹是之間的通訊方式<xref:System.Data.EntityClient>和 基礎.NET Framework 資料提供者，例如<xref:System.Data.SqlClient>。  
  
 <xref:System.Data.EntityClient.EntityDataReader> 會公開針對概念模型執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。 若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。 <xref:System.Data.EntityClient.EntityDataReader> 會實作 <xref:System.Data.IExtendedDataRecord> 來描述豐富的結構化結果。  
  
## <a name="managing-transactions"></a>異動管理  
 Entity Framework 中有兩種使用異動的方式：自動與明確。 自動交易會使用 <xref:System.Transactions> 命名空間，而明確交易會使用 <xref:System.Data.EntityClient.EntityTransaction> 類別。  
  
 若要更新透過概念模型公開的資料，請參閱[How to:管理交易，在 Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100))。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建置 Entitycollection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [如何：執行可傳回 PrimitiveType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [如何：執行可傳回 RefType 結果的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [如何：執行可傳回複雜類型的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [如何：執行可傳回巢狀的集合的查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [如何：使用 EntityCommand Entity SQL 查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [如何：執行參數化的預存程序，以使用 EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [如何：執行多型查詢](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [如何：使用巡覽關聯性巡覽運算子](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>另請參閱

- [管理連接和異動](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [語言參考](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
