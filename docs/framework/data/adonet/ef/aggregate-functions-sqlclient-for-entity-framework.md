---
title: 彙總函式 (適用於 Entity Framework 的 SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700049"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>彙總函式 (適用於 Entity Framework 的 SqlClient)
.NET Framework Data Provider for SQL Server (SqlClient) 有提供彙總函式。 彙總函式會對一組輸入值執行計算，並傳回值。 這些函式位於您使用 SqlClient 時可以使用的 SqlServer 命名空間 (Namespace) 內。 提供者命名空間屬性可以讓 Entity Framework 了解此提供者對特定建構 (例如型別和函式) 所使用的前置詞。  
  
 以下是 SqlClient 彙總函式。  

## <a name="avgexpression"></a>AVG （expression）

傳回集合中各個值的平均值。 會忽略 Null 值。

**引數**

@No__t-0、`Int64`、`Double` 和 `Decimal`。

**傳回值**

`expression` 的類型。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG （集合）
 
 傳回集合中值的總和檢查碼 (Checksum)。 會忽略 Null 值。
 
 **引數**
 
 集合（`Int32`）。
 
 **傳回值**
 
 `Int32`。
 
 **範例**
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>計數（運算式）

以 `Int32` 形式傳回集合中的項目數。

**引數**

集合 @ no__t-0T >，其中 T 是下列其中一種類型：

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` （SQL Server 2000 中未傳回）|

**傳回值**

`Int32`。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a>COUNT_BIG （運算式）
 
以 `bigint` 形式傳回集合中的項目數。
 
 **引數**
 
 集合（T），其中 T 是下列其中一種類型：
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` （SQL Server 2000 中未傳回）|

**傳回值**

`Int64`。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>最大值（運算式）

傳回集合中的最大值。

**引數**

集合（T），其中 T 是下列其中一種類型： 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**傳回值**

`expression` 的類型。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>最小值（運算式）

傳回集合中的最小值。

**引數**

集合（T），其中 T 是下列其中一種類型： 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**傳回值**

`expression` 的類型。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV （運算式）

傳回指定運算式中之所有值的統計標準差。

**引數**

集合（`Double`）。

**傳回值**

`Double`。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP （運算式）

傳回指定運算式中所有值的母體擴展統計標準差。

**引數**

集合（`Double`）。

**傳回值**

`Double`。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM （expression）

傳回集合中所有值的總和。

**引數**

集合（T），其中 T 是下列其中一個類型： `Int32`，`Int64`，`Double`，`Decimal`。

**傳回值**

`expression` 的類型。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR （expression）

傳回指定運算式中之所有值的統計變異數。

**引數**

集合（`Double`）。

**傳回值**

`Double`。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP （運算式）

傳回指定之運算式中所有值的母體擴展統計變異數。

**引數**

集合（`Double`）。

**傳回值**

`Double`。

**範例**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>另請參閱

- [彙總函式 (transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Entity SQL 語言](./language-reference/entity-sql-language.md)
- [彙總標準函式](./language-reference/aggregate-canonical-functions.md)
