---
title: 使用具有探索用戶端通道的自訂繫結
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 7473262ec52adfd917b8ec5cd7ec1f4935a3646d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195221"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>使用具有探索用戶端通道的自訂繫結
使用自訂繫結配合 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 時，您必須定義建立 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 執行個體的 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>。  
  
## <a name="creating-a-discoveryendpointprovider"></a>建立 DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>負責建立<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>隨選執行個體。 若要定義探索端點提供者，請從 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 衍生一個類別，覆寫 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> 方法並傳回新的探索端點。 下列範例示範如何建立探索端點提供者。  
  
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
  
 定義探索端點提供者之後，即可建立自訂繫結，並且加入 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>，此項目會參考探索端點提供者，如下列範例所示。  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 如需使用探索用戶端通道的詳細資訊，請參閱 <<c0> [ 使用探索用戶端通道](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)。 
  
## <a name="see-also"></a>另請參閱  

- [WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
- [使用探索用戶端通道](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  