---
title: "Entity SQL 語言 | Microsoft Docs"
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
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Entity SQL 語言
Entity SQL 是與儲存體無關的查詢語言，與 SQL 類似。  Entity SQL 可讓您查詢實體資料 \(無論以物件形式或在表格式資料表中\)。  在下列情況下，您可以考慮使用 Entity SQL：  
  
-   必須在執行階段動態建構查詢時。  在此情況下，您也可以考慮使用 <xref:System.Data.Objects.ObjectQuery%601> 的查詢產生器方法，而不在執行階段建構 Entity SQL 查詢字串。  
  
-   當您想要將查詢定義為模型定義的一部分時。  資料模型僅支援 Entity SQL。  如需詳細資訊，請參閱[QueryView Element \(MSL\)](http://msdn.microsoft.com/zh-tw/f0426b34-45cb-4fd7-9777-e0570c5e0e80)。  
  
-   使用 EntityClient 傳回唯讀實體資料，做為使用 <xref:System.Data.EntityClient.EntityDataReader> 的資料列集時。  如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。  
  
-   如果您非常熟悉 SQL 查詢語言，對您來說，Entity SQL 可能最易於使用。  
  
## 搭配 EntityClient 提供者使用 Entity SQL  
 如果您想要搭配 EntityClient 提供者使用 Entity SQL，請參閱下列主題取得詳細資訊：  
  
 [Entity Framework 的 EntityClient 提供者](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [HOW TO：建立 EntityConnection 連接字串](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [HOW TO：執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [HOW TO：執行會傳回 RefType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [HOW TO：執行可傳回複雜類型的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [HOW TO：執行可傳回巢狀集合的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [HOW TO：使用 EntityCommand 執行參數化 Entity SQL 查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [HOW TO：使用 EntityCommand 執行參數化預存程序](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [HOW TO：執行多型查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [HOW TO：使用 Navigate 運算子巡覽關聯性](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## 搭配物件查詢使用 Entity SQL  
 如果您想要搭配物件查詢使用 Entity SQL，請參閱下列主題取得詳細資訊：  
  
 [How to: Execute a Query that Returns Entity Type Objects](http://msdn.microsoft.com/zh-tw/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [How to: Execute a Parameterized Query](http://msdn.microsoft.com/zh-tw/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [How to: Navigate Relationships Using Navigation Properties](http://msdn.microsoft.com/zh-tw/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [How to: Call a User\-Defined Function](http://msdn.microsoft.com/zh-tw/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [How to: Filter Data](http://msdn.microsoft.com/zh-tw/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [How to: Sort Data](http://msdn.microsoft.com/zh-tw/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [How to: Group Data](http://msdn.microsoft.com/zh-tw/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [How to: Aggregate Data](http://msdn.microsoft.com/zh-tw/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [How to: Execute a Query that Returns Anonymous Type Objects](http://msdn.microsoft.com/zh-tw/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [How to: Execute a Query that Returns a Collection of Primitive Types](http://msdn.microsoft.com/zh-tw/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [How to: Query Related Objects in an EntityCollection](http://msdn.microsoft.com/zh-tw/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [How to: Order the Union of Two Queries](http://msdn.microsoft.com/zh-tw/853c583a-eaba-4400-830d-be974e735313)  
  
 [How to: Page Through Query Results](http://msdn.microsoft.com/zh-tw/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## 本章節內容  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## 請參閱  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)   
 [語言參考](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)