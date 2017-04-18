---
title: "使用者定義函式 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 使用者定義函式 (Entity SQL)
Entity SQL 支援呼叫查詢中的使用者定義函式。  您可以定義這些函式內嵌在查詢之中 \(請參閱 [How to: Call a User\-Defined Function](http://msdn.microsoft.com/zh-tw/ad131b86-8b4e-4747-8605-d4fc64fb9d02)\)，或是做為概念模型的一部分 \(請參閱 [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/zh-tw/0dad7b8b-58f6-4271-b238-f34810d68e5f)\)。  在概念模型中，概念模型函式會在 [Function](http://msdn.microsoft.com/zh-tw/dc3beca7-55cf-4977-8db0-5064cdbab134) 項目的 [DefiningExpression](http://msdn.microsoft.com/zh-tw/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) 項目中定義為 Entity SQL 命令。  
  
 Entity SQL 可讓您定義查詢命令自身中的函式。  [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) 運算子可定義內嵌函式。  您可以在單一命令中定義多個函式，只要函式的簽章是唯一的，這些函式可以有相同的函式名稱。  如需詳細資訊，請參閱[函式多載解析](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)。  
  
## 請參閱  
 [函式](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)