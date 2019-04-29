---
title: 工作流程異動
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 17e4b712f5b6955ab777168d60d8a28e8b0ebd63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670192"
---
# <a name="workflow-transactions"></a><span data-ttu-id="3a337-102">工作流程異動</span><span class="sxs-lookup"><span data-stu-id="3a337-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="3a337-103">使用 <xref:System.Transactions> 活動來限定工作異動單元的範圍，以支援參與 <xref:System.Activities.Statements.TransactionScope> 異動。</span><span class="sxs-lookup"><span data-stu-id="3a337-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="3a337-104"><xref:System.Transactions.TransactionScope?displayProperty=nameWithType> 必須明確地完成，而 <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> 活動則會在順利完成時隱含地呼叫交易。</span><span class="sxs-lookup"><span data-stu-id="3a337-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="3a337-105"><xref:System.Activities.Statements.TransactionScope.Body%2A> 活動的 <xref:System.Activities.Statements.TransactionScope> 中包含的任何活動都會參與異動。</span><span class="sxs-lookup"><span data-stu-id="3a337-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="3a337-106">WF 可以透過使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動，將交易流動至工作流程。</span><span class="sxs-lookup"><span data-stu-id="3a337-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="3a337-107">如同 <xref:System.Activities.Statements.TransactionScope> 活動，<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 中所含的所有活動都會參與交易。</span><span class="sxs-lookup"><span data-stu-id="3a337-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="3a337-108">WF 會確定相依於 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> 的活動都能與 <xref:System.Activities.Statements.TransactionScope> 和 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 共同運作。</span><span class="sxs-lookup"><span data-stu-id="3a337-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="3a337-109">如果系統提供的活動無法符合所有需求，可以使用 <xref:System.Activities.RuntimeTransactionHandle> 建置自訂活動，以啟用進階流程及異動控制案例。</span><span class="sxs-lookup"><span data-stu-id="3a337-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="3a337-110">在下列範例中，工作流程建構組成<xref:System.Activities.Statements.Sequence>活動，其中包含子活動，包括<xref:System.Activities.Statements.TransactionScope>活動。</span><span class="sxs-lookup"><span data-stu-id="3a337-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="3a337-111"><xref:System.Activities.Statements.TransactionScope.Body%2A> 的 <xref:System.Activities.Statements.TransactionScope> 活動會在 <xref:System.Activities.Statements.TransactionScope> 活動初始化的交易之下執行。</span><span class="sxs-lookup"><span data-stu-id="3a337-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
<span data-ttu-id="3a337-112">如需詳細資訊，請參閱有關使用<xref:System.ServiceModel.Activities.TransactedReceiveScope>，請參閱 <<c2> [ 流動交易，進出工作流程服務](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3a337-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a337-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a337-113">See also</span></span>

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
