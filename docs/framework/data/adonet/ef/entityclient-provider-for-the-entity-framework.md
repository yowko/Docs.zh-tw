---
title: Entity Framework 的 EntityClient 提供者
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: e3a87d4a936e5bdf633e1f997f66dd98add2a9cb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854706"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework 的 EntityClient 提供者
EntityClient 提供者是 Entity Framework 應用程式用來存取概念模型中所描述之資料的資料提供者。 如需概念模型的詳細資訊，請參閱[模型化和對應](modeling-and-mapping.md)。 EntityClient 會使用其他 .NET Framework 資料提供者來存取資料來源。 例如，EntityClient 會在存取 SQL Server 資料庫時使用 .NET Framework Data Provider for SQL Server (SqlClient)。 如需有關 SqlClient 提供者的詳細資訊，請參閱[適用于 Entity Framework 的 SqlClient](sqlclient-for-the-entity-framework.md)。 EntityClient 提供者是在 <xref:System.Data.EntityClient> 命名空間 (Namespace) 中實作的。  
  
## <a name="managing-connections"></a>管理連接  
 Entity Framework 會藉由提供<xref:System.Data.EntityClient.EntityConnection>給基礎資料提供者和關係資料庫，以在儲存體專屬的 ADO.NET 資料提供者之上建立。 若要建立<xref:System.Data.EntityClient.EntityConnection>物件，您必須參考一組中繼資料，其中包含必要的模型和對應，以及儲存體特定的資料提供者名稱和連接字串。 <xref:System.Data.EntityClient.EntityConnection>準備就緒之後，即可透過概念模型產生的類別來存取實體。  
  
 您可以在 app.config 檔案中指定連接字串。  
  
 <xref:System.Data.EntityClient> 也包含 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 類別。 這個類別可讓開發人員使用此類別的屬性和方法，以程式設計方式建立語法正確的連接字串，以及剖析和重建現有的連接字串。 如需詳細資訊，請參閱[如何：建立 EntityConnection 連接字串](how-to-build-an-entityconnection-connection-string.md)。  
  
## <a name="creating-queries"></a>建立查詢  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)]語言是與儲存體無關的 SQL 方言，可直接與概念實體架構搭配運作，並且支援繼承和關聯性等實體資料模型概念。 類別是用來針對實體模型[!INCLUDE[esql](../../../../../includes/esql-md.md)]執行命令。 <xref:System.Data.EntityClient.EntityCommand> 建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢文字。 此 Entity Framework 可與儲存體特定的資料提供者搭配使用[!INCLUDE[esql](../../../../../includes/esql-md.md)] ，以將泛型轉譯成特定儲存體的查詢。 如需撰寫[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢的詳細資訊，請參閱[Entity SQL 語言](./language-reference/entity-sql-language.md)。  
  
 下列範例會建立<xref:System.Data.EntityClient.EntityCommand>物件，並將[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢文字指派給其<xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>屬性。 此[!INCLUDE[esql](../../../../../includes/esql-md.md)]查詢會要求從概念模型依標價排序的產品。 下列程式碼完全不了解儲存模型的相關資訊。  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>執行查詢  
 執行查詢時，會先剖析查詢然後將它轉換成標準命令樹。 所有後續的查詢處理都是在此命令樹上執行。 命令樹是<xref:System.Data.EntityClient>和基礎 .NET Framework Data Provider （ <xref:System.Data.SqlClient>例如）之間的通訊方式。  
  
 <xref:System.Data.EntityClient.EntityDataReader> 會公開針對概念模型執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。 若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。 <xref:System.Data.EntityClient.EntityDataReader> 會實作 <xref:System.Data.IExtendedDataRecord> 來描述豐富的結構化結果。  
  
## <a name="managing-transactions"></a>異動管理  
 Entity Framework 中有兩種使用異動的方式：自動與明確。 自動交易會使用 <xref:System.Transactions> 命名空間，而明確交易會使用 <xref:System.Data.EntityClient.EntityTransaction> 類別。  
  
 若要更新透過概念模型公開的資料，請參閱[如何：管理 Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100))中的交易。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立 EntityConnection 連接字串](how-to-build-an-entityconnection-connection-string.md)  
  
 [如何：執行可傳回 PrimitiveType 結果的查詢](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [如何：執行可傳回 StructuralType 結果的查詢](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [如何：執行可傳回 RefType 結果的查詢](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [如何：執行可傳回複雜類型的查詢](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [如何：執行傳回嵌套集合的查詢](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [如何：使用 EntityCommand 執行參數化 Entity SQL 查詢](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [如何：使用 EntityCommand 執行參數化預存程式](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [如何：執行多型查詢](how-to-execute-a-polymorphic-query.md)  
  
 [如何：使用導覽運算子導覽關聯性](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>另請參閱

- [管理連接和交易](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](index.md)
- [語言參考](./language-reference/index.md)
