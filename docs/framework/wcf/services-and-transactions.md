---
title: 服務與異動
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4c59b83448f5a2c448843c12dae99c442441441f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143274"
---
# <a name="services-and-transactions"></a>服務與異動
Windows 通信基礎 （WCF） 應用程式可以從用戶端內部啟動事務，並在服務操作中協調事務。 用戶端可以初始化異動並叫用數個服務作業，同時確保服務作業已認可，或是復原為單一單位。  
  
 對於需要用戶端異動的服務作業，您可以指定 <xref:System.ServiceModel.ServiceBehaviorAttribute> 並設定服務合約的 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 和 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性，藉此啟用服務合約中的異動行為。 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 參數指定如果沒有擲回任何未處理的例外狀況，執行該方法的異動是否會自動完成。 有關這些屬性的詳細資訊，請參閱[服務模型事務屬性](./feature-details/servicemodel-transaction-attributes.md)。  
  
 在服務作業中執行並由資源管理員所管理的工作 (例如記錄資料庫更新)，屬於用戶端交易的一部分。  
  
 下列範例示範如何使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性來控制服務端的交易行為。  
  
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
  
 您可以通過配置用戶端和服務綁定來使用 WS-Atomic交易協定，並將[\<事務流>](../configure-apps/file-schema/wcf/transactionflow.md)元素設置為`true`，從而啟用事務和事務流，如以下示例配置所示。  
  
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
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [System.ServiceModel 中的異動式支援](./feature-details/transactional-support-in-system-servicemodel.md)
- [異動模型](./feature-details/transaction-models.md)
- [WS 交易流程](./samples/ws-transaction-flow.md)
