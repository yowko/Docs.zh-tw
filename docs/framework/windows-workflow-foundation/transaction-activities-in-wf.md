---
title: "WF 中的交易活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# WF 中的交易活動
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 有幾種系統提供的活動，用於模型化交易、補償和取消。這些程式設計模型允許在商務邏輯和錯誤處理發生變更時，工作流程可繼續執行。[!INCLUDE[crabout](../../../includes/crabout-md.md)]以進一步了解交易、補償和取消，請參閱[交易](../../../docs/framework/windows-workflow-foundation//workflow-transactions.md), [補償](../../../docs/framework/windows-workflow-foundation//compensation.md) 和 [取消](../../../docs/framework/windows-workflow-foundation//modeling-cancellation-behavior-in-workflows.md)。  
  
## 交易活動  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|將取消邏輯 \(採活動形式\) 與執行主要路徑 \(也使用活動表示\) 相關聯。|  
|<xref:System.Activities.Statements.CompensableActivity>|支援其子活動的補償。|  
|<xref:System.Activities.Statements.Compensate>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的補償處理常式。|  
|<xref:System.Activities.Statements.Confirm>|明確叫用 <xref:System.Activities.Statements.CompensableActivity> 的確認處理常式。|  
|<xref:System.Activities.Statements.TransactionScope>|區分交易界限。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|範圍為接收之訊息所啟始的交易存留期。交易可能會流動至初始訊息上的工作流程，或是在接收到訊息時由發送器所建立。 **Note:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> 位在 \[**工具箱**\] 的 \[**傳訊**\] 區段中。|