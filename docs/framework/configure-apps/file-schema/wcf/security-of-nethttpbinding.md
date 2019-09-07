---
title: <security> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 890cee3271c410a921b3a88f78d0705ba8718252
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399849"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="66482-102">\<netHttpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="66482-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="66482-103">定義[ \<netHttpBinding >](nethttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="66482-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="66482-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="66482-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="66482-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="66482-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="66482-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="66482-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="66482-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="66482-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="66482-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="66482-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="66482-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="66482-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="66482-110">語法</span><span class="sxs-lookup"><span data-stu-id="66482-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="66482-111">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="66482-111">Attributes and elements</span></span>

<span data-ttu-id="66482-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="66482-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="66482-113">屬性</span><span class="sxs-lookup"><span data-stu-id="66482-113">Attributes</span></span>

|<span data-ttu-id="66482-114">屬性</span><span class="sxs-lookup"><span data-stu-id="66482-114">Attribute</span></span>|<span data-ttu-id="66482-115">描述</span><span class="sxs-lookup"><span data-stu-id="66482-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="66482-116">模式</span><span class="sxs-lookup"><span data-stu-id="66482-116">mode</span></span>|<span data-ttu-id="66482-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="66482-117">Optional.</span></span> <span data-ttu-id="66482-118">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="66482-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="66482-119">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="66482-119">The default is `None`.</span></span> <span data-ttu-id="66482-120">此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="66482-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="66482-121">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="66482-121">mode attribute</span></span>

|<span data-ttu-id="66482-122">值</span><span class="sxs-lookup"><span data-stu-id="66482-122">Value</span></span>|<span data-ttu-id="66482-123">描述</span><span class="sxs-lookup"><span data-stu-id="66482-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="66482-124">無</span><span class="sxs-lookup"><span data-stu-id="66482-124">None</span></span>|<span data-ttu-id="66482-125">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="66482-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="66482-126">Transport</span><span class="sxs-lookup"><span data-stu-id="66482-126">Transport</span></span>|<span data-ttu-id="66482-127">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="66482-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="66482-128">SOAP 訊息是使用 HTTPS 來保護其安全。</span><span class="sxs-lookup"><span data-stu-id="66482-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="66482-129">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="66482-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="66482-130">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="66482-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="66482-131">訊息</span><span class="sxs-lookup"><span data-stu-id="66482-131">Message</span></span>|<span data-ttu-id="66482-132">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="66482-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="66482-133">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="66482-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="66482-134">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="66482-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="66482-135">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="66482-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="66482-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="66482-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="66482-137">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="66482-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="66482-138">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="66482-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="66482-139">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="66482-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="66482-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="66482-140">TransportCredentialOnly</span></span>|<span data-ttu-id="66482-141">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="66482-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="66482-142">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="66482-142">It provides http-based client authentication.</span></span> <span data-ttu-id="66482-143">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="66482-143">This mode should be used with caution.</span></span> <span data-ttu-id="66482-144">它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="66482-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="66482-145">子元素</span><span class="sxs-lookup"><span data-stu-id="66482-145">Child elements</span></span>

|<span data-ttu-id="66482-146">項目</span><span class="sxs-lookup"><span data-stu-id="66482-146">Element</span></span>|<span data-ttu-id="66482-147">描述</span><span class="sxs-lookup"><span data-stu-id="66482-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66482-148">\<transport></span><span class="sxs-lookup"><span data-stu-id="66482-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="66482-149">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="66482-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="66482-150">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="66482-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="66482-151">\<message></span><span class="sxs-lookup"><span data-stu-id="66482-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="66482-152">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="66482-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="66482-153">這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。</span><span class="sxs-lookup"><span data-stu-id="66482-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="66482-154">父元素</span><span class="sxs-lookup"><span data-stu-id="66482-154">Parent elements</span></span>

|<span data-ttu-id="66482-155">元素</span><span class="sxs-lookup"><span data-stu-id="66482-155">Element</span></span>|<span data-ttu-id="66482-156">說明</span><span class="sxs-lookup"><span data-stu-id="66482-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="66482-157">繫結</span><span class="sxs-lookup"><span data-stu-id="66482-157">binding</span></span>|<span data-ttu-id="66482-158">BasicHttpBinding > 的 binding 元素。 [ \< ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="66482-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="66482-159">備註</span><span class="sxs-lookup"><span data-stu-id="66482-159">Remarks</span></span>

 <span data-ttu-id="66482-160">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="66482-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="66482-161">這個項目可讓您設定 `netHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="66482-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="66482-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66482-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="66482-163">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="66482-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="66482-164">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="66482-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="66482-165">繫結</span><span class="sxs-lookup"><span data-stu-id="66482-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="66482-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="66482-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="66482-167">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="66482-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="66482-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="66482-168">\<binding></span></span>](../../../misc/binding.md)
