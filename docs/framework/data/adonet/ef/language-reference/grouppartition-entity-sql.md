---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)
傳回引數值的集合，該集合會將目前的群組分割投影至其相關的彙總。 `GroupPartition` 彙總是以群組為基礎的彙總，不具有以集合為基礎的形式。  
  
## <a name="syntax"></a>語法  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。  
  
## <a name="remarks"></a>備註  
 下列查詢會產生產品清單，以及每項產品的訂單產品線數量集合：  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 以下兩個查詢的語意相同：  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 `GROUPPARTITION` 運算子可以搭配使用者定義的彙總函式使用。  
  
 `GROUPPARTITION` 是特殊的彙總運算子，可保留群組輸入集的參考。 若 GROUP BY 在範圍內，即可在查詢中任何位置使用此參考。 例如：  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 搭配標準 GROUP BY，會隱藏群組的結果。 您只能在彙總函式中使用結果。 若要查看群組的結果，您必須使用子查詢，讓群組和輸入集互相關聯。 下列兩個查詢的用法相同：  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 如範例所示，GROUPPARTITION 彙總運算子可讓您更容易在群組之後參考輸入集。  
  
 當您使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 參數時，GROUPPARTITION 運算子可以指定運算子輸入中的任何 `expression` 運算式。  
  
 下列針對群組分割的所有輸入運算式在執行個體中皆有效：  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 GROUPPARTITION 子句搭配 GROUP BY 子句。 GROUP BY 子句會依 `SalesOrderHeader` 將 `Contact`實體進行分組。 GROUPPARTITION 子句接著會投影每個群組的 `TotalDue` 屬性，以產生十進位集合。  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
