---
title: 探索繫結項目範例
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: d906d9a389c50095f2af5d52e3874c3e43199e68
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964499"
---
# <a name="discovery-binding-element-sample"></a>探索繫結項目範例
此範例示範如何使用探索用戶端繫結項目探索服務。 此功能可讓開發人員將探索用戶端通道加入至其現有的用戶端通道堆疊中，讓程式設計模型變得非常直覺。 開啟相關聯的通道時，就會使用探索解析服務的位址。 這個範例包含下列專案：  
  
-   **CalculatorService**： 可探索的 WCF 服務。  
  
-   **CalculatorClient**： 使用探索用戶端通道搜尋與呼叫 CalculatorService 的 WCF 用戶端應用程式。  
  
-   **DynamicCalculatorClient**： 使用動態端點搜尋與呼叫 CalculatorService 的 WCF 用戶端應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 此專案包含實作 `ICalculatorService` 合約的簡易計算機服務。  
  
 以下的 App.config 檔案用來在服務行為以及探索端點中加入 `<serviceDiscovery>` 行為。  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 這會讓服務及其端點變成可搜尋。 CalculatorService 是一個自我裝載的服務，此服務會使用 NetTcpBinding binding 加入一個端點。 它也會將 `EndpointDiscoveryBehavior` 加入至端點並指定範圍，如下列程式碼所示。  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 此專案包含將訊息傳送至 CalculatorService 的用戶端實作。 此程式會使用 `CreateCustomBindingWithDiscoveryElement()` 方法建立使用探索用戶端通道的自訂繫結。  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 具現化 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 之後，開發人員會指定搜尋服務時使用的準則。 在此情況下，探索尋找準則為 `ICalculatorService` 類型。 此外，開發人員會指定 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>，以傳回指定搜尋服務之位置的 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>。 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 會傳回新的 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 執行個體。 如需詳細資訊，請參閱 <<c0> [ 使用具有探索用戶端通道的自訂繫結](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md)。  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 在此情況下，用戶端會使用探索通訊協定所定義的 UDP 多點傳送機制搜尋區域子網路上的服務。 方法的其他部分會建立自訂繫結，並將探索繫結項目插入堆疊頂端。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 必須放在繫結堆疊的頂端。 <xref:System.ServiceModel.Channels.BindingElement> 頂端的任何 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 都必須確認它所建立的通道處理站或通道沒有使用 `EndpointAddress` 或 `Via` 屬性，因為實際位址只會在探索用戶端通道找到。  
  
 接著，`CalculatorClient` 可以透過傳入這個自訂繫結以及端點位址來進行具現化。  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 使用探索用戶端通道時，會傳入先前指定的固定端點位址。 現在探索用戶端通道會在執行階段尋找由尋找準則所指定的服務並進行連接。 若要讓服務和用戶端建立連接，它們必須擁有相同的基礎繫結堆疊。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟方案。  
  
2.  建置方案。  
  
3.  執行服務應用程式以及每個用戶端應用程式。  
  
4.  請注意，用戶端不需知道位址，就能找到此服務。  
  
## <a name="see-also"></a>另請參閱
