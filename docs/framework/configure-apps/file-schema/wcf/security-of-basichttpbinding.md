---
title: <security> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738712"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="9b31c-102">\<basicHttpBinding 的 \<安全性 > ></span><span class="sxs-lookup"><span data-stu-id="9b31c-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="9b31c-103">定義[\<basicHttpBinding >](basichttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="9b31c-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="9b31c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b31c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9b31c-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9b31c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9b31c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="9b31c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9b31c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="9b31c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="9b31c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="9b31c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="9b31c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="9b31c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b31c-110">語法</span><span class="sxs-lookup"><span data-stu-id="9b31c-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b31c-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9b31c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9b31c-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="9b31c-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b31c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9b31c-113">Attributes</span></span>  
  
|<span data-ttu-id="9b31c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="9b31c-114">Attribute</span></span>|<span data-ttu-id="9b31c-115">描述</span><span class="sxs-lookup"><span data-stu-id="9b31c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b31c-116">模式</span><span class="sxs-lookup"><span data-stu-id="9b31c-116">mode</span></span>|<span data-ttu-id="9b31c-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="9b31c-117">Optional.</span></span> <span data-ttu-id="9b31c-118">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="9b31c-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="9b31c-119">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="9b31c-119">The default is `None`.</span></span> <span data-ttu-id="9b31c-120">此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="9b31c-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9b31c-121">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="9b31c-121">mode Attribute</span></span>  
  
|<span data-ttu-id="9b31c-122">值</span><span class="sxs-lookup"><span data-stu-id="9b31c-122">Value</span></span>|<span data-ttu-id="9b31c-123">描述</span><span class="sxs-lookup"><span data-stu-id="9b31c-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9b31c-124">None</span><span class="sxs-lookup"><span data-stu-id="9b31c-124">None</span></span>|<span data-ttu-id="9b31c-125">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="9b31c-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="9b31c-126">Transport</span><span class="sxs-lookup"><span data-stu-id="9b31c-126">Transport</span></span>|<span data-ttu-id="9b31c-127">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="9b31c-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="9b31c-128">SOAP 訊息是使用 HTTPS 來保護其安全。</span><span class="sxs-lookup"><span data-stu-id="9b31c-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="9b31c-129">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="9b31c-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="9b31c-130">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="9b31c-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="9b31c-131">請參閱[\<傳輸 >](transport-of-basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="9b31c-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="9b31c-132">訊息</span><span class="sxs-lookup"><span data-stu-id="9b31c-132">Message</span></span>|<span data-ttu-id="9b31c-133">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="9b31c-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="9b31c-134">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="9b31c-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="9b31c-135">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="9b31c-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="9b31c-136">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="9b31c-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="9b31c-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="9b31c-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="9b31c-138">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="9b31c-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="9b31c-139">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="9b31c-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="9b31c-140">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="9b31c-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="9b31c-141">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="9b31c-141">TransportCredentialOnly</span></span>|<span data-ttu-id="9b31c-142">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="9b31c-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="9b31c-143">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="9b31c-143">It provides http-based client authentication.</span></span> <span data-ttu-id="9b31c-144">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="9b31c-144">This mode should be used with caution.</span></span> <span data-ttu-id="9b31c-145">它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="9b31c-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b31c-146">子項目</span><span class="sxs-lookup"><span data-stu-id="9b31c-146">Child Elements</span></span>  
  
|<span data-ttu-id="9b31c-147">項目</span><span class="sxs-lookup"><span data-stu-id="9b31c-147">Element</span></span>|<span data-ttu-id="9b31c-148">描述</span><span class="sxs-lookup"><span data-stu-id="9b31c-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b31c-149">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="9b31c-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="9b31c-150">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9b31c-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="9b31c-151">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="9b31c-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="9b31c-152">\<message ></span><span class="sxs-lookup"><span data-stu-id="9b31c-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="9b31c-153">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9b31c-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="9b31c-154">這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。</span><span class="sxs-lookup"><span data-stu-id="9b31c-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b31c-155">父項目</span><span class="sxs-lookup"><span data-stu-id="9b31c-155">Parent Elements</span></span>  
  
|<span data-ttu-id="9b31c-156">項目</span><span class="sxs-lookup"><span data-stu-id="9b31c-156">Element</span></span>|<span data-ttu-id="9b31c-157">描述</span><span class="sxs-lookup"><span data-stu-id="9b31c-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b31c-158">繫結</span><span class="sxs-lookup"><span data-stu-id="9b31c-158">binding</span></span>|<span data-ttu-id="9b31c-159">[\<basicHttpBinding >](basichttpbinding.md)的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="9b31c-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b31c-160">備註</span><span class="sxs-lookup"><span data-stu-id="9b31c-160">Remarks</span></span>  
 <span data-ttu-id="9b31c-161">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="9b31c-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="9b31c-162">這個項目可讓您設定 `basicHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9b31c-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b31c-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b31c-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="9b31c-164">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="9b31c-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9b31c-165">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="9b31c-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="9b31c-166">繫結</span><span class="sxs-lookup"><span data-stu-id="9b31c-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9b31c-167">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="9b31c-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9b31c-168">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="9b31c-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9b31c-169">\<binding ></span><span class="sxs-lookup"><span data-stu-id="9b31c-169">\<binding></span></span>](bindings.md)
