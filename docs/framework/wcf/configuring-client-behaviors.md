---
title: 設定用戶端行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193651"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="c2ebf-102">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="c2ebf-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="c2ebf-103">Windows Communication Foundation (WCF) 設定行為以兩種方式： 藉由參考行為組態，是定義於`<behavior>`用戶端應用程式組態檔-，或以程式設計方式呼叫中的區段應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="c2ebf-104">這個主題將描述這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="c2ebf-105">使用組態檔時，行為組態都是具名的組態設定集合。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="c2ebf-106">每個行為組態的名稱必須是獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="c2ebf-107">會在端點組態的 `behaviorConfiguration` 屬性中使用這個字串，以便將端點連結至行為。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2ebf-108">範例</span><span class="sxs-lookup"><span data-stu-id="c2ebf-108">Example</span></span>  
 <span data-ttu-id="c2ebf-109">下列組態程式碼會定義名稱為 `myBehavior` 的行為。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="c2ebf-110">用戶端端點會參考 `behaviorConfiguration` 屬性中的這個行為。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="c2ebf-111">以程式設計方式使用行為</span><span class="sxs-lookup"><span data-stu-id="c2ebf-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="c2ebf-112">您也可以設定或以程式設計方式插入行為，找出適當`Behaviors`Windows Communication Foundation (WCF) 用戶端物件或用戶端通道處理站物件之前開啟用戶端上的屬性。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2ebf-113">範例</span><span class="sxs-lookup"><span data-stu-id="c2ebf-113">Example</span></span>  
 <span data-ttu-id="c2ebf-114">下列程式碼範例會示範如何以程式設計的方式插入行為，其方法是先存取傳回自 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 屬性之 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性，再建立通道物件。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="c2ebf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2ebf-115">See also</span></span>

- [<span data-ttu-id="c2ebf-116">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c2ebf-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
