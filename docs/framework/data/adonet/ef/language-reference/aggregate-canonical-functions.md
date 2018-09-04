---
title: 彙總標準函式
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: e4772176130fc72a22645462921c90dd5b7967b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506634"
---
# <a name="aggregate-canonical-functions"></a>彙總標準函式

彙總 (Aggregate) 是指將一連串輸入值縮減成單一值的運算式。 彙總通常會與 SELECT 運算式的 GROUP BY 子句搭配使用，而且它們的使用位置具有一些條件約束 (Constraint)。

## <a name="aggegate-entity-sql-canonical-functions"></a>Aggegate Entity SQL 標準函式

以下是彙總的 Entity SQL 標準函式。

### <a name="avgexpression"></a>Avg(expression)

傳回非 null 值的平均。

**引數**

`Int32`， `Int64`， `Double`，和`Decimal`。

**傳回值**

型別`expression`，或`null`如果所有輸入的值為`null`值。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] 
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a>BigCount(expression)

傳回包含 null 和重複值的彙總大小。

**引數**

任何型別。

**傳回值**

`Int64`。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] 
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a>Count(expression) 

傳回包含 null 和重複值的彙總大小。

**引數**

任何型別。

**傳回值**

`Int32`。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a>Max(expression)

傳回非 null 值的最大值。

**引數**

`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。

**傳回值**

型別`expression`，或`null`如果所有輸入的值為`null`值。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a>Min(expression)

傳回非 null 值的最小值。

**引數**

`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。

**傳回值**

型別`expression`，或`null`如果所有輸入的值為`null`值。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a>StDev(expression)

傳回非 Null 值的標準差。

**引數**

`Int32`、`Int64`、`Double`、`Decimal`。

**傳回值**

`Double`。 如果所有輸入值是 `Null` 值，則為 `null`。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a>StDevP(expression)

傳回所有值的母體擴展標準差。

**引數**

`Int32`、`Int64`、`Double`、`Decimal`。

**傳回值**

A `Double`，或`null`如果所有輸入的值為`null`值。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a>Sum(expression)

傳回非 null 值的總和。

**引數**

`Int32`、`Int64`、`Double`、`Decimal`。

**傳回值**

A `Double`，或`null`如果所有輸入的值為`null`值。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a>Var(expression)

傳回所有非 NULL 值的變異數。

**引數**

`Int32`、`Int64`、`Double`、`Decimal`。

**傳回值**

A `Double`，或`null`如果所有輸入的值為`null`值。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a>VarP(expression)

傳回所有非 NULL 值的母體變異數。

**引數**

`Int32`、`Int64`、`Double`、`Decimal`。

**傳回值**

A `Double`，或`null`如果所有輸入的值為`null`值。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] 

Microsoft SQL Client Managed Provider 中提供了對等的功能。 如需詳細資訊，請參閱 <<c0> [ 適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。

## <a name="collection-based-aggregates"></a>以集合為基礎的彙總

以集合為基礎的彙總 (集合函式) 會針對集合運作並傳回一個值。 比方說如果 ORDERS 是所有訂單的集合，您可以計算最早的出貨日期，使用下列運算式：

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

以集合為基礎之彙總內部的運算式是在目前的環境名稱解析範圍內評估。

## <a name="group-based-aggregates"></a>群組為基礎的彙總

以群組為基礎的彙總會計算 GROUP BY 子句所定義的整個群組。 系統會針對結果中的每個群組，使用每個群組中的項目當做彙總計算的輸入來計算個別的彙總。 當 group-by 子句用於 select 運算式時，只有群組運算式名稱、彙總或常數運算式可以出現在投影或 order-by 子句中。

下列範例會計算針對每個產品訂購的平均數量：

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

可以在 SELECT 運算式中以群組為基礎的彙總，而不需要明確 group-by 子句。 在此情況下，所有項目會視為單一群組。 這是指定群組，根據常數的對等項目。 以下列運算式為例：

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

這個運算式就相當於下列運算式：

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

以群組為基礎之彙總內部的運算式是在 WHERE 子句運算式可見的名稱解析範圍內評估。

依照[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]，群組為基礎的彙總也可以指定 ALL 或 DISTINCT 修飾詞。 如果有指定 DISTINCT 修飾詞，系統就會在計算彙總之前，從彙總輸入集合中刪除重複項目。 如果指定的是 ALL 修飾詞 (或沒有指定任何修飾詞)，就不會執行重複項目刪除作業。  

## <a name="see-also"></a>另請參閱

[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
