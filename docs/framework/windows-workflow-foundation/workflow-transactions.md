---
title: 工作流程異動
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: e2a0c301abac562904e976fe09e5a68697b191e5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030151"
---
# <a name="workflow-transactions"></a>工作流程異動

[!INCLUDE[wf1](../../../includes/wf1-md.md)] 使用 <xref:System.Transactions> 活動來限定工作交易單元的範圍，以支援參與 <xref:System.Activities.Statements.TransactionScope> 交易。 <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> 必須明確地完成，而 <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> 活動則會在順利完成時隱含地呼叫交易。 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動的 <xref:System.Activities.Statements.TransactionScope> 中包含的任何活動都會參與交易。 WF 可以透過使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動，將交易流動至工作流程。 如同 <xref:System.Activities.Statements.TransactionScope> 活動，<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 中所含的所有活動都會參與交易。 WF 會確定相依於 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> 的活動都能與 <xref:System.Activities.Statements.TransactionScope> 和 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 共同運作。 如果系統提供的活動無法符合所有需求，可以使用 <xref:System.Activities.RuntimeTransactionHandle> 建置自訂活動，以啟用進階流程及交易控制案例。  
  
在下列範例中，工作流程建構組成<xref:System.Activities.Statements.Sequence>活動，其中包含子活動，包括<xref:System.Activities.Statements.TransactionScope>活動。 <xref:System.Activities.Statements.TransactionScope.Body%2A> 的 <xref:System.Activities.Statements.TransactionScope> 活動會在 <xref:System.Activities.Statements.TransactionScope> 活動初始化的交易之下執行。  
  
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
  
如需詳細資訊，請參閱有關使用<xref:System.ServiceModel.Activities.TransactedReceiveScope>，請參閱 <<c2> [ 流動交易，進出工作流程服務](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
