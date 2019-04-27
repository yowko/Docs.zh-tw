---
title: 使用具有探索用戶端通道的自訂繫結
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 6fe9370bb22ca424774fc8cb4566e0802bc06697
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918615"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="fe0c3-102">使用具有探索用戶端通道的自訂繫結</span><span class="sxs-lookup"><span data-stu-id="fe0c3-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="fe0c3-103">使用自訂繫結配合 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 時，您必須定義建立 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 執行個體的 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="fe0c3-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="fe0c3-104">建立 DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="fe0c3-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="fe0c3-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>負責建立<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>隨選執行個體。</span><span class="sxs-lookup"><span data-stu-id="fe0c3-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="fe0c3-106">若要定義探索端點提供者，請從 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 衍生一個類別，覆寫 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> 方法並傳回新的探索端點。</span><span class="sxs-lookup"><span data-stu-id="fe0c3-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="fe0c3-107">下列範例示範如何建立探索端點提供者。</span><span class="sxs-lookup"><span data-stu-id="fe0c3-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="fe0c3-108">定義探索端點提供者之後，即可建立自訂繫結，並且加入 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>，此項目會參考探索端點提供者，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fe0c3-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fe0c3-109">如需使用探索用戶端通道的詳細資訊，請參閱 <<c0> [ 使用探索用戶端通道](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)。</span><span class="sxs-lookup"><span data-stu-id="fe0c3-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="fe0c3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe0c3-110">See also</span></span>

- [<span data-ttu-id="fe0c3-111">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="fe0c3-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="fe0c3-112">使用探索用戶端通道</span><span class="sxs-lookup"><span data-stu-id="fe0c3-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
