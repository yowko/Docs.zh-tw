---
title: "使用具有探索用戶端通道的自訂繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 716dc09d38c778c49a1e2e5fa094ef1bf004eb46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="e2f9c-102">使用具有探索用戶端通道的自訂繫結</span><span class="sxs-lookup"><span data-stu-id="e2f9c-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="e2f9c-103">使用自訂繫結配合 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 時，您必須定義建立 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 執行個體的 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="e2f9c-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="e2f9c-104">建立 DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="e2f9c-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="e2f9c-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>會負責建立<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>隨選執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2f9c-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="e2f9c-106">若要定義探索端點提供者，請從 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 衍生一個類別，覆寫 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> 方法並傳回新的探索端點。</span><span class="sxs-lookup"><span data-stu-id="e2f9c-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="e2f9c-107">下列範例示範如何建立探索端點提供者。</span><span class="sxs-lookup"><span data-stu-id="e2f9c-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="e2f9c-108">定義探索端點提供者之後，即可建立自訂繫結，並且加入 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>，此項目會參考探索端點提供者，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e2f9c-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2f9c-109">使用探索用戶端通道，請參閱[使用探索用戶端通道](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)。</span><span class="sxs-lookup"><span data-stu-id="e2f9c-109"> using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> <span data-ttu-id="e2f9c-110">如需完整的程式碼範例，請參閱[探索繫結項目範例](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span><span class="sxs-lookup"><span data-stu-id="e2f9c-110">For a complete code example, see [Discovery Binding Element Sample](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f9c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2f9c-111">See Also</span></span>  
 [<span data-ttu-id="e2f9c-112">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="e2f9c-112">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="e2f9c-113">使用探索用戶端通道</span><span class="sxs-lookup"><span data-stu-id="e2f9c-113">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [<span data-ttu-id="e2f9c-114">探索繫結項目範例</span><span class="sxs-lookup"><span data-stu-id="e2f9c-114">Discovery Binding Element Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
