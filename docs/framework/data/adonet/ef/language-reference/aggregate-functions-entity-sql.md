---
title: "彙總函式 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 彙總函式 (Entity SQL)
彙總是語言建構，可將集合壓縮至純量，做為群組作業的一部份。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 彙總以兩種形式出現：  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集合函式可用於運算式內的任何地方，包括於投影和述詞中 \(在集合上作用\) 使用彙總函式。集合函式是在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中指定彙總的慣用模式。  
  
-   查詢運算式中的群組彙總有 GROUP BY 子句。  與 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 相同，群組彙總接受 DISTINCT 和 ALL 做為彙總輸入的修飾詞。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會先嘗試將運算式解譯為集合函式，如果運算式位於 SELECT 運算式的內容中，則會解譯為群組彙總。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 可定義特殊彙總運算子，名為 [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)。  這個運算子可讓您取得群組輸入集的參考。  如此可允許更多進階的分組查詢，其中的 GROUP BY 子句結果可用於不是群組彙總或集合函式的地方。  
  
## 集合函式  
 集合函式會針對集合運作，並傳回一個純量值。  例如，如果 `orders` 是所有 `orders` 的集合，您就可以使用下列運算式，計算最早出貨日期：  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## 群組彙總  
 群組彙總會計算 GROUP BY 子句所定義的群組結果。  GROUP BY 子句會將資料分割成數個群組。  系統會針對結果中的每個群組套用彙總函式，並使用每個群組中的項目做為彙總計算的輸入，計算個別彙總。  當 GROUP BY 子句用於 SELECT 運算式時，只有群組運算式名稱、彙總或常數運算式可以出現在投影、HAVING 或 ORDER BY 子句中。  
  
 下列範例會計算針對每個產品訂購的平均數量。  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 您可以在 SELECT 運算式中使用群組彙總，但不使用明確的 GROUP BY 子句。  所有項目都會被視為單一群組，這就相當於根據常數指定群組的情況。  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 GROUP BY 子句中使用的運算式會使用 WHERE 子句運算式中可見的相同名稱解析範圍，進行評估。  
  
## 請參閱  
 [函式](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)