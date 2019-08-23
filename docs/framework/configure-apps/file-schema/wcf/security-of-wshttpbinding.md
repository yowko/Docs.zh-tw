---
title: <security> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: e627a63221d0013c89495d7ff81e02047a03df89
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936513"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="6de2a-102">\<wsHttpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6de2a-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="6de2a-103">表示[ \<wsHttpBinding >](wshttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6de2a-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="6de2a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6de2a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6de2a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6de2a-105">\<bindings></span></span>  
<span data-ttu-id="6de2a-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6de2a-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="6de2a-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="6de2a-107">\<binding></span></span>  
<span data-ttu-id="6de2a-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6de2a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de2a-109">語法</span><span class="sxs-lookup"><span data-stu-id="6de2a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6de2a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6de2a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6de2a-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6de2a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6de2a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6de2a-112">Attributes</span></span>  
  
|<span data-ttu-id="6de2a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6de2a-113">Attribute</span></span>|<span data-ttu-id="6de2a-114">描述</span><span class="sxs-lookup"><span data-stu-id="6de2a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6de2a-115">模式</span><span class="sxs-lookup"><span data-stu-id="6de2a-115">mode</span></span>|<span data-ttu-id="6de2a-116">選擇性.</span><span class="sxs-lookup"><span data-stu-id="6de2a-116">-   Optional.</span></span> <span data-ttu-id="6de2a-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="6de2a-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6de2a-118">預設為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="6de2a-118">The default is `Message`.</span></span><br /><span data-ttu-id="6de2a-119">-這個屬性的類型<xref:System.ServiceModel.SecurityMode>為。</span><span class="sxs-lookup"><span data-stu-id="6de2a-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6de2a-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="6de2a-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6de2a-121">值</span><span class="sxs-lookup"><span data-stu-id="6de2a-121">Value</span></span>|<span data-ttu-id="6de2a-122">描述</span><span class="sxs-lookup"><span data-stu-id="6de2a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6de2a-123">無</span><span class="sxs-lookup"><span data-stu-id="6de2a-123">None</span></span>|<span data-ttu-id="6de2a-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="6de2a-124">Security is disabled.</span></span>|  
|<span data-ttu-id="6de2a-125">Transport</span><span class="sxs-lookup"><span data-stu-id="6de2a-125">Transport</span></span>|<span data-ttu-id="6de2a-126">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6de2a-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="6de2a-127">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="6de2a-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="6de2a-128">用戶端使用 HTTPS 來完全保護訊息，並使用服務的 SSL 憑證來驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="6de2a-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6de2a-129">用戶端驗證是透過 `ClientCredentials` 屬性</span><span class="sxs-lookup"><span data-stu-id="6de2a-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="6de2a-130">> 的傳輸。 [ \< ](transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6de2a-130">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="6de2a-131">訊息</span><span class="sxs-lookup"><span data-stu-id="6de2a-131">Message</span></span>|<span data-ttu-id="6de2a-132">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6de2a-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6de2a-133">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="6de2a-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="6de2a-134">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及透過 Security.Message 屬性將何種保護層級套用至訊息主體。</span><span class="sxs-lookup"><span data-stu-id="6de2a-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="6de2a-135">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="6de2a-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="6de2a-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6de2a-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="6de2a-137">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="6de2a-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="6de2a-138">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="6de2a-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6de2a-139">子元素</span><span class="sxs-lookup"><span data-stu-id="6de2a-139">Child Elements</span></span>  
  
|<span data-ttu-id="6de2a-140">項目</span><span class="sxs-lookup"><span data-stu-id="6de2a-140">Element</span></span>|<span data-ttu-id="6de2a-141">說明</span><span class="sxs-lookup"><span data-stu-id="6de2a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6de2a-142">\<transport></span><span class="sxs-lookup"><span data-stu-id="6de2a-142">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="6de2a-143">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6de2a-143">Defines the transport security settings.</span></span> <span data-ttu-id="6de2a-144">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="6de2a-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="6de2a-145">\<message></span><span class="sxs-lookup"><span data-stu-id="6de2a-145">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="6de2a-146">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6de2a-146">Defines the security settings for the message.</span></span> <span data-ttu-id="6de2a-147">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="6de2a-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6de2a-148">父項目</span><span class="sxs-lookup"><span data-stu-id="6de2a-148">Parent Elements</span></span>  
  
|<span data-ttu-id="6de2a-149">項目</span><span class="sxs-lookup"><span data-stu-id="6de2a-149">Element</span></span>|<span data-ttu-id="6de2a-150">描述</span><span class="sxs-lookup"><span data-stu-id="6de2a-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6de2a-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6de2a-151">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="6de2a-152">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="6de2a-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6de2a-153">備註</span><span class="sxs-lookup"><span data-stu-id="6de2a-153">Remarks</span></span>  
 <span data-ttu-id="6de2a-154">WSHttpBinding 類別主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="6de2a-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="6de2a-155">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="6de2a-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de2a-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6de2a-156">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="6de2a-157">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6de2a-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6de2a-158">繫結</span><span class="sxs-lookup"><span data-stu-id="6de2a-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6de2a-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6de2a-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6de2a-160">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6de2a-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6de2a-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="6de2a-161">\<binding></span></span>](../../../misc/binding.md)
