---
title: "Analytic Tracing with ETW | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "diagnostics [WCF], analytic tracing"
  - "administration [WCF], analytic tracing"
  - "analytic tracing [WCF]"
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Analytic Tracing with ETW
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 分析追蹤提供可在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務執行期間擷取診斷資訊的方法。[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤事件會在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 堆疊中的關鍵點發出，以便在實際執行環境中處理 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的疑難排解。對於裝載 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的產品伺服器，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的分析追蹤幾乎不會影響效能，因為這些事件以非常有效率的方式發出到 Windows 事件追蹤 \(ETW\) 工作階段。  
  
## 在本節中  
 [分析追蹤的概觀](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 討論 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤如何在 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中運作。  
  
 [動態地啟用分析的追蹤](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 討論如何啟用或停用 ETW 動態追蹤。  
  
 [設定訊息流程追蹤](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 說明如何設定訊息流程追蹤。  
  
 [分析的追蹤事件參考](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 顯示一份資料表，列出事件識別碼，並附上事件層級、事件訊息及關鍵字。  
  
## 請參閱  
 [WCF 服務及 Windows 的事件追蹤](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)   
 [在 Windows 事件追蹤中追蹤事件](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)