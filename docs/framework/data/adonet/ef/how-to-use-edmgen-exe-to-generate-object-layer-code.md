---
title: "HOW TO：使用 EdmGen.exe 產生物件層程式碼 | Microsoft Docs"
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
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# HOW TO：使用 EdmGen.exe 產生物件層程式碼
本主題示範如何使用 [EDM 產生器 \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) 工具依據 .csdl 檔產生物件層程式碼。  
  
### 使用 EdmGen.exe 針對 Visual Basic 專案產生 School 模型的物件層程式碼  
  
1.  建立 School 資料庫。  如需詳細資訊，請參閱[Creating the School Sample Database](http://msdn.microsoft.com/zh-tw/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  產生 School 模型或取得 School.csdl 檔案。  如需詳細資訊，請參閱[HOW TO：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
3.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### 使用 EdmGen.exe 針對 C\# 專案產生 School 模型的物件層程式碼  
  
1.  建立 School 資料庫。  如需詳細資訊，請參閱[Creating the School Sample Database](http://msdn.microsoft.com/zh-tw/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)。  
  
2.  產生 School 模型或取得 School.csdl 檔案。  如需詳細資訊，請參閱[HOW TO：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。  
  
3.  在命令提示字元中，執行下列命令但不含分行符號：  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## 請參閱  
 [模型化及對應檔案](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)   
 [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/zh-tw/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/zh-tw/91076853-0881-421b-837a-f582f36be527)   
 [How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/zh-tw/b18a9d16-e10b-4043-ba91-b632f85a2579)   
 [HOW TO：使用 EdmGen.exe 產生模型和對應檔](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)