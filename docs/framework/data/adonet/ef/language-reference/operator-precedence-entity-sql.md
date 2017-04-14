---
title: "運算子優先順序 (Entity SQL) | Microsoft Docs"
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
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 運算子優先順序 (Entity SQL)
當 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢有多個運算子時，運算子優先順序會決定作業的執行順序。  執行的順序對於查詢結果有很大的影響。  
  
 下表顯示運算子的優先順序層級。  先評估層級較高的運算子，再評估層級較低的運算子。  
  
|層級|運算類型|運算子|  
|--------|----------|---------|  
|1|主要|`. , [] ()`|  
|2|一元|`! not`|  
|3|乘法類 \(Multiplicative\)|`* / %`|  
|4|加法類 \(Additive\)|`+ -`|  
|5|排序|`< > <= >=`|  
|6|相等|`= != <>`|  
|7|條件式 AND|`and &&`|  
|8|條件式 OR|`or &#124;&#124;`|  
  
 當運算式中的兩個運算子有相同的運算子優先順序層級時，會依據它們在查詢中的位置，由左至右來評估它們。  例如， `x+y-z`  會判斷值為  `(x+y)-z`。  
  
 您可以使用括號來覆寫查詢中已定義的運算子優先順序。  括號內的所有內容都會先評估得出單一結果，之後，括號外的任何運算子便可以使用這個結果。  例如， `x+y*z` 會將 `y` 乘以 `z` ，然後加上 `x`，但是 `(x+y)*z` 會將 `x` 與 `y` 相加，然後將結果乘以 `z`。  
  
## 請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)