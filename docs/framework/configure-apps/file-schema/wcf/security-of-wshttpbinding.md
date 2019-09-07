---
title: <security> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f7a4ef98637a7c966665fdd02ad26929bd4ba6ac
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399719"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="a1c76-102">\<wsHttpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="a1c76-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="a1c76-103">表示[ \<wsHttpBinding >](wshttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="a1c76-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="a1c76-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a1c76-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a1c76-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a1c76-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a1c76-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a1c76-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a1c76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a1c76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="a1c76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="a1c76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a1c76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="a1c76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1c76-110">語法</span><span class="sxs-lookup"><span data-stu-id="a1c76-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1c76-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a1c76-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a1c76-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a1c76-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1c76-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a1c76-113">Attributes</span></span>  
  
|<span data-ttu-id="a1c76-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a1c76-114">Attribute</span></span>|<span data-ttu-id="a1c76-115">說明</span><span class="sxs-lookup"><span data-stu-id="a1c76-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1c76-116">模式</span><span class="sxs-lookup"><span data-stu-id="a1c76-116">mode</span></span>|<span data-ttu-id="a1c76-117">選擇性.</span><span class="sxs-lookup"><span data-stu-id="a1c76-117">-   Optional.</span></span> <span data-ttu-id="a1c76-118">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="a1c76-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a1c76-119">預設為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="a1c76-119">The default is `Message`.</span></span><br /><span data-ttu-id="a1c76-120">-這個屬性的類型<xref:System.ServiceModel.SecurityMode>為。</span><span class="sxs-lookup"><span data-stu-id="a1c76-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a1c76-121">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="a1c76-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="a1c76-122">值</span><span class="sxs-lookup"><span data-stu-id="a1c76-122">Value</span></span>|<span data-ttu-id="a1c76-123">描述</span><span class="sxs-lookup"><span data-stu-id="a1c76-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a1c76-124">無</span><span class="sxs-lookup"><span data-stu-id="a1c76-124">None</span></span>|<span data-ttu-id="a1c76-125">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="a1c76-125">Security is disabled.</span></span>|  
|<span data-ttu-id="a1c76-126">Transport</span><span class="sxs-lookup"><span data-stu-id="a1c76-126">Transport</span></span>|<span data-ttu-id="a1c76-127">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="a1c76-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="a1c76-128">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="a1c76-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="a1c76-129">用戶端使用 HTTPS 來完全保護訊息，並使用服務的 SSL 憑證來驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="a1c76-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="a1c76-130">用戶端驗證是透過 `ClientCredentials` 屬性</span><span class="sxs-lookup"><span data-stu-id="a1c76-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="a1c76-131">> 的傳輸。 [ \< ](transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a1c76-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="a1c76-132">訊息</span><span class="sxs-lookup"><span data-stu-id="a1c76-132">Message</span></span>|<span data-ttu-id="a1c76-133">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="a1c76-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="a1c76-134">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="a1c76-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="a1c76-135">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及透過 Security.Message 屬性將何種保護層級套用至訊息主體。</span><span class="sxs-lookup"><span data-stu-id="a1c76-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="a1c76-136">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="a1c76-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="a1c76-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a1c76-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="a1c76-138">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="a1c76-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="a1c76-139">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="a1c76-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1c76-140">子元素</span><span class="sxs-lookup"><span data-stu-id="a1c76-140">Child Elements</span></span>  
  
|<span data-ttu-id="a1c76-141">項目</span><span class="sxs-lookup"><span data-stu-id="a1c76-141">Element</span></span>|<span data-ttu-id="a1c76-142">描述</span><span class="sxs-lookup"><span data-stu-id="a1c76-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1c76-143">\<transport></span><span class="sxs-lookup"><span data-stu-id="a1c76-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="a1c76-144">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a1c76-144">Defines the transport security settings.</span></span> <span data-ttu-id="a1c76-145">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="a1c76-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="a1c76-146">\<message></span><span class="sxs-lookup"><span data-stu-id="a1c76-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="a1c76-147">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a1c76-147">Defines the security settings for the message.</span></span> <span data-ttu-id="a1c76-148">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="a1c76-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1c76-149">父項目</span><span class="sxs-lookup"><span data-stu-id="a1c76-149">Parent Elements</span></span>  
  
|<span data-ttu-id="a1c76-150">項目</span><span class="sxs-lookup"><span data-stu-id="a1c76-150">Element</span></span>|<span data-ttu-id="a1c76-151">說明</span><span class="sxs-lookup"><span data-stu-id="a1c76-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1c76-152">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a1c76-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="a1c76-153">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="a1c76-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1c76-154">備註</span><span class="sxs-lookup"><span data-stu-id="a1c76-154">Remarks</span></span>  
 <span data-ttu-id="a1c76-155">WSHttpBinding 類別主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="a1c76-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="a1c76-156">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="a1c76-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c76-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1c76-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="a1c76-158">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a1c76-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a1c76-159">繫結</span><span class="sxs-lookup"><span data-stu-id="a1c76-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a1c76-160">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a1c76-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a1c76-161">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a1c76-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a1c76-162">\<binding></span><span class="sxs-lookup"><span data-stu-id="a1c76-162">\<binding></span></span>](../../../misc/binding.md)
