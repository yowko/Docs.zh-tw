---
title: '&lt;basicHttpBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2adb5736cca59d42ab3c62d61513bbfd80a4be04
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749444"
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="6c47a-102">&lt;basicHttpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="6c47a-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="6c47a-103">定義的安全性功能[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="6c47a-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="6c47a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6c47a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c47a-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6c47a-105">\<bindings></span></span>  
<span data-ttu-id="6c47a-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6c47a-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="6c47a-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6c47a-107">\<binding></span></span>  
<span data-ttu-id="6c47a-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6c47a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c47a-109">語法</span><span class="sxs-lookup"><span data-stu-id="6c47a-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c47a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6c47a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6c47a-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6c47a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c47a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6c47a-112">Attributes</span></span>  
  
|<span data-ttu-id="6c47a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6c47a-113">Attribute</span></span>|<span data-ttu-id="6c47a-114">描述</span><span class="sxs-lookup"><span data-stu-id="6c47a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c47a-115">模式</span><span class="sxs-lookup"><span data-stu-id="6c47a-115">mode</span></span>|<span data-ttu-id="6c47a-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="6c47a-116">Optional.</span></span> <span data-ttu-id="6c47a-117">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="6c47a-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="6c47a-118">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="6c47a-118">The default is `None`.</span></span> <span data-ttu-id="6c47a-119">此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="6c47a-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6c47a-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="6c47a-120">mode Attribute</span></span>  
  
|<span data-ttu-id="6c47a-121">值</span><span class="sxs-lookup"><span data-stu-id="6c47a-121">Value</span></span>|<span data-ttu-id="6c47a-122">描述</span><span class="sxs-lookup"><span data-stu-id="6c47a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6c47a-123">無</span><span class="sxs-lookup"><span data-stu-id="6c47a-123">None</span></span>|<span data-ttu-id="6c47a-124">訊息在傳輸期間並未受到保護。</span><span class="sxs-lookup"><span data-stu-id="6c47a-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="6c47a-125">Transport</span><span class="sxs-lookup"><span data-stu-id="6c47a-125">Transport</span></span>|<span data-ttu-id="6c47a-126">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6c47a-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="6c47a-127">SOAP 訊息是使用 HTTPS 來保護其安全。</span><span class="sxs-lookup"><span data-stu-id="6c47a-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="6c47a-128">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="6c47a-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="6c47a-129">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="6c47a-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="6c47a-130">請參閱[\<傳輸 >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="6c47a-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="6c47a-131">訊息</span><span class="sxs-lookup"><span data-stu-id="6c47a-131">Message</span></span>|<span data-ttu-id="6c47a-132">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6c47a-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6c47a-133">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="6c47a-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6c47a-134">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="6c47a-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="6c47a-135">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="6c47a-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="6c47a-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6c47a-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="6c47a-137">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="6c47a-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="6c47a-138">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="6c47a-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="6c47a-139">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="6c47a-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="6c47a-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="6c47a-140">TransportCredentialOnly</span></span>|<span data-ttu-id="6c47a-141">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="6c47a-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="6c47a-142">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="6c47a-142">It provides http-based client authentication.</span></span> <span data-ttu-id="6c47a-143">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="6c47a-143">This mode should be used with caution.</span></span> <span data-ttu-id="6c47a-144">它應該用於提供的環境中以其他方式 （例如 IPSec) 提供傳輸安全性，且只有用戶端驗證是由 WCF 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="6c47a-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c47a-145">子元素</span><span class="sxs-lookup"><span data-stu-id="6c47a-145">Child Elements</span></span>  
  
|<span data-ttu-id="6c47a-146">項目</span><span class="sxs-lookup"><span data-stu-id="6c47a-146">Element</span></span>|<span data-ttu-id="6c47a-147">描述</span><span class="sxs-lookup"><span data-stu-id="6c47a-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c47a-148">\<transport></span><span class="sxs-lookup"><span data-stu-id="6c47a-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="6c47a-149">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6c47a-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="6c47a-150">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="6c47a-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="6c47a-151">\<message></span><span class="sxs-lookup"><span data-stu-id="6c47a-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="6c47a-152">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6c47a-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="6c47a-153">這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。</span><span class="sxs-lookup"><span data-stu-id="6c47a-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c47a-154">父項目</span><span class="sxs-lookup"><span data-stu-id="6c47a-154">Parent Elements</span></span>  
  
|<span data-ttu-id="6c47a-155">項目</span><span class="sxs-lookup"><span data-stu-id="6c47a-155">Element</span></span>|<span data-ttu-id="6c47a-156">描述</span><span class="sxs-lookup"><span data-stu-id="6c47a-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c47a-157">繫結</span><span class="sxs-lookup"><span data-stu-id="6c47a-157">binding</span></span>|<span data-ttu-id="6c47a-158">繫結項目[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="6c47a-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c47a-159">備註</span><span class="sxs-lookup"><span data-stu-id="6c47a-159">Remarks</span></span>  
 <span data-ttu-id="6c47a-160">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="6c47a-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="6c47a-161">這個項目可讓您設定 `basicHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6c47a-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c47a-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c47a-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="6c47a-163">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6c47a-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6c47a-164">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="6c47a-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="6c47a-165">繫結</span><span class="sxs-lookup"><span data-stu-id="6c47a-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6c47a-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6c47a-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6c47a-167">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="6c47a-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6c47a-168">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6c47a-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
