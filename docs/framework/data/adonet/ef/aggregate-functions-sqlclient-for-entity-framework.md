---
title: "彙總函式 (適用於 Entity Framework 的 SqlClient)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 804acd77887c1cf05caa2004e75ef01110909490
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>彙總函式 (適用於 Entity Framework 的 SqlClient)
.NET Framework Data Provider for SQL Server (SqlClient) 有提供彙總函式。 彙總函式會對一組輸入值執行計算，並傳回值。 這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。 提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。  
  
 下表顯示 SqlClient 彙總函式。  
  
|函式|描述|  
|--------------|-----------------|  
|`AVG(` `expression` `)`|傳回集合中各個值的平均值。<br /><br /> 會忽略 Null 值。<br /><br /> **引數**<br /><br /> `Int32`， `Int64`， `Double`，和`Decimal`。<br /><br /> **傳回值**<br /><br /> `expression` 的類型。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]|  
|`CHECKSUM_AGG(` `collection` `)`|傳回集合中值的總和檢查碼 (Checksum)。<br /><br /> 會忽略 Null 值。<br /><br /> **引數**<br /><br /> 集合 (`Int32`)。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]|  
|`COUNT(` `expression` `)`|以 `Int32` 形式傳回集合中的項目數。<br /><br /> **引數**<br /><br /> 集合 (T)，其中的 T 為下列其中一個型別：<br /><br /> `Guid` (在 SQL Server 2000 中不會傳回)、<br /><br /> `Boolean`、`Double`、`DateTime`、`DateTimeOffset`、`Time`、`String` 或 `Binary`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]|  
|`COUNT_BIG(` `expression` `)`|以 `bigint` 形式傳回集合中的項目數。<br /><br /> **引數**<br /><br /> 集合 (T)，其中的 T 為下列其中一個型別：<br /><br /> `Guid` (在 SQL Server 2000 中不會傳回)、`Boolean`、`Double`、`DateTime`、`DateTimeOffset`、`Time`、`String` 或 `Binary`。<br /><br /> **傳回值**<br /><br /> `Int64`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]|  
|`MAX(` `expression` `)`|傳回集合中的最大值。<br /><br /> **引數**<br /><br /> 集合 (T)，其中 T 為下列其中一個型別：`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。<br /><br /> **傳回值**<br /><br /> `expression` 的類型。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]|  
|`MIN(` `expression` `)`|傳回集合中的最小值。<br /><br /> **引數**<br /><br /> 集合 (T)，其中 T 為下列其中一個型別：`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、<br /><br /> `Binary`.<br /><br /> **傳回值**<br /><br /> `expression` 的類型。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]|  
|`STDEV(` `expression` `)`|傳回指定運算式中之所有值的統計標準差。<br /><br /> **引數**<br /><br /> 集合 (`Double`)。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]|  
|`STDEVP(` `expression` `)`|傳回指定運算式中所有值的母體擴展統計標準差。<br /><br /> **引數**<br /><br /> 集合 (`Double`)。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]|  
|`SUM(` `expression` `)`|傳回集合中所有值的總和。<br /><br /> **引數**<br /><br /> 集合 (T)，其中 T 為下列其中一個型別：`Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **傳回值**<br /><br /> `expression` 的類型。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]|  
|`VAR(` `expression` `)`|傳回指定運算式中之所有值的統計變異數。<br /><br /> **引數**<br /><br /> 集合 (`Double`)。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]|  
|`VARP(` `expression` `)`|傳回指定之運算式中所有值的母體擴展統計變異數。<br /><br /> **引數**<br /><br /> 集合 (`Double`)。<br /><br /> **傳回值**<br /><br /> `Double`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]|  
  
 如需 SqlClient 所支援彙總函式的詳細資訊，請參閱 SqlClient 提供者資訊清單中所指定 SQL Server 版本的說明文件：  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[彙總函式 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115906)|[彙總函式 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkID=115903)|[彙總函式 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115907)|  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [彙總標準函式](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
