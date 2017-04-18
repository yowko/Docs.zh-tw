---
title: "HOW TO：定義連接字串 | Microsoft Docs"
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
  - "ESQL"
  - "jsharp"
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HOW TO：定義連接字串
本主題將示範如何定義連接至概念模型時所使用的連接字串 \(Connection String\)。  本主題是根據 [AdventureWorks Sales](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832) 概念模型。  AdventureWorks Sales Model 會在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 文件的所有工作相關的主題內使用。  本主題會假設您已經設定 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 並且定義 AdventureWorks Sales Model。  如需詳細資訊，請參閱[How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/zh-tw/d4fd6864-f2a1-48f0-aa32-1e318775a99a)。  本主題中的程序也包含在 [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/zh-tw/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)中。  
  
> [!NOTE]
>  如果在 [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 專案中使用 [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] 精靈，精靈會自動產生 .edmx 檔案，並設定專案使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。  如需詳細資訊，請參閱[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/zh-tw/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
### 定義 Entity Framework 連接字串  
  
-   開啟專案的應用程式組態檔 \(app.config\) 並加入下列連接字串：  
  
  
  
     如果您的專案沒有應用程式組態檔，可以從 \[**專案**\] 功能表中選取 \[**加入新項目**\]、選取 \[**一般**\] 類別、選取 \[**應用程式組態檔**\]，然後按一下 \[**加入**\]，藉以加入應用程式組態檔。  
  
## 請參閱  
 [Quickstart](http://msdn.microsoft.com/zh-tw/0bc534be-789f-4819-b9f6-76e51d961675)   
 [How to: Create a New .edmx File](http://msdn.microsoft.com/zh-tw/beb8189e-e51c-4051-839c-9902c224abf2)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/zh-tw/91076853-0881-421b-837a-f582f36be527)