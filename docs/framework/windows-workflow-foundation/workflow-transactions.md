---
title: "工作流程交易 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 工作流程交易
[!INCLUDE[wf1](../../../includes/wf1-md.md)] 使用 <xref:System.Activities.Statements.TransactionScope> 活動來限定工作交易單元的範圍，以支援參與 <xref:System.Transactions> 交易。<xref:System.Transactions.TransactionScope?displayProperty=fullName> 必須明確地完成，而 <xref:System.Activities.Statements.TransactionScope?displayProperty=fullName> 活動則會在順利完成時隱含地呼叫交易。<xref:System.Activities.Statements.TransactionScope> 活動之 <xref:System.Activities.Statements.TransactionScope.Body%2A> 項目所含的所有活動都會參與交易。WF 可以透過使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動，將交易流動至工作流程。如同 <xref:System.Activities.Statements.TransactionScope> 活動，<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 中所含的所有活動都會參與交易。WF 會確定相依於 <xref:System.Transactions.Transaction.Current%2A?displayProperty=fullName> 的活動都能與 <xref:System.Activities.Statements.TransactionScope> 和 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 共同運作。如果系統提供的活動無法符合所有需求，可以使用 <xref:System.Activities.RuntimeTransactionHandle> 建置自訂活動，以啟用進階流程及交易控制案例。  
  
 下列範例取自 [基本 TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) 範例，其中所建置的工作流程由 <xref:System.Activities.Statements.Sequence> 活動組成，該活動包含一個包括 <xref:System.Activities.Statements.TransactionScope> 活動的子活動。<xref:System.Activities.Statements.TransactionScope> 的 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動會在 <xref:System.Activities.Statements.TransactionScope> 活動初始化的交易之下執行。  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] 基本的 [異動](../../../docs/framework/windows-workflow-foundation/samples/basic-transactions.md) 範例，以及以 [異動](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) 範例為基礎的案例。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] 關於使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope>，請參閱[進出工作流程服務的交易流動](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)。  
  
## 請參閱  
 <xref:System.Activities.Statements.TransactionScope>   
 <xref:System.Transactions.TransactionScope>   
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=fullName>