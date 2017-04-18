---
title: "例外狀況、交易與補償 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式設計 [WF], 錯誤處理"
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 例外狀況、交易與補償
[!INCLUDE[wf1](../../../includes/wf1-md.md)] 提供數種不同的機制，可用於處理工作流程中的執行階段錯誤狀況。工作流程可以合併運用例外狀況處理常式、交易、取消與補償來處理錯誤狀況，並從錯誤狀況正常復原。  
  
## 在本節中  
 [例外狀況](../../../docs/framework/windows-workflow-foundation//exceptions.md)  
 示範如何使用 <xref:System.Activities.Statements.TryCatch> 活動處理工作流程中的例外狀況。  
  
 [交易](../../../docs/framework/windows-workflow-foundation//workflow-transactions.md)  
 示範如何使用 <xref:System.Activities.Statements.TransactionScope> 活動運用工作流程中的交易。  
  
 [補償](../../../docs/framework/windows-workflow-foundation//compensation.md)  
 描述工作流程中的補償，並且示範如何使用 <xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate> 和 <xref:System.Activities.Statements.Confirm> 等補償活動。  
  
 [取消](../../../docs/framework/windows-workflow-foundation//modeling-cancellation-behavior-in-workflows.md)  
 描述如何使用內建活動以及自訂活動，在工作流程中執行取消處理。  
  
 [偵錯工作流程](../../../docs/framework/windows-workflow-foundation//debugging-workflows.md)  
 描述如何偵錯工作流程。