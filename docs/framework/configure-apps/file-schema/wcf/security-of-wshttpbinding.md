---
title: '&lt;wsHttpBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 2260a64b53f2ff2ace11f78c392ffc0a69c187bd
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145623"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="35164-102">&lt;wsHttpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="35164-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="35164-103">代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="35164-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="35164-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35164-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="35164-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="35164-105">\<bindings></span></span>  
<span data-ttu-id="35164-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="35164-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="35164-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="35164-107">\<binding></span></span>  
<span data-ttu-id="35164-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="35164-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35164-109">語法</span><span class="sxs-lookup"><span data-stu-id="35164-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35164-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="35164-110">Attributes and Elements</span></span>  
 <span data-ttu-id="35164-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="35164-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35164-112">屬性</span><span class="sxs-lookup"><span data-stu-id="35164-112">Attributes</span></span>  
  
|<span data-ttu-id="35164-113">屬性</span><span class="sxs-lookup"><span data-stu-id="35164-113">Attribute</span></span>|<span data-ttu-id="35164-114">描述</span><span class="sxs-lookup"><span data-stu-id="35164-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35164-115">模式</span><span class="sxs-lookup"><span data-stu-id="35164-115">mode</span></span>|<span data-ttu-id="35164-116">-選擇性。</span><span class="sxs-lookup"><span data-stu-id="35164-116">-   Optional.</span></span> <span data-ttu-id="35164-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="35164-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="35164-118">預設為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="35164-118">The default is `Message`.</span></span><br /><span data-ttu-id="35164-119">-此屬性為類型<xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="35164-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="35164-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="35164-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="35164-121">值</span><span class="sxs-lookup"><span data-stu-id="35164-121">Value</span></span>|<span data-ttu-id="35164-122">描述</span><span class="sxs-lookup"><span data-stu-id="35164-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35164-123">無</span><span class="sxs-lookup"><span data-stu-id="35164-123">None</span></span>|<span data-ttu-id="35164-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="35164-124">Security is disabled.</span></span>|  
|<span data-ttu-id="35164-125">Transport</span><span class="sxs-lookup"><span data-stu-id="35164-125">Transport</span></span>|<span data-ttu-id="35164-126">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="35164-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="35164-127">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="35164-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="35164-128">用戶端使用 HTTPS 來完全保護訊息，並使用服務的 SSL 憑證來驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="35164-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="35164-129">用戶端驗證是透過 `ClientCredentials` 屬性</span><span class="sxs-lookup"><span data-stu-id="35164-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="35164-130">[\<傳輸 >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="35164-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="35164-131">訊息</span><span class="sxs-lookup"><span data-stu-id="35164-131">Message</span></span>|<span data-ttu-id="35164-132">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="35164-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="35164-133">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="35164-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="35164-134">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及透過 Security.Message 屬性將何種保護層級套用至訊息主體。</span><span class="sxs-lookup"><span data-stu-id="35164-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="35164-135">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="35164-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="35164-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="35164-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="35164-137">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="35164-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="35164-138">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="35164-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35164-139">子元素</span><span class="sxs-lookup"><span data-stu-id="35164-139">Child Elements</span></span>  
  
|<span data-ttu-id="35164-140">項目</span><span class="sxs-lookup"><span data-stu-id="35164-140">Element</span></span>|<span data-ttu-id="35164-141">描述</span><span class="sxs-lookup"><span data-stu-id="35164-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35164-142">\<transport></span><span class="sxs-lookup"><span data-stu-id="35164-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="35164-143">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="35164-143">Defines the transport security settings.</span></span> <span data-ttu-id="35164-144">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="35164-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="35164-145">\<message></span><span class="sxs-lookup"><span data-stu-id="35164-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="35164-146">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="35164-146">Defines the security settings for the message.</span></span> <span data-ttu-id="35164-147">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="35164-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35164-148">父項目</span><span class="sxs-lookup"><span data-stu-id="35164-148">Parent Elements</span></span>  
  
|<span data-ttu-id="35164-149">項目</span><span class="sxs-lookup"><span data-stu-id="35164-149">Element</span></span>|<span data-ttu-id="35164-150">描述</span><span class="sxs-lookup"><span data-stu-id="35164-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35164-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="35164-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="35164-152">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="35164-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35164-153">備註</span><span class="sxs-lookup"><span data-stu-id="35164-153">Remarks</span></span>  
 <span data-ttu-id="35164-154">WSHttpBinding 類別主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="35164-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="35164-155">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="35164-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35164-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35164-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="35164-157">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="35164-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="35164-158">繫結</span><span class="sxs-lookup"><span data-stu-id="35164-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="35164-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="35164-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="35164-160">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="35164-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="35164-161">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="35164-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
