---
title: "Common Language Runtime 中的 ETW 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CLR ETW 事件"
  - "ETW, CLR 事件"
  - "ETW, Common Language Runtime"
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Common Language Runtime 中的 ETW 事件
Common Language Runtime \(CLR\) 會透過各種偵錯和程式碼剖析事件提供有用的 Windows 事件追蹤 \(ETW\) 診斷資訊。  CLR ETW 事件會運用 Windows ETW 追蹤系統來擴充 Common Language Runtime 所提供的現有程式碼剖析和偵錯支援。  
  
 您可以在 MSDN 上的[使用 ETW 改善偵錯和效能調整](http://go.microsoft.com/fwlink/?LinkID=161142)文章中取得 ETW 的詳細資訊。  您可以在 NTDebugging 部落格的 [Windows 效能工具組 \- Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) \(英文\) 項目中找到 Xperf 的相關資訊。  
  
 其他 CLR ETW 工具可用時，將於 [CodePlex 網站](http://go.microsoft.com/fwlink/?LinkID=111138) 上提供。  
  
 對這些事件主題所描述的所有事件 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] \(含\) 以後版本是必要的。  Windows Vista 作業系統是最低階支援的用戶端，而 Windows Server 2008 是最低階支援的伺服器。  
  
## 在本節中  
 [控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)  
 描述用來擷取及檢視 ETW 事件的工具和命令。  
  
 [CLR ETW 提供者](../../../docs/framework/performance/clr-etw-providers.md)  
 提供了有關執行階段提供者和取消提供者，以及如何將它們用於 ETW 資料收集的相關資訊。  
  
 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 描述對於執行階段提供者和取消提供者，可用來依分類篩選事件的關鍵字。  
  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)  
 提供 CLR ETW 事件、其關鍵字、層級和事件資料的詳細資訊。  
  
## 請參閱  
 [.NET Framework 中的 ETW 事件](../../../docs/framework/performance/etw-events.md)