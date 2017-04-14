---
title: "參數 (Entity SQL) | Microsoft Docs"
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
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 參數 (Entity SQL)
參數是定義在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 外部的變數，通常是透過主應用程式語言使用的繫結 API 來定義。  每一個參數都有一個名稱和型別，  參數名稱會在查詢運算式內定義，使用 At \(@\) 符號作為前置詞，如此可避免與屬性名稱或在查詢內定義的其他名稱混淆。  
  
 主應用程式語言的繫結 API 會提供用來繫結參數的 API。  
  
## 範例  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)