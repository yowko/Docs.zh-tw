---
title: 服務與異動
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: e60f84aafe6c62a657cd3f27c9ccdb6b65186c35
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235905"
---
# <a name="services-and-transactions"></a><span data-ttu-id="01491-102">服務與異動</span><span class="sxs-lookup"><span data-stu-id="01491-102">Services and Transactions</span></span>

<span data-ttu-id="01491-103">Windows Communication Foundation (WCF) 應用程式可以從用戶端起始交易，並協調服務作業內的交易。</span><span class="sxs-lookup"><span data-stu-id="01491-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="01491-104">用戶端可以初始化異動並叫用數個服務作業，同時確保服務作業已認可，或是復原為單一單位。</span><span class="sxs-lookup"><span data-stu-id="01491-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="01491-105">對於需要用戶端異動的服務作業，您可以指定 <xref:System.ServiceModel.ServiceBehaviorAttribute> 並設定服務合約的 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 和 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性，藉此啟用服務合約中的異動行為。</span><span class="sxs-lookup"><span data-stu-id="01491-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="01491-106"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 參數指定如果沒有擲回任何未處理的例外狀況，執行該方法的異動是否會自動完成。</span><span class="sxs-lookup"><span data-stu-id="01491-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="01491-107">如需這些屬性的詳細資訊，請參閱 [System.servicemodel 交易屬性](./feature-details/servicemodel-transaction-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="01491-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="01491-108">在服務作業中執行並由資源管理員所管理的工作 (例如記錄資料庫更新)，屬於用戶端交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="01491-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="01491-109">下列範例示範如何使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性來控制服務端的交易行為。</span><span class="sxs-lookup"><span data-stu-id="01491-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="01491-110">您可以設定用戶端和服務系結使用 WS-AtomicTransaction 的通訊協定，並將專案設定為，以啟用交易和交易流程 [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) `true` ，如下列範例設定所示。</span><span class="sxs-lookup"><span data-stu-id="01491-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"
          binding="netTcpBinding"
          bindingConfiguration="netTcpBindingWSAT"
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="01491-111">用戶端可以藉由建立 <xref:System.Transactions.TransactionScope> 並叫用交易範圍內的服務作業來開始交易。</span><span class="sxs-lookup"><span data-stu-id="01491-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="01491-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01491-112">See also</span></span>

- [<span data-ttu-id="01491-113">System.ServiceModel 中的交易式支援</span><span class="sxs-lookup"><span data-stu-id="01491-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="01491-114">異動模型</span><span class="sxs-lookup"><span data-stu-id="01491-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="01491-115">WS 交易流程</span><span class="sxs-lookup"><span data-stu-id="01491-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
