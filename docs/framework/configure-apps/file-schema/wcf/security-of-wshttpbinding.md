---
title: <security> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738576"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="47c73-102">\<security> 的 \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="47c73-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="47c73-103">表示的安全性功能 [\<wsHttpBinding>](wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="47c73-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="47c73-104">語法</span><span class="sxs-lookup"><span data-stu-id="47c73-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47c73-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="47c73-105">Attributes and Elements</span></span>  
 <span data-ttu-id="47c73-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="47c73-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47c73-107">屬性</span><span class="sxs-lookup"><span data-stu-id="47c73-107">Attributes</span></span>  
  
|<span data-ttu-id="47c73-108">屬性</span><span class="sxs-lookup"><span data-stu-id="47c73-108">Attribute</span></span>|<span data-ttu-id="47c73-109">描述</span><span class="sxs-lookup"><span data-stu-id="47c73-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47c73-110">mode</span><span class="sxs-lookup"><span data-stu-id="47c73-110">mode</span></span>|<span data-ttu-id="47c73-111">選擇性.</span><span class="sxs-lookup"><span data-stu-id="47c73-111">-   Optional.</span></span> <span data-ttu-id="47c73-112">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="47c73-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="47c73-113">預設值為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="47c73-113">The default is `Message`.</span></span><br /><span data-ttu-id="47c73-114">-這個屬性的類型為 <xref:System.ServiceModel.SecurityMode> 。</span><span class="sxs-lookup"><span data-stu-id="47c73-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="47c73-115">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="47c73-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="47c73-116">值</span><span class="sxs-lookup"><span data-stu-id="47c73-116">Value</span></span>|<span data-ttu-id="47c73-117">描述</span><span class="sxs-lookup"><span data-stu-id="47c73-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47c73-118">None</span><span class="sxs-lookup"><span data-stu-id="47c73-118">None</span></span>|<span data-ttu-id="47c73-119">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="47c73-119">Security is disabled.</span></span>|  
|<span data-ttu-id="47c73-120">傳輸</span><span class="sxs-lookup"><span data-stu-id="47c73-120">Transport</span></span>|<span data-ttu-id="47c73-121">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="47c73-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="47c73-122">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="47c73-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="47c73-123">用戶端使用 HTTPS 來完全保護訊息，並使用服務的 SSL 憑證來驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="47c73-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="47c73-124">用戶端驗證是透過 `ClientCredentials` 屬性</span><span class="sxs-lookup"><span data-stu-id="47c73-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="47c73-125">的 [\<transport>](transport-of-wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="47c73-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="47c73-126">訊息</span><span class="sxs-lookup"><span data-stu-id="47c73-126">Message</span></span>|<span data-ttu-id="47c73-127">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="47c73-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="47c73-128">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="47c73-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="47c73-129">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及透過 Security.Message 屬性將何種保護層級套用至訊息主體。</span><span class="sxs-lookup"><span data-stu-id="47c73-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="47c73-130">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="47c73-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="47c73-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="47c73-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="47c73-132">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="47c73-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="47c73-133">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="47c73-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47c73-134">子元素</span><span class="sxs-lookup"><span data-stu-id="47c73-134">Child Elements</span></span>  
  
|<span data-ttu-id="47c73-135">元素</span><span class="sxs-lookup"><span data-stu-id="47c73-135">Element</span></span>|<span data-ttu-id="47c73-136">描述</span><span class="sxs-lookup"><span data-stu-id="47c73-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="47c73-137">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="47c73-137">Defines the transport security settings.</span></span> <span data-ttu-id="47c73-138">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="47c73-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="47c73-139">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="47c73-139">Defines the security settings for the message.</span></span> <span data-ttu-id="47c73-140">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="47c73-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47c73-141">父項目</span><span class="sxs-lookup"><span data-stu-id="47c73-141">Parent Elements</span></span>  
  
|<span data-ttu-id="47c73-142">元素</span><span class="sxs-lookup"><span data-stu-id="47c73-142">Element</span></span>|<span data-ttu-id="47c73-143">描述</span><span class="sxs-lookup"><span data-stu-id="47c73-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="47c73-144">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="47c73-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47c73-145">備註</span><span class="sxs-lookup"><span data-stu-id="47c73-145">Remarks</span></span>  
 <span data-ttu-id="47c73-146">WSHttpBinding 類別主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="47c73-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="47c73-147">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="47c73-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c73-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c73-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="47c73-149">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="47c73-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="47c73-150">繫結</span><span class="sxs-lookup"><span data-stu-id="47c73-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="47c73-151">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="47c73-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="47c73-152">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="47c73-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
