---
title: 服務與異動
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c39c9f6e56dc4c2bf2feb5340d7d1bb1b96f5ab6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="services-and-transactions"></a>服務與異動
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式可以初始化用戶端內的交易，並協調服務作業中的交易。 用戶端可以初始化異動並叫用數個服務作業，同時確保服務作業已認可，或是復原為單一單位。  
  
 對於需要用戶端交易的服務作業，您可以指定 <xref:System.ServiceModel.ServiceBehaviorAttribute> 並設定服務合約的 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 和 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性，藉此啟用服務合約中的交易行為。 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 參數指定如果沒有擲回任何未處理的例外狀況，執行該方法的交易是否會自動完成。 如需有關這些屬性的詳細資訊，請參閱[ServiceModel 交易屬性](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)。  
  
 在服務作業中執行並由資源管理員所管理的工作 (例如記錄資料庫更新)，屬於用戶端異動的一部分。  
  
 下列範例示範如何使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性來控制服務端的交易行為。  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 您可以啟用交易和交易流程設定用戶端和服務繫結使用 Ws-atomictransaction 通訊協定，以及設定[ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)元素`true`，如下所示在下列範例組態中。  
  
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
  
 用戶端可以藉由建立 <xref:System.Transactions.TransactionScope> 並叫用交易範圍內的服務作業來開始交易。  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [System.ServiceModel 中的異動式支援](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [異動模型](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [WS 異動流程](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
