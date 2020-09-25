---
title: <security> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 6144e5448526d7f2a7c89693f70f71a7f26c4a22
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183659"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="e1015-102">\<security> 的 \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e1015-102">\<security> of \<basicHttpBinding></span></span>

<span data-ttu-id="e1015-103">定義的安全性功能 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e1015-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="e1015-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1015-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1015-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e1015-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e1015-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="e1015-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1015-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e1015-107">Attributes</span></span>  
  
|<span data-ttu-id="e1015-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e1015-108">Attribute</span></span>|<span data-ttu-id="e1015-109">描述</span><span class="sxs-lookup"><span data-stu-id="e1015-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1015-110">mode</span><span class="sxs-lookup"><span data-stu-id="e1015-110">mode</span></span>|<span data-ttu-id="e1015-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e1015-111">Optional.</span></span> <span data-ttu-id="e1015-112">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="e1015-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="e1015-113">預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="e1015-113">The default is `None`.</span></span> <span data-ttu-id="e1015-114">此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="e1015-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e1015-115">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="e1015-115">mode Attribute</span></span>  
  
|<span data-ttu-id="e1015-116">值</span><span class="sxs-lookup"><span data-stu-id="e1015-116">Value</span></span>|<span data-ttu-id="e1015-117">描述</span><span class="sxs-lookup"><span data-stu-id="e1015-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e1015-118">無</span><span class="sxs-lookup"><span data-stu-id="e1015-118">None</span></span>|<span data-ttu-id="e1015-119">-傳輸期間不會保護訊息。</span><span class="sxs-lookup"><span data-stu-id="e1015-119">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="e1015-120">傳輸</span><span class="sxs-lookup"><span data-stu-id="e1015-120">Transport</span></span>|<span data-ttu-id="e1015-121">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="e1015-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="e1015-122">使用 HTTPS 來維護 SOAP 訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="e1015-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="e1015-123">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="e1015-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="e1015-124">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="e1015-124">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="e1015-125">請參閱 [\<transport>](transport-of-basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e1015-125">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="e1015-126">訊息</span><span class="sxs-lookup"><span data-stu-id="e1015-126">Message</span></span>|<span data-ttu-id="e1015-127">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="e1015-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="e1015-128">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="e1015-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="e1015-129">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e1015-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="e1015-130">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="e1015-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="e1015-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e1015-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="e1015-132">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="e1015-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="e1015-133">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="e1015-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="e1015-134">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="e1015-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="e1015-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="e1015-135">TransportCredentialOnly</span></span>|<span data-ttu-id="e1015-136">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="e1015-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="e1015-137">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="e1015-137">It provides http-based client authentication.</span></span> <span data-ttu-id="e1015-138">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="e1015-138">This mode should be used with caution.</span></span> <span data-ttu-id="e1015-139">它應該用於以其他方式提供傳輸安全性的環境中 (例如 IPSec) ，而且只有 WCF 基礎結構會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="e1015-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1015-140">子元素</span><span class="sxs-lookup"><span data-stu-id="e1015-140">Child Elements</span></span>  
  
|<span data-ttu-id="e1015-141">項目</span><span class="sxs-lookup"><span data-stu-id="e1015-141">Element</span></span>|<span data-ttu-id="e1015-142">描述</span><span class="sxs-lookup"><span data-stu-id="e1015-142">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="e1015-143">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e1015-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="e1015-144">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="e1015-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="e1015-145">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e1015-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="e1015-146">這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。</span><span class="sxs-lookup"><span data-stu-id="e1015-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1015-147">父項目</span><span class="sxs-lookup"><span data-stu-id="e1015-147">Parent Elements</span></span>  
  
|<span data-ttu-id="e1015-148">項目</span><span class="sxs-lookup"><span data-stu-id="e1015-148">Element</span></span>|<span data-ttu-id="e1015-149">描述</span><span class="sxs-lookup"><span data-stu-id="e1015-149">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1015-150">繫結</span><span class="sxs-lookup"><span data-stu-id="e1015-150">binding</span></span>|<span data-ttu-id="e1015-151">的繫結項目 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e1015-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1015-152">備註</span><span class="sxs-lookup"><span data-stu-id="e1015-152">Remarks</span></span>  

 <span data-ttu-id="e1015-153">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="e1015-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="e1015-154">這個項目可讓您設定 `basicHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e1015-154">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1015-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1015-155">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="e1015-156">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="e1015-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e1015-157">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="e1015-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="e1015-158">繫結</span><span class="sxs-lookup"><span data-stu-id="e1015-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e1015-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e1015-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e1015-160">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e1015-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
