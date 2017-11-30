---
title: "&lt;netHttpBinding 的 &gt;security&lt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63d65ea50babd0cd4aa7ee92cdd6d2b281dcbc26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="46607-102">&lt;netHttpBinding 的 &gt;security&lt;</span><span class="sxs-lookup"><span data-stu-id="46607-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="46607-103">定義的安全性功能[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="46607-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="46607-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="46607-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="46607-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="46607-105">\<bindings></span></span>  
<span data-ttu-id="46607-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="46607-106">\<netHttpBinding></span></span>  
<span data-ttu-id="46607-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="46607-107">\<binding></span></span>  
<span data-ttu-id="46607-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="46607-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46607-109">語法</span><span class="sxs-lookup"><span data-stu-id="46607-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46607-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46607-110">Attributes and Elements</span></span>  
 <span data-ttu-id="46607-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="46607-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46607-112">屬性</span><span class="sxs-lookup"><span data-stu-id="46607-112">Attributes</span></span>  
  
|<span data-ttu-id="46607-113">屬性</span><span class="sxs-lookup"><span data-stu-id="46607-113">Attribute</span></span>|<span data-ttu-id="46607-114">描述</span><span class="sxs-lookup"><span data-stu-id="46607-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46607-115">模式</span><span class="sxs-lookup"><span data-stu-id="46607-115">mode</span></span>|<span data-ttu-id="46607-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="46607-116">Optional.</span></span> <span data-ttu-id="46607-117">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="46607-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="46607-118">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="46607-118">The default is `None`.</span></span> <span data-ttu-id="46607-119">這個屬性是屬於型別<!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`。</span><span class="sxs-lookup"><span data-stu-id="46607-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="46607-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="46607-120">mode Attribute</span></span>  
  
|<span data-ttu-id="46607-121">值</span><span class="sxs-lookup"><span data-stu-id="46607-121">Value</span></span>|<span data-ttu-id="46607-122">描述</span><span class="sxs-lookup"><span data-stu-id="46607-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="46607-123">無</span><span class="sxs-lookup"><span data-stu-id="46607-123">None</span></span>|<span data-ttu-id="46607-124">傳輸期間並未保護訊息數。</span><span class="sxs-lookup"><span data-stu-id="46607-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="46607-125">Transport</span><span class="sxs-lookup"><span data-stu-id="46607-125">Transport</span></span>|<span data-ttu-id="46607-126">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="46607-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="46607-127">SOAP 訊息是使用 HTTPS 來保護其安全。</span><span class="sxs-lookup"><span data-stu-id="46607-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="46607-128">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="46607-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="46607-129">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="46607-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="46607-130">訊息</span><span class="sxs-lookup"><span data-stu-id="46607-130">Message</span></span>|<span data-ttu-id="46607-131">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="46607-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="46607-132">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="46607-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="46607-133">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="46607-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="46607-134">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="46607-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="46607-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="46607-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="46607-136">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="46607-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="46607-137">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="46607-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="46607-138">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="46607-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="46607-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="46607-139">TransportCredentialOnly</span></span>|<span data-ttu-id="46607-140">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="46607-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="46607-141">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="46607-141">It provides http-based client authentication.</span></span> <span data-ttu-id="46607-142">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="46607-142">This mode should be used with caution.</span></span> <span data-ttu-id="46607-143">它應使用在以其他方式 (如 IPSec) 提供傳輸安全性，且 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="46607-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46607-144">子元素</span><span class="sxs-lookup"><span data-stu-id="46607-144">Child Elements</span></span>  
  
|<span data-ttu-id="46607-145">項目</span><span class="sxs-lookup"><span data-stu-id="46607-145">Element</span></span>|<span data-ttu-id="46607-146">說明</span><span class="sxs-lookup"><span data-stu-id="46607-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46607-147">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="46607-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="46607-148">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="46607-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="46607-149">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="46607-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="46607-150">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="46607-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="46607-151">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="46607-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="46607-152">這個項目對應至<!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`。</span><span class="sxs-lookup"><span data-stu-id="46607-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46607-153">父項目</span><span class="sxs-lookup"><span data-stu-id="46607-153">Parent Elements</span></span>  
  
|<span data-ttu-id="46607-154">項目</span><span class="sxs-lookup"><span data-stu-id="46607-154">Element</span></span>|<span data-ttu-id="46607-155">描述</span><span class="sxs-lookup"><span data-stu-id="46607-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46607-156">繫結</span><span class="sxs-lookup"><span data-stu-id="46607-156">binding</span></span>|<span data-ttu-id="46607-157">繫結項目[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="46607-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46607-158">備註</span><span class="sxs-lookup"><span data-stu-id="46607-158">Remarks</span></span>  
 <span data-ttu-id="46607-159">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="46607-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="46607-160">這個項目可讓您設定 `netHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="46607-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46607-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46607-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <span data-ttu-id="46607-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span><span class="sxs-lookup"><span data-stu-id="46607-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span></span>    
 [<span data-ttu-id="46607-163">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="46607-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="46607-164">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="46607-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="46607-165">繫結</span><span class="sxs-lookup"><span data-stu-id="46607-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="46607-166">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="46607-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="46607-167">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="46607-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="46607-168">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="46607-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
