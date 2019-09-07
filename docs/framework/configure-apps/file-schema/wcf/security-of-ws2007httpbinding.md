---
title: <security> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ab5969da6a2d7cb59c057fd5bb909add6b6398a4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399792"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="6ce90-102">\<ws2007HttpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6ce90-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="6ce90-103">表示與[ \<ws2007HttpBinding >](ws2007httpbinding.md)元素搭配使用的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6ce90-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="6ce90-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ce90-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6ce90-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6ce90-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6ce90-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6ce90-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6ce90-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6ce90-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="6ce90-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="6ce90-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6ce90-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="6ce90-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce90-110">語法</span><span class="sxs-lookup"><span data-stu-id="6ce90-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ce90-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6ce90-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6ce90-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6ce90-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ce90-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6ce90-113">Attributes</span></span>  
  
|<span data-ttu-id="6ce90-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6ce90-114">Attribute</span></span>|<span data-ttu-id="6ce90-115">說明</span><span class="sxs-lookup"><span data-stu-id="6ce90-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6ce90-116">選擇性.</span><span class="sxs-lookup"><span data-stu-id="6ce90-116">-   Optional.</span></span> <span data-ttu-id="6ce90-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="6ce90-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6ce90-118">預設為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="6ce90-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="6ce90-119">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="6ce90-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6ce90-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="6ce90-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6ce90-121">值</span><span class="sxs-lookup"><span data-stu-id="6ce90-121">Value</span></span>|<span data-ttu-id="6ce90-122">說明</span><span class="sxs-lookup"><span data-stu-id="6ce90-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6ce90-123">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="6ce90-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="6ce90-124">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6ce90-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="6ce90-125">而服務必須使用安全通訊端層 (SSL) 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="6ce90-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="6ce90-126">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="6ce90-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6ce90-127">用戶端驗證是透過`ClientCredentials` [ \<transport >](transport-of-ws2007httpbinding.md)元素的屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="6ce90-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="6ce90-128">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6ce90-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6ce90-129">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="6ce90-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="6ce90-130">這個模式透過 <xref:System.ServiceModel.Security.SecurityMessageProperty> 提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="6ce90-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="6ce90-131">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="6ce90-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="6ce90-132">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="6ce90-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="6ce90-133">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="6ce90-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ce90-134">子元素</span><span class="sxs-lookup"><span data-stu-id="6ce90-134">Child Elements</span></span>  
  
|<span data-ttu-id="6ce90-135">項目</span><span class="sxs-lookup"><span data-stu-id="6ce90-135">Element</span></span>|<span data-ttu-id="6ce90-136">描述</span><span class="sxs-lookup"><span data-stu-id="6ce90-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ce90-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="6ce90-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="6ce90-138">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6ce90-138">Defines the transport security settings.</span></span> <span data-ttu-id="6ce90-139">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="6ce90-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="6ce90-140">當模式設定為 Transport，才會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="6ce90-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="6ce90-141">\<message></span><span class="sxs-lookup"><span data-stu-id="6ce90-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="6ce90-142">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6ce90-142">Defines the security settings for the message.</span></span> <span data-ttu-id="6ce90-143">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="6ce90-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="6ce90-144">當模式設定為 Transport，就不會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="6ce90-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ce90-145">父項目</span><span class="sxs-lookup"><span data-stu-id="6ce90-145">Parent Elements</span></span>  
  
|<span data-ttu-id="6ce90-146">項目</span><span class="sxs-lookup"><span data-stu-id="6ce90-146">Element</span></span>|<span data-ttu-id="6ce90-147">描述</span><span class="sxs-lookup"><span data-stu-id="6ce90-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ce90-148">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="6ce90-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="6ce90-149">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="6ce90-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ce90-150">備註</span><span class="sxs-lookup"><span data-stu-id="6ce90-150">Remarks</span></span>  
 <span data-ttu-id="6ce90-151">這個項目主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="6ce90-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="6ce90-152">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="6ce90-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce90-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ce90-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="6ce90-154">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6ce90-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6ce90-155">繫結</span><span class="sxs-lookup"><span data-stu-id="6ce90-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6ce90-156">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6ce90-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6ce90-157">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6ce90-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6ce90-158">\<binding></span><span class="sxs-lookup"><span data-stu-id="6ce90-158">\<binding></span></span>](../../../misc/binding.md)
