---
title: "設定用戶端行為"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f16f32128c7223fa600802ae593d36286847dc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="70eb7-102">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="70eb7-102">Configuring Client Behaviors</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="70eb7-103"> 會以兩種方式設定行為：一種是參考行為組態 (定義於用戶端應用程式組態檔的 `<behavior>` 區段中)，另一種是透過呼叫應用程式，以程式設計的方式設定。</span><span class="sxs-lookup"><span data-stu-id="70eb7-103"> configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="70eb7-104">這個主題將描述這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="70eb7-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="70eb7-105">使用組態檔時，行為組態都是具名的組態設定集合。</span><span class="sxs-lookup"><span data-stu-id="70eb7-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="70eb7-106">每個行為組態的名稱必須是獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="70eb7-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="70eb7-107">會在端點組態的 `behaviorConfiguration` 屬性中使用這個字串，以便將端點連結至行為。</span><span class="sxs-lookup"><span data-stu-id="70eb7-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70eb7-108">範例</span><span class="sxs-lookup"><span data-stu-id="70eb7-108">Example</span></span>  
 <span data-ttu-id="70eb7-109">下列組態程式碼會定義名稱為 `myBehavior` 的行為。</span><span class="sxs-lookup"><span data-stu-id="70eb7-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="70eb7-110">用戶端端點會參考 `behaviorConfiguration` 屬性中的這個行為。</span><span class="sxs-lookup"><span data-stu-id="70eb7-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="70eb7-111">以程式設計方式使用行為</span><span class="sxs-lookup"><span data-stu-id="70eb7-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="70eb7-112">您也可以用程式設計的方式來設定或插入行為，方法是在開啟用戶端之前，在 `Behaviors` 用戶端物件上或用戶端通道物件處理站上尋找適當的 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 屬性。</span><span class="sxs-lookup"><span data-stu-id="70eb7-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70eb7-113">範例</span><span class="sxs-lookup"><span data-stu-id="70eb7-113">Example</span></span>  
 <span data-ttu-id="70eb7-114">下列程式碼範例會示範如何以程式設計的方式插入行為，其方法是先存取傳回自 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 屬性之 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性，再建立通道物件。</span><span class="sxs-lookup"><span data-stu-id="70eb7-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="70eb7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70eb7-115">See Also</span></span>  
 [<span data-ttu-id="70eb7-116">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="70eb7-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
