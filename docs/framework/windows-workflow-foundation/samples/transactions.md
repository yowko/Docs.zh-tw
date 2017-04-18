---
title: "異動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 異動
本節中的範例示範使用 [!INCLUDE[wf](../../../../includes/wf-md.md)] 工作流程交易的案例。  
  
## 在本節中  
 [在命令性 TransactionScope 中執行工作流程](../../../../docs/framework/windows-workflow-foundation/samples/execute-a-workflow-in-an-imperative-transactionscope.md)  
 示範如何從命令式 C\# 程式碼，在 <xref:System.Transactions.Transaction> 底下使用 <xref:System.Activities.WorkflowInvoker> 來執行工作流程。  
  
 [交易防護範圍](../../../../docs/framework/windows-workflow-foundation/samples/transaction-convoy-scope.md)  
 示範如何建立 Parallel Convoy 訊息活動模式搭配 <xref:System.ServiceModel.Activities.TransactedReceiveScope>，以建立多個作業可依任何順序同時在相同交易中發生的通訊協定模型。  
  
 [交易回復](../../../../docs/framework/windows-workflow-foundation/samples/transaction-rollback.md)  
 示範如何建立自訂 <xref:System.Activities.NativeActivity>，用來存取環境 <xref:System.Activities.RuntimeTransactionHandle> 以取得環境交易並明確回復此交易。  
  
 [隱藏交易範圍](../../../../docs/framework/windows-workflow-foundation/samples/suppress-transaction-scope.md)  
 示範如何撰寫自訂 `SuppressTransactionScope` 活動，以隱藏環境執行階段交易 \(如果有的話\)。  
  
 [交易的佇列](../../../../docs/framework/windows-workflow-foundation/samples/transacted-queues.md)  
 示範如何在 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 中整合佇列和交易，以建立可靠和可擴充的服務。