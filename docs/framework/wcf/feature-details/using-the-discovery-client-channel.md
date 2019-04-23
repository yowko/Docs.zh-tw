---
title: 使用探索用戶端通道
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 298cafe34b20a3644f967acf15f831be5b0b90ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329930"
---
# <a name="using-the-discovery-client-channel"></a>使用探索用戶端通道
撰寫 WCF 用戶端應用程式時，您需要知道您所呼叫之服務的端點位址。 在很多情況下，無法事先知道服務的端點位址，或是服務的位址可能會隨著時間改變。 探索用戶端通道可讓您撰寫 WCF 用戶端應用程式、描述您要呼叫的服務，然後用戶端會自動傳送探查要求。 服務回應的時候，探索用戶端通道會從探查回應擷取服務的端點位址，並且使用此位址呼叫服務。  
  
## <a name="using-the-discovery-client-channel"></a>使用探索用戶端通道  
 若要使用探索用戶端通道，請將 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 的執行個體加入到您的用戶端通道堆疊。 另一種方法是使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，如果繫結還沒有 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>，就會自動加入至繫結。  
  
> [!CAUTION]
>  建議以 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 做為用戶端通道堆疊最上方的項目。 任何加到 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 上方的繫結項目，都必須確保建立的 <xref:System.ServiceModel.ChannelFactory> 或通道不會使用該端點位址或 `Via` 位址 (傳遞給 `CreateChannel` 方法)，因為這些可能沒有包含正確的位址。  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 類別包含兩個公用屬性：  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>，用來描述您要呼叫的服務。  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> 指定要傳送探索訊息的探索端點。  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> 屬性可以指定您要搜尋的服務合約、任何必要的範圍 URI，以及開啟通道嘗試次數的上限。 藉由呼叫建構函式指定的合約型別<xref:System.ServiceModel.Discovery.FindCriteria>。 範圍 URI 可以加入至 <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> 屬性。 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 屬性可讓您指定用戶端嘗試連接的結果數目上限。 收到探查回應時，用戶端會使用探查回應中的端點位址，嘗試開啟通道。 如果發生例外狀況，用戶端會移至下一個探查回應，若有必要，則會等候更多回應。 這個動作會繼續執行，直到通道已成功開啟，或是達到結果數目上限為止。 如需有關這些設定的詳細資訊，請參閱<xref:System.ServiceModel.Discovery.FindCriteria>。  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> 屬性可讓您指定要使用的探索端點。 通常這會是 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>，但也可能是任何有效的端點。  
  
 您必須特別注意，建立要使用的繫結以便與服務通訊時，要使用與服務完全相同的繫結。 唯一的差異是，用戶端繫結在堆疊的最上方會有一個 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>。 如果服務正在使用系統提供的其中一個繫結，請建立新的 <xref:System.ServiceModel.Channels.CustomBinding>，並且在系統提供的繫結中傳遞給 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> 建構函式。 然後，您可以透過在 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 屬性上呼叫 `Insert` 的方式，加入 <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A>。  
  
 一旦將 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 加入至您的繫結並妥善設定之後，您可以建立 WCF 用戶端類別的執行個體、開啟此執行個體，然後呼叫其方法。 下列範例使用探索用戶端通道，探索實作 `ICalculator` 類別 (用於「WCF 快速入門」教學課程) 並呼叫其 `Add` 方法的 WCF 服務。  
  
```  
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the   
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a>安全性與探索用戶端通道  
 使用探索用戶端通道時，會指定兩個端點。 一個會用來探索訊息 (通常是 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>)，另一個則是應用程式端點。 實作安全服務時，請務必謹慎，以確保兩個端點的安全。 如需有關安全性的詳細資訊，請參閱 < [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。
