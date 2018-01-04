---
title: "單向服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d023d3623777a93cf72715410aed87fe8a63ee5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="one-way-services"></a>單向服務
服務作業的預設行為是要求-回覆模式。 在要求-回覆模式中，用戶端也都會等候回覆訊息，即使該服務作業已透過程式碼表示為 `void` 方法也是如此。 在單向作業中，只會傳輸一則訊息。 接收者不會傳送回覆訊息，傳送者也不會期待回覆訊息。  
  
 使用單向設計模式：  
  
-   當用戶端必須呼叫作業，而且不受作業層級之作業結果影響時。  
  
-   當使用 <xref:System.ServiceModel.NetMsmqBinding> 或 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 類別時。 ([!INCLUDE[crabout](../../../../includes/crabout-md.md)]此案例中，請參閱[WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。)  
  
 當作業為單向時，就不存在將錯誤資訊帶回到用戶端的回應訊息。 錯誤狀況的偵測方式，可以是透過使用基礎繫結的功能 (例如可靠工作階段)，或是設計使用兩個單向作業的雙工服務合約來進行，而前述的雙工服務會包含一個會從用戶端到服務來呼叫服務作業的單向合約，另一個介於服務與用戶端之間的單向合約，則可讓服務使用用戶端所實作的回呼來將錯誤傳回給用戶端。  
  
 若要建立單向服務合約，請定義您的服務合約，將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個作業，並將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設定為 `true`，如下列範例程式碼所示。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 如需完整範例，請參閱[單向](../../../../docs/framework/wcf/samples/one-way.md)範例。  
  
## <a name="clients-blocking-with-one-way-operations"></a>用戶端封鎖使用單向作業  
 您必須瞭解，儘管有些單向應用程式會在傳出資料寫入至網路連線時立即傳回，但在許多狀況下，繫結或服務的實作可能會導致 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端封鎖使用單向作業。 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式中，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件必須等到傳出資料已經寫入網路連線之後才會傳回。 包括單向作業的所有訊息交換模式都是如此；這表示在將資料寫入至傳輸時所發生的任何問題，都會導致用戶端無法傳回。 根據不同的問題，此結果可能會是在傳送訊息至服務時發生例外狀況或延遲。  
  
 例如，如果傳輸找不到該端點，便會擲回 <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> 例外狀況而不會發生什麼延遲。 然而，服務也可能因為某些原因而無法從線上讀取資料，進而導致用戶端傳輸傳送作業無法傳回。 在這些情況下，如果超過用戶端傳輸繫結上的 <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> 期限，便會擲回 <xref:System.TimeoutException?displayProperty=nameWithType>，但是必須等到已經超過逾時期限才會發生這種情況。 另外一種可能情形，則是出現在服務位置上的訊息多到服務無法將其處理成通過特定點。 在此情況下，單向用戶端會進行封鎖，直到服務能夠處理訊息，或是擲回例外狀況為止。  
  
 類似的情況會發生在服務 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.ServiceModel.ConcurrencyMode.Single>，而繫結使用工作階段的狀況下。 在此情況下，發送器會強制排序傳入訊息 (工作階段的需求)，進而阻止從網路讀取後來的訊息，直到服務已處理過該工作階段的先前訊息才會停止此狀況。 同樣地，用戶端會進行封鎖，不過是否會發生例外狀況則取決於服務是否能在用戶端的逾時設定前處理等候中的資料。  
  
 您可以在用戶端物件與用戶端傳輸的傳送作業之間插入緩衝區，以便稍微緩解這個問題。 例如，使用非同步呼叫或使用記憶體中的訊息佇列，都可讓用戶端物件能夠快速傳回。 兩種處理方法都可以增加功能，不過執行緒集區與訊息佇列的大小仍然會強制執行限制。  
  
 因此，建議的做法是檢查服務及用戶端上的各種控制項，然後測試您的應用程式案例以判斷兩端的最佳組態。 例如，如果使用工作階段會封鎖服務上的訊息處理，您可以將 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall> 以使每則訊息都能由不同的服務執行個體處理，並將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為 <xref:System.ServiceModel.ConcurrencyMode.Multiple>，以便一次讓一個以上的執行緒發送訊息。 另一種處理方法則是增加服務與用戶端繫結的讀取配額。  
  
## <a name="see-also"></a>請參閱  
 [單向](../../../../docs/framework/wcf/samples/one-way.md)
