---
title: "模型化及對應檔案 | Microsoft Docs"
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
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# 模型化及對應檔案
在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 中，您可以使用應用程式最適合的方式來定義概念模型、儲存體模型，以及兩者間的對應。  [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 中的實體資料模型工具可讓您從資料庫或圖形模型建立 .[edmx 檔](http://msdn.microsoft.com/zh-tw/f4c8e7ce-1db6-417e-9759-15f8b55155d4)，然後在資料庫或模型變更時更新該檔案。  
  
 從 Entity Framework 4.1 開始，您也可以使用 Code First 開發透過程式設計方式建立模型。  Code First 開發有兩種不同的方案。  在這兩種情況下，開發人員透過編碼 .NET Framework 類別定義建立模型，然後選擇性地使用資料註解或 Fluent 應用程式開發介面指定其他對應或組態。  
  
 如需詳細資訊，請參閱[建立與對應概念模型](http://go.microsoft.com/fwlink/?LinkId=235016)。  
  
 您還可以使用 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 隨附的 EDM 產生器。  EdmGen.exe 可從現有的資料來源產生 .csdl、.ssdl 和 .msl 檔。  您也可以手動建立模型和對應內容。  如需詳細資訊，請參閱[EDM 產生器 \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)。