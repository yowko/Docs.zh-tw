---
title: <security> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: f2750036aa4d3fbe41062ad041e50ff3a4be32b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283958"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="32b0b-102">\<安全性 > 的\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="32b0b-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="32b0b-103">定義的安全性功能[ \<basicHttpBinding >](basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0b-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>

<span data-ttu-id="32b0b-104">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="32b0b-104">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="32b0b-105">\<bindings>\\</span><span class="sxs-lookup"><span data-stu-id="32b0b-105">\<bindings>\\</span></span>
<span data-ttu-id="32b0b-106">\<netHttpBinding>\\</span><span class="sxs-lookup"><span data-stu-id="32b0b-106">\<netHttpBinding>\\</span></span>
<span data-ttu-id="32b0b-107">\<binding>\\</span><span class="sxs-lookup"><span data-stu-id="32b0b-107">\<binding>\\</span></span>
<span data-ttu-id="32b0b-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="32b0b-108">\<security></span></span>

## <a name="syntax"></a><span data-ttu-id="32b0b-109">語法</span><span class="sxs-lookup"><span data-stu-id="32b0b-109">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32b0b-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="32b0b-110">Attributes and elements</span></span>

<span data-ttu-id="32b0b-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="32b0b-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="32b0b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="32b0b-112">Attributes</span></span>

|<span data-ttu-id="32b0b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="32b0b-113">Attribute</span></span>|<span data-ttu-id="32b0b-114">描述</span><span class="sxs-lookup"><span data-stu-id="32b0b-114">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="32b0b-115">模式</span><span class="sxs-lookup"><span data-stu-id="32b0b-115">mode</span></span>|<span data-ttu-id="32b0b-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="32b0b-116">Optional.</span></span> <span data-ttu-id="32b0b-117">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="32b0b-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="32b0b-118">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="32b0b-118">The default is `None`.</span></span> <span data-ttu-id="32b0b-119">此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="32b0b-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="32b0b-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="32b0b-120">mode attribute</span></span>

|<span data-ttu-id="32b0b-121">值</span><span class="sxs-lookup"><span data-stu-id="32b0b-121">Value</span></span>|<span data-ttu-id="32b0b-122">描述</span><span class="sxs-lookup"><span data-stu-id="32b0b-122">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="32b0b-123">無</span><span class="sxs-lookup"><span data-stu-id="32b0b-123">None</span></span>|<span data-ttu-id="32b0b-124">訊息在傳輸期間並未受到保護。</span><span class="sxs-lookup"><span data-stu-id="32b0b-124">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="32b0b-125">Transport</span><span class="sxs-lookup"><span data-stu-id="32b0b-125">Transport</span></span>|<span data-ttu-id="32b0b-126">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="32b0b-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="32b0b-127">SOAP 訊息是使用 HTTPS 來保護其安全。</span><span class="sxs-lookup"><span data-stu-id="32b0b-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="32b0b-128">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="32b0b-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="32b0b-129">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="32b0b-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="32b0b-130">訊息</span><span class="sxs-lookup"><span data-stu-id="32b0b-130">Message</span></span>|<span data-ttu-id="32b0b-131">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="32b0b-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="32b0b-132">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="32b0b-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="32b0b-133">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="32b0b-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="32b0b-134">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="32b0b-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="32b0b-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="32b0b-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="32b0b-136">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="32b0b-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="32b0b-137">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="32b0b-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="32b0b-138">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="32b0b-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="32b0b-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="32b0b-139">TransportCredentialOnly</span></span>|<span data-ttu-id="32b0b-140">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="32b0b-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="32b0b-141">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="32b0b-141">It provides http-based client authentication.</span></span> <span data-ttu-id="32b0b-142">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="32b0b-142">This mode should be used with caution.</span></span> <span data-ttu-id="32b0b-143">它應該用於提供的環境中以其他方式 （例如 IPSec) 提供傳輸安全性，且只有用戶端驗證是由 WCF 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="32b0b-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="32b0b-144">子元素</span><span class="sxs-lookup"><span data-stu-id="32b0b-144">Child elements</span></span>

|<span data-ttu-id="32b0b-145">項目</span><span class="sxs-lookup"><span data-stu-id="32b0b-145">Element</span></span>|<span data-ttu-id="32b0b-146">描述</span><span class="sxs-lookup"><span data-stu-id="32b0b-146">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32b0b-147">\<transport></span><span class="sxs-lookup"><span data-stu-id="32b0b-147">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="32b0b-148">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="32b0b-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="32b0b-149">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="32b0b-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="32b0b-150">\<message></span><span class="sxs-lookup"><span data-stu-id="32b0b-150">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="32b0b-151">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="32b0b-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="32b0b-152">這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。</span><span class="sxs-lookup"><span data-stu-id="32b0b-152">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="32b0b-153">父元素</span><span class="sxs-lookup"><span data-stu-id="32b0b-153">Parent elements</span></span>

|<span data-ttu-id="32b0b-154">元素</span><span class="sxs-lookup"><span data-stu-id="32b0b-154">Element</span></span>|<span data-ttu-id="32b0b-155">描述</span><span class="sxs-lookup"><span data-stu-id="32b0b-155">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="32b0b-156">繫結</span><span class="sxs-lookup"><span data-stu-id="32b0b-156">binding</span></span>|<span data-ttu-id="32b0b-157">繫結項目[ \<basicHttpBinding >](basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0b-157">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="32b0b-158">備註</span><span class="sxs-lookup"><span data-stu-id="32b0b-158">Remarks</span></span>

 <span data-ttu-id="32b0b-159">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="32b0b-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="32b0b-160">這個項目可讓您設定 `netHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="32b0b-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="32b0b-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32b0b-161">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="32b0b-162">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="32b0b-162">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="32b0b-163">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="32b0b-163">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="32b0b-164">繫結</span><span class="sxs-lookup"><span data-stu-id="32b0b-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="32b0b-165">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="32b0b-165">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="32b0b-166">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="32b0b-166">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="32b0b-167">\<binding></span><span class="sxs-lookup"><span data-stu-id="32b0b-167">\<binding></span></span>](../../../misc/binding.md)
