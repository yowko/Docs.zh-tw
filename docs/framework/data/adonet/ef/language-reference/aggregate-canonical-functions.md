---
title: "彙總標準函式 | Microsoft Docs"
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
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 彙總標準函式
彙總 \(Aggregate\) 是指將一連串輸入值縮減成單一值的運算式。  彙總通常會與 SELECT 運算式的 GROUP BY 子句搭配使用，而且它們的使用位置具有一些條件約束 \(Constraint\)。  
  
 下表所示為彙總 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
|函式|描述|  
|--------|--------|  
|`Avg(` `expression` `)`|傳回非 null 值的平均。<br /><br /> **引數**<br /><br /> `Int32`、 `Int64`、`Double` 和 `Decimal`。<br /><br /> **傳回值**<br /><br /> `expression` 的類型。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
 [!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]|  
|`BigCount(` `expression` `)`|傳回包含 null 和重複值的彙總大小。<br /><br /> **引數**<br /><br /> 任何型別。<br /><br /> **傳回值**<br /><br /> `Int64`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
 [!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]|  
|`Count(` `expression` `)`|傳回包含 null 和重複值的彙總大小。<br /><br /> **引數**<br /><br /> 任何型別。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
 [!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]|  
|`Max(` `expression` `)`|傳回非 null 值的最大值。<br /><br /> **引數**<br /><br /> `Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。<br /><br /> **傳回值**<br /><br /> `expression` 的類型。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
 [!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]|  
|`Min(` `expression` `)`|傳回非 null 值的最小值。<br /><br /> **引數**<br /><br /> `Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。<br /><br /> **傳回值**<br /><br /> `expression` 的類型。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
 [!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]|  
|`StDev(` `expression` `)`|傳回非 Null 值的標準差。<br /><br /> **引數**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **傳回值**<br /><br /> `Double`。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
 [!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]|  
|`StDevP(` `expression` `)`|傳回所有值的母體擴展標準差。<br /><br /> **引數**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **傳回值**<br /><br /> `Double`。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
 [!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]|  
|`Sum(` `expression` `)`|傳回非 null 值的總和。<br /><br /> **引數**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **傳回值**<br /><br /> `Double`。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
 [!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]|  
|`Var(` `expression` `)`|傳回所有非 NULL 值的變異數。<br /><br /> **引數**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **傳回值**<br /><br /> `Double`。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
 [!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]|  
|`VarP(` `expression` `)`|傳回所有非 NULL 值的母體變異數。<br /><br /> **引數**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **傳回值**<br /><br /> `Double`。  如果所有輸入值是 `null` 值，則為 `Null`。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
 [!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]|  
  
 Microsoft SQL Client Managed Provider 中提供了對等的功能。  如需詳細資訊，請參閱[Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## 以集合為基礎的彙總  
 以集合為基礎的彙總 \(集合函式\) 會針對集合運作並傳回一個值。  例如，如果 ORDERS 是所有訂單的集合，您就可以使用下列運算式來計算最早出貨日期：  
  
```  
min(select value o.ShipDate from LOB.Orders as o)  
```  
  
 以集合為基礎之彙總內部的運算式是在目前的環境名稱解析範圍內評估。  
  
## 以群組為基礎的彙總  
 以群組為基礎的彙總會計算 GROUP BY 子句所定義的整個群組。  系統會針對結果中的每個群組，使用每個群組中的項目當做彙總計算的輸入來計算個別的彙總。  當 group\-by 子句用於 select 運算式時，只有群組運算式名稱、彙總或常數運算式可以出現在投影或 order\-by 子句中。  
  
 下列範例會計算針對每個產品訂購的平均數量：  
  
```  
select p, avg(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 您可以在 SELECT 運算式中使用以群組為基礎的彙總，但不使用明確的 group\-by 子句。  在此情況下，所有元素都會被視為單一群組。  這就相當於根據常數指定群組的情況。  以下列運算式為例：  
  
```  
select avg(ol.Quantity) from LOB.OrderLines as ol  
```  
  
 這個運算式就相當於下列運算式：  
  
```  
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1  
```  
  
 以群組為基礎之彙總內部的運算式是在 WHERE 子句運算式可見的名稱解析範圍內評估。  
  
 如同在 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 中，以群組為基礎的彙總也可以指定 ALL 或 DISTINCT 修飾詞 \(Modifier\)。  如果有指定 DISTINCT 修飾詞，系統就會在計算彙總之前，從彙總輸入集合中刪除重複項目。  如果指定的是 ALL 修飾詞 \(或沒有指定任何修飾詞\)，就不會執行重複項目刪除作業。  
  
## 請參閱  
 [標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)