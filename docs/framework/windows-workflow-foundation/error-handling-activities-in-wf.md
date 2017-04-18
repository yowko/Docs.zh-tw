---
title: "WF 中的錯誤處理活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# WF 中的錯誤處理活動
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 提供數種系統提供的活動，可用於實作錯誤處理與復原。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][例外狀況](../../../docs/framework/windows-workflow-foundation//exceptions.md)。  
  
## 錯誤處理活動  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|重新擲回從 `TryCatch` 活動中上次擲回的例外狀況。|  
|<xref:System.Activities.Statements.Throw>|擲回例外狀況。|  
|<xref:System.Activities.Statements.TryCatch>|實作例外狀況處理。|