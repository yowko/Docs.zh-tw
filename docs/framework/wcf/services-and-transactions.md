---
title: 服務與異動
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 5078e12ed5c68556a1d1d04d01c90440b57c1407
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736399"
---
# <a name="services-and-transactions"></a>服務與異動
Windows Communication Foundation (WCF) 應用程式可以起始從交易內的用戶端，並協調服務作業內的交易。 用戶端可以初始化異動並叫用數個服務作業，同時確保服務作業已認可，或是復原為單一單位。  
  
 對於需要用戶端異動的服務作業，您可以指定 <xref:System.ServiceModel.ServiceBehaviorAttribute> 並設定服務合約的 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 和 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性，藉此啟用服務合約中的異動行為。 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 參數指定如果沒有擲回任何未處理的例外狀況，執行該方法的異動是否會自動完成。 如需有關這些屬性的詳細資訊，請參閱 < [ServiceModel 異動屬性](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)。  
  
 在服務作業中執行並由資源管理員所管理的工作 (例如記錄資料庫更新)，屬於用戶端異動的一部分。  
  
 下列範例示範如何使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性來控制服務端的異動行為。  
  
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
  
 您可以讓交易和交易流程所設定的用戶端和服務繫結使用 WS-AtomicTransaction 通訊協定，並設定[ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)項目`true`，如所示在下列範例組態中。  
  
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
  
 用戶端可以藉由建立 <xref:System.Transactions.TransactionScope> 並叫用異動範圍內的服務作業來開始異動。  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>另請參閱
- [System.ServiceModel 中的異動式支援](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)
- [異動模型](../../../docs/framework/wcf/feature-details/transaction-models.md)
- [WS 異動流程](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
