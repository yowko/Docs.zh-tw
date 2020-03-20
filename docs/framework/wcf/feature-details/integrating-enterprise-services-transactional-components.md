---
title: 整合 Enterprise Services 異動元件
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184744"
---
# <a name="integrating-enterprise-services-transactional-components"></a>整合 Enterprise Services 異動元件

Windows 通信基礎 （WCF） 提供了與企業服務集成的自動機制（請參閱[與 COM+ 應用程式集成](integrating-with-com-plus-applications.md)）。 不過，您可能希望能夠彈性地開發出可透過內部方式使用裝載於 Enterprise Services 之異動元件的服務。 由於 WCF 事務功能構建在<xref:System.Transactions>基礎結構上，因此將企業服務與 WCF 集成的過程與指定與企業服務之間的<xref:System.Transactions>互通性的過程相同，如[與企業服務和 COM+ 事務的互通性](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))中所述。  
  
 為了在傳入的流動異動和 COM+ 內容異動之間提供所需等級的互通性，此服務的實作必須建立 <xref:System.Transactions.TransactionScope> 執行個體並使用適當的 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉值。  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>整合 Enterprise Services 和服務作業  
 下列程式碼範例會示範一項允許異動流程的作業，這項作業會建立具有 <xref:System.Transactions.TransactionScope> 選項的 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>。 下列狀況適用於本案例：  
  
- 如果用戶端流動交易，則作業 (包括 Enterprise Services 元件的呼叫) 會在該交易的範圍內執行。 使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 會確保交易與 <xref:System.EnterpriseServices> 內容為同步處理，也就是說 <xref:System.Transactions> 的環境交易和 <xref:System.EnterpriseServices> 會是相同的。  
  
- 如果用戶端沒有流動異動，此時將 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 設定為 `true` 便會建立供作業使用的新異動範圍。 同樣地，使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 可確保作業的交易與 <xref:System.EnterpriseServices> 元件內容中所使用的交易是相同的。  
  
 任何其他的方法呼叫也會發生在相同作業的交易範圍內。  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services
         // component
  
         // Call UpdateOtherCustomerData method on an Enterprise
         // Services component
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 如果作業的目前交易和 Enterprise Services 交易元件的呼叫之間不需要同步處理，那麼請在初始化 <xref:System.Transactions.EnterpriseServicesInteropOption.None> 執行個體時使用 <xref:System.Transactions.TransactionScope> 選項。  
  
## <a name="integrating-enterprise-services-with-a-client"></a>整合 Enterprise Services 和用戶端  
 下列程式碼會示範以 <xref:System.Transactions.TransactionScope> 設定來使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 執行個體的用戶端程式碼。 在此案例中，支援異動流程的服務作業呼叫會發生於呼叫 Enterprise Services 元件的相同異動範圍內，  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services
        // component
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [與 COM+ 應用程式集成](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [整合 COM 應用程式](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
