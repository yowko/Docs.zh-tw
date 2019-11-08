---
title: <security> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736487"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="a1755-102">\<netHttpBinding 的 \<安全性 > ></span><span class="sxs-lookup"><span data-stu-id="a1755-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="a1755-103">定義[\<netHttpBinding >](nethttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="a1755-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="a1755-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a1755-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a1755-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a1755-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a1755-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="a1755-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a1755-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a1755-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="a1755-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="a1755-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a1755-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="a1755-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a1755-110">語法</span><span class="sxs-lookup"><span data-stu-id="a1755-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1755-111">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a1755-111">Attributes and elements</span></span>

<span data-ttu-id="a1755-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a1755-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1755-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a1755-113">Attributes</span></span>

|<span data-ttu-id="a1755-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a1755-114">Attribute</span></span>|<span data-ttu-id="a1755-115">描述</span><span class="sxs-lookup"><span data-stu-id="a1755-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a1755-116">模式</span><span class="sxs-lookup"><span data-stu-id="a1755-116">mode</span></span>|<span data-ttu-id="a1755-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a1755-117">Optional.</span></span> <span data-ttu-id="a1755-118">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="a1755-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="a1755-119">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="a1755-119">The default is `None`.</span></span> <span data-ttu-id="a1755-120">此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="a1755-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="a1755-121">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="a1755-121">mode attribute</span></span>

|<span data-ttu-id="a1755-122">值</span><span class="sxs-lookup"><span data-stu-id="a1755-122">Value</span></span>|<span data-ttu-id="a1755-123">描述</span><span class="sxs-lookup"><span data-stu-id="a1755-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="a1755-124">None</span><span class="sxs-lookup"><span data-stu-id="a1755-124">None</span></span>|<span data-ttu-id="a1755-125">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="a1755-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="a1755-126">Transport</span><span class="sxs-lookup"><span data-stu-id="a1755-126">Transport</span></span>|<span data-ttu-id="a1755-127">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="a1755-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="a1755-128">SOAP 訊息是使用 HTTPS 來保護其安全。</span><span class="sxs-lookup"><span data-stu-id="a1755-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="a1755-129">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a1755-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="a1755-130">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="a1755-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="a1755-131">訊息</span><span class="sxs-lookup"><span data-stu-id="a1755-131">Message</span></span>|<span data-ttu-id="a1755-132">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="a1755-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="a1755-133">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="a1755-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="a1755-134">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="a1755-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="a1755-135">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="a1755-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="a1755-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a1755-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="a1755-137">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="a1755-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="a1755-138">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="a1755-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="a1755-139">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="a1755-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="a1755-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="a1755-140">TransportCredentialOnly</span></span>|<span data-ttu-id="a1755-141">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="a1755-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="a1755-142">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="a1755-142">It provides http-based client authentication.</span></span> <span data-ttu-id="a1755-143">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="a1755-143">This mode should be used with caution.</span></span> <span data-ttu-id="a1755-144">它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="a1755-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a1755-145">子元素</span><span class="sxs-lookup"><span data-stu-id="a1755-145">Child elements</span></span>

|<span data-ttu-id="a1755-146">項目</span><span class="sxs-lookup"><span data-stu-id="a1755-146">Element</span></span>|<span data-ttu-id="a1755-147">描述</span><span class="sxs-lookup"><span data-stu-id="a1755-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1755-148">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="a1755-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="a1755-149">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a1755-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="a1755-150">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="a1755-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="a1755-151">\<message ></span><span class="sxs-lookup"><span data-stu-id="a1755-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="a1755-152">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a1755-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="a1755-153">這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。</span><span class="sxs-lookup"><span data-stu-id="a1755-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1755-154">父元素</span><span class="sxs-lookup"><span data-stu-id="a1755-154">Parent elements</span></span>

|<span data-ttu-id="a1755-155">項目</span><span class="sxs-lookup"><span data-stu-id="a1755-155">Element</span></span>|<span data-ttu-id="a1755-156">描述</span><span class="sxs-lookup"><span data-stu-id="a1755-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="a1755-157">繫結</span><span class="sxs-lookup"><span data-stu-id="a1755-157">binding</span></span>|<span data-ttu-id="a1755-158">[\<basicHttpBinding >](basichttpbinding.md)的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="a1755-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1755-159">備註</span><span class="sxs-lookup"><span data-stu-id="a1755-159">Remarks</span></span>

 <span data-ttu-id="a1755-160">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="a1755-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="a1755-161">這個項目可讓您設定 `netHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a1755-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1755-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1755-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="a1755-163">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a1755-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a1755-164">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="a1755-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="a1755-165">繫結</span><span class="sxs-lookup"><span data-stu-id="a1755-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a1755-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a1755-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a1755-167">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a1755-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a1755-168">\<binding ></span><span class="sxs-lookup"><span data-stu-id="a1755-168">\<binding></span></span>](bindings.md)
