---
title: "搭配 WCF 使用多個驗證配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db2545470c416fe066226124fb7833ef5d9e5d13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="335ed-102">搭配 WCF 使用多個驗證配置</span><span class="sxs-lookup"><span data-stu-id="335ed-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="335ed-103">WCF 現在允許您在單一端點上指定多個驗證配置。</span><span class="sxs-lookup"><span data-stu-id="335ed-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="335ed-104">此外，Web 裝載服務可以直接從 IIS 繼承驗證設定。</span><span class="sxs-lookup"><span data-stu-id="335ed-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="335ed-105">自我裝載服務可以指定可使用的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="335ed-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="335ed-106">如需有關如何在 IIS 中設定驗證設定的詳細資訊，請參閱[IIS 驗證](http://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="335ed-106">For more information about setting authentication settings in IIS, see [IIS Authentication](http://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="335ed-107">IIS 裝載的服務</span><span class="sxs-lookup"><span data-stu-id="335ed-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="335ed-108">對於 IIS 裝載的服務，設定您希望在 IIS 中使用的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="335ed-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="335ed-109">然後在服務的 web.config 檔案中，繫結組態的 clientCredential 類型指定為"InheritedFromHost"下列 XML 程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="335ed-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="335ed-110">您可以指定您只想要使用 ServiceAuthenticationBehavior 服務搭配使用的驗證配置子集或\<serviceAuthenticationManager > 項目。</span><span class="sxs-lookup"><span data-stu-id="335ed-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="335ed-111">在程式碼中進行這項設定時，請使用 ServiceAuthenticationBehavior，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="335ed-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="335ed-112">進行這項設定設定檔中，當使用\<serviceAuthenticationManager > 項目，如下列 XML 片段所示。</span><span class="sxs-lookup"><span data-stu-id="335ed-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="335ed-113">這將確保只會根據在 IIS 中選取的部分，考慮將這裡列出的驗證配置子集套用在服務端點。</span><span class="sxs-lookup"><span data-stu-id="335ed-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="335ed-114">這表示開發人員可以在 serviceAuthenticationManager 清單中省略該項基本驗證，將其從清單中排除，即使已在 IIS 中啟用亦同，這項驗證將不會套用在服務端點上。</span><span class="sxs-lookup"><span data-stu-id="335ed-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="335ed-115">自我裝載的服務</span><span class="sxs-lookup"><span data-stu-id="335ed-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="335ed-116">自我裝載服務的設定方式有點不同，因為沒有可繼承其設定的 IIS。</span><span class="sxs-lookup"><span data-stu-id="335ed-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="335ed-117">在此您可以使用\<serviceAuthenticationManager > 項目或 ServiceAuthenticationBehavior 來指定將會繼承驗證設定。</span><span class="sxs-lookup"><span data-stu-id="335ed-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="335ed-118">在程式碼中，看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="335ed-118">In code it looks like this:</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="335ed-119">在組態中，看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="335ed-119">In config, it looks like this:</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="335ed-120">然後您可以在繫結設定中指定 InheritFromHost，如下列 XML 片段所示。</span><span class="sxs-lookup"><span data-stu-id="335ed-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="335ed-121">或者，您可在 HTTP 傳輸繫結元素上設定驗證配置，以指定自訂繫結中的驗證配置，如下列組態片段所示。</span><span class="sxs-lookup"><span data-stu-id="335ed-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="335ed-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="335ed-122">See Also</span></span>  
 [<span data-ttu-id="335ed-123">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="335ed-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="335ed-124">端點： 位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="335ed-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="335ed-125">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="335ed-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="335ed-126">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="335ed-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="335ed-127">繫結</span><span class="sxs-lookup"><span data-stu-id="335ed-127">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="335ed-128">繫結</span><span class="sxs-lookup"><span data-stu-id="335ed-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="335ed-129">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="335ed-129">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
