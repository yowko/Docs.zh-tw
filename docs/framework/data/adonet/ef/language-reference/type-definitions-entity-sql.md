---
title: "類型定義 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 類型定義 (Entity SQL)
型別定義用於 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 內嵌函式中的宣告陳述式。  
  
## 備註  
 內嵌函式的宣告陳述式包括後面接表示函式名稱之識別項 \(例如 "MyAvg"\) 的 [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) 關鍵字，後面再接以括號括住的參數定義清單 \(例如 "dues Collection\(Decimal\)"\)。  
  
 參數定義清單包括零或多個參數定義。  每個參數定義包括一個識別項 \(函式參數的名稱，例如 "dues"\)，後面接型別定義 \(例如 "Collection\(Decimal\)"\)。  
  
 型別定義可以是下面其中一項：  
  
-   識別項的型別 \(例如 "Int32" 或 "AdventureWorks.Order"\)。  
  
-   關鍵字 `COLLECTION` 後面接以括號括住的其他型別定義 \(例如 "Collection\(AdventureWorks.Order\)"\)。  
  
-   關鍵字 ROW 後面接以括號括住的屬性定義清單 \(例如 "Row\(x AdventureWorks.Order\)"\)。  屬性定義的格式如 "`identifier type_definition`, `identifier type_definition`, ..."。  
  
-   關鍵字 REF 後面接以括號括住的識別項型別 \(例如 "Ref\(AdventureWorks.Order\)"\)。  REF 型別定義運算子需要實體類型做為引數。  您不能指定基本型別做為引數。  
  
 您也可以巢狀化型別定義 \(例如 "Collection\(Row\(x Ref\(AdventureWorks.Order\)\)\)"\)。  
  
 型別定義的選項是：  
  
-   `IdentifierName supported_type` 或  
  
-   `IdentifierName` COLLECTION\(`type_definition`\)，或  
  
-   `IdentifierName` ROW\(`property_definition`\)，或  
  
-   `IdentifierName` REF\(`supported_entity_type`\)  
  
 屬性定義的選項是 `IdentifierName type_definition`。  
  
 支援的型別是目前命名空間中的任何型別。  這些包括基本型別和實體類型兩者。  
  
 支援的實體類型只會參考目前命名空間中的實體類型。  不包括基本型別。  
  
## 範例  
 下面是一個簡單的型別定義範例：  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 下面是一個 COLLECTION 型別定義的範例：  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 下面是一個 ROW 型別定義的範例：  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 下面是一個 REF 型別定義的範例。  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## 請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)   
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)