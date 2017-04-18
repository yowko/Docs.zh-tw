---
title: "撰寫 Entity Framework 資料提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 撰寫 Entity Framework 資料提供者
本節討論如何編寫 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 提供者，以支援 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 以外的資料來源。[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 包括支援 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 的提供者。  
  
## Entity Framework 提供者模型簡介  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 與資料庫無關，而且您可以使用 ADO.NET 提供者模型來撰寫提供者，以便連接到各種不同的資料來源。  
  
 Entity Framework 資料提供者 \(使用 ADO.NET 資料提供者模型所建置\) 會執行下列功能：  
  
-   將實體資料模型 \(EDM\) 基本型別對應到提供者類型。  
  
-   公開提供者特有的函式。  
  
-   為給定的 DbQueryCommandTree 產生提供者特有的命令來支援 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 查詢。  
  
-   為給定的 DbModificationCommandTree 產生提供者特有的更新命令，以支援透過 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的更新。  
  
-   公開存放結構定義的對應檔案，以便支援根據資料庫產生模型。  
  
-   透過概念模型公開中繼資料 \(如資料表和檢視表\)。  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c\-0ac0\-4911\-86be\-0460a78760ba")  
  
## 範例  
 如需可支援 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 以外之資料來源的 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 提供者範例，請參閱 [Entity Framework 範例提供者](http://go.microsoft.com/fwlink/?LinkId=180616)。  
  
## 本章節內容  
 [SQL 產生](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [修改 SQL 產生](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [提供者資訊清單規格](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## 請參閱  
 [使用資料提供者](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)