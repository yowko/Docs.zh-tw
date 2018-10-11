---
title: '&lt;ws2007HttpBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
author: BrucePerlerMS
ms.openlocfilehash: 6d02b787618275cbbbdd17a54a1f14a6d8e2d2c4
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086514"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="26ad8-102">&lt;ws2007HttpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="26ad8-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="26ad8-103">表示搭配使用的安全性設定[ \<lt;ws2007httpbinding&gt >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="26ad8-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="26ad8-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26ad8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="26ad8-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="26ad8-105">\<bindings></span></span>  
<span data-ttu-id="26ad8-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="26ad8-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="26ad8-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="26ad8-107">\<binding></span></span>  
<span data-ttu-id="26ad8-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="26ad8-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ad8-109">語法</span><span class="sxs-lookup"><span data-stu-id="26ad8-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26ad8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="26ad8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="26ad8-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="26ad8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26ad8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="26ad8-112">Attributes</span></span>  
  
|<span data-ttu-id="26ad8-113">屬性</span><span class="sxs-lookup"><span data-stu-id="26ad8-113">Attribute</span></span>|<span data-ttu-id="26ad8-114">描述</span><span class="sxs-lookup"><span data-stu-id="26ad8-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="26ad8-115">-選擇性。</span><span class="sxs-lookup"><span data-stu-id="26ad8-115">-   Optional.</span></span> <span data-ttu-id="26ad8-116">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="26ad8-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="26ad8-117">預設為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="26ad8-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="26ad8-118">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="26ad8-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="26ad8-119">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="26ad8-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="26ad8-120">值</span><span class="sxs-lookup"><span data-stu-id="26ad8-120">Value</span></span>|<span data-ttu-id="26ad8-121">描述</span><span class="sxs-lookup"><span data-stu-id="26ad8-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="26ad8-122">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="26ad8-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="26ad8-123">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="26ad8-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="26ad8-124">而服務必須使用安全通訊端層 (SSL) 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="26ad8-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="26ad8-125">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="26ad8-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="26ad8-126">用戶端驗證透過`ClientCredentials`的屬性[\<傳輸 >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="26ad8-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="26ad8-127">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="26ad8-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="26ad8-128">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="26ad8-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="26ad8-129">這個模式透過 <xref:System.ServiceModel.Security.SecurityMessageProperty> 提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="26ad8-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="26ad8-130">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="26ad8-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="26ad8-131">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="26ad8-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="26ad8-132">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="26ad8-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26ad8-133">子元素</span><span class="sxs-lookup"><span data-stu-id="26ad8-133">Child Elements</span></span>  
  
|<span data-ttu-id="26ad8-134">項目</span><span class="sxs-lookup"><span data-stu-id="26ad8-134">Element</span></span>|<span data-ttu-id="26ad8-135">描述</span><span class="sxs-lookup"><span data-stu-id="26ad8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26ad8-136">\<transport></span><span class="sxs-lookup"><span data-stu-id="26ad8-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="26ad8-137">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="26ad8-137">Defines the transport security settings.</span></span> <span data-ttu-id="26ad8-138">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="26ad8-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="26ad8-139">當模式設定為 Transport，才會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="26ad8-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="26ad8-140">\<message></span><span class="sxs-lookup"><span data-stu-id="26ad8-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="26ad8-141">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="26ad8-141">Defines the security settings for the message.</span></span> <span data-ttu-id="26ad8-142">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="26ad8-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="26ad8-143">當模式設定為 Transport，就不會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="26ad8-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26ad8-144">父項目</span><span class="sxs-lookup"><span data-stu-id="26ad8-144">Parent Elements</span></span>  
  
|<span data-ttu-id="26ad8-145">項目</span><span class="sxs-lookup"><span data-stu-id="26ad8-145">Element</span></span>|<span data-ttu-id="26ad8-146">描述</span><span class="sxs-lookup"><span data-stu-id="26ad8-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26ad8-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="26ad8-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="26ad8-148">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="26ad8-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26ad8-149">備註</span><span class="sxs-lookup"><span data-stu-id="26ad8-149">Remarks</span></span>  
 <span data-ttu-id="26ad8-150">這個項目主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="26ad8-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="26ad8-151">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="26ad8-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ad8-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26ad8-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="26ad8-153">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="26ad8-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="26ad8-154">繫結</span><span class="sxs-lookup"><span data-stu-id="26ad8-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="26ad8-155">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="26ad8-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="26ad8-156">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="26ad8-156">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="26ad8-157">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="26ad8-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
