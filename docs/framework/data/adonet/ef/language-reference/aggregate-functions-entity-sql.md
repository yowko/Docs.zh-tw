---
title: 彙總函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: c79071e73763b56c0dde906499f3eef1d296ce0c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251341"
---
# <a name="aggregate-functions-entity-sql"></a>彙總函式 (Entity SQL)
彙總是語言建構，可將集合壓縮至純量，做為群組作業的一部份。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 彙總以兩種形式出現：  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)]可以在運算式中的任何位置使用的集合函數。 包括於投影和述詞中 (在集合上作用) 使用彙總函式。 集合函式是在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中指定彙總的慣用模式。  
  
- 查詢運算式中的群組彙總有 GROUP BY 子句。 如同在 Transact-sql 中, 群組匯總會接受 DISTINCT 和 ALL 做為匯總輸入的修飾詞。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]會先嘗試將運算式解讀為集合函式, 而且如果運算式位於 SELECT 運算式的內容中, 它會將它解讀為群組匯總。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]定義名為[GROUPPARTITION](grouppartition-entity-sql.md)的特殊匯總運算子。 這個運算子可讓您取得群組輸入集的參考。 如此可允許更多進階的分組查詢，其中的 GROUP BY 子句結果可用於不是群組彙總或集合函式的地方。  
  
## <a name="collection-functions"></a>集合函式  
 集合函式會針對集合運作，並傳回一個純量值。 例如，如果 `orders` 是所有 `orders` 的集合，您就可以使用下列運算式，計算最早出貨日期：  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>群組彙總  
 群組彙總會計算 GROUP BY 子句所定義的群組結果。 GROUP BY 子句會將資料分割成數個群組。 系統會針對結果中的每個群組套用彙總函式，並使用每個群組中的項目做為彙總計算的輸入，計算個別彙總。 當 GROUP BY 子句用於 SELECT 運算式時，只有群組運算式名稱、彙總或常數運算式可以出現在投影、HAVING 或 ORDER BY 子句中。  
  
 下列範例會計算針對每個產品訂購的平均數量。  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 您可以在 SELECT 運算式中使用群組彙總，但不使用明確的 GROUP BY 子句。 所有項目都會被視為單一群組，這就相當於根據常數指定群組的情況。  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 GROUP BY 子句中使用的運算式會使用 WHERE 子句運算式中可見的相同名稱解析範圍，進行評估。  
  
## <a name="see-also"></a>另請參閱

- [函式](functions-entity-sql.md)
