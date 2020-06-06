---
title: <security> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736487"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="4acf2-102">\<security> 的 \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4acf2-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="4acf2-103">定義的安全性功能 [\<netHttpBinding>](nethttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="4acf2-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="4acf2-104">語法</span><span class="sxs-lookup"><span data-stu-id="4acf2-104">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4acf2-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="4acf2-105">Attributes and elements</span></span>

<span data-ttu-id="4acf2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4acf2-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4acf2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4acf2-107">Attributes</span></span>

|<span data-ttu-id="4acf2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4acf2-108">Attribute</span></span>|<span data-ttu-id="4acf2-109">描述</span><span class="sxs-lookup"><span data-stu-id="4acf2-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="4acf2-110">mode</span><span class="sxs-lookup"><span data-stu-id="4acf2-110">mode</span></span>|<span data-ttu-id="4acf2-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4acf2-111">Optional.</span></span> <span data-ttu-id="4acf2-112">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="4acf2-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="4acf2-113">預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="4acf2-113">The default is `None`.</span></span> <span data-ttu-id="4acf2-114">此屬性的型別為 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="4acf2-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="4acf2-115">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="4acf2-115">mode attribute</span></span>

|<span data-ttu-id="4acf2-116">值</span><span class="sxs-lookup"><span data-stu-id="4acf2-116">Value</span></span>|<span data-ttu-id="4acf2-117">描述</span><span class="sxs-lookup"><span data-stu-id="4acf2-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="4acf2-118">None</span><span class="sxs-lookup"><span data-stu-id="4acf2-118">None</span></span>|<span data-ttu-id="4acf2-119">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="4acf2-119">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="4acf2-120">傳輸</span><span class="sxs-lookup"><span data-stu-id="4acf2-120">Transport</span></span>|<span data-ttu-id="4acf2-121">會使用 HTTPS 傳輸來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="4acf2-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="4acf2-122">使用 HTTPS 來維護 SOAP 訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="4acf2-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="4acf2-123">對用戶端驗證服務時，則是使用服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="4acf2-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="4acf2-124">用戶端會透過提供的 ClientCredentialType 來驗證。</span><span class="sxs-lookup"><span data-stu-id="4acf2-124">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="4acf2-125">訊息</span><span class="sxs-lookup"><span data-stu-id="4acf2-125">Message</span></span>|<span data-ttu-id="4acf2-126">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="4acf2-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4acf2-127">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="4acf2-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="4acf2-128">對於此繫結，系統會要求將伺服器憑證提供給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="4acf2-128">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="4acf2-129">這個繫結唯一有效的 `ClientCredentialType` 是 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="4acf2-129">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="4acf2-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4acf2-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="4acf2-131">完整性、機密性與伺服器驗證都是經由傳輸安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="4acf2-131">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="4acf2-132">用戶端驗證是透過 SOAP 訊息安全性的方式提供。</span><span class="sxs-lookup"><span data-stu-id="4acf2-132">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="4acf2-133">當使用者是透過使用者名稱/密碼進行驗證，且有現有的 HTTP 部署來保護訊息傳輸的安全時，即與此模式有關。</span><span class="sxs-lookup"><span data-stu-id="4acf2-133">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="4acf2-134">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="4acf2-134">TransportCredentialOnly</span></span>|<span data-ttu-id="4acf2-135">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="4acf2-135">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="4acf2-136">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="4acf2-136">It provides http-based client authentication.</span></span> <span data-ttu-id="4acf2-137">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="4acf2-137">This mode should be used with caution.</span></span> <span data-ttu-id="4acf2-138">它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="4acf2-138">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4acf2-139">子元素</span><span class="sxs-lookup"><span data-stu-id="4acf2-139">Child elements</span></span>

|<span data-ttu-id="4acf2-140">元素</span><span class="sxs-lookup"><span data-stu-id="4acf2-140">Element</span></span>|<span data-ttu-id="4acf2-141">描述</span><span class="sxs-lookup"><span data-stu-id="4acf2-141">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="4acf2-142">定義基本 HTTP 服務的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="4acf2-142">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="4acf2-143">這個項目對應於 <xref:System.ServiceModel.HttpTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="4acf2-143">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="4acf2-144">定義基本 HTTP 服務的訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="4acf2-144">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="4acf2-145">這個項目對應於 <xref:System.ServiceModel.BasicHttpMessageSecurity>。</span><span class="sxs-lookup"><span data-stu-id="4acf2-145">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4acf2-146">父元素</span><span class="sxs-lookup"><span data-stu-id="4acf2-146">Parent elements</span></span>

|<span data-ttu-id="4acf2-147">元素</span><span class="sxs-lookup"><span data-stu-id="4acf2-147">Element</span></span>|<span data-ttu-id="4acf2-148">描述</span><span class="sxs-lookup"><span data-stu-id="4acf2-148">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="4acf2-149">繫結</span><span class="sxs-lookup"><span data-stu-id="4acf2-149">binding</span></span>|<span data-ttu-id="4acf2-150">的繫結項目 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="4acf2-150">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="4acf2-151">備註</span><span class="sxs-lookup"><span data-stu-id="4acf2-151">Remarks</span></span>

 <span data-ttu-id="4acf2-152">根據預設，SOAP 訊息並不安全，而且用戶端也尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="4acf2-152">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="4acf2-153">這個項目可讓您設定 `netHttpBinding` 項目的其他安全性設定。</span><span class="sxs-lookup"><span data-stu-id="4acf2-153">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4acf2-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4acf2-154">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="4acf2-155">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="4acf2-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4acf2-156">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="4acf2-156">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="4acf2-157">繫結</span><span class="sxs-lookup"><span data-stu-id="4acf2-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4acf2-158">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="4acf2-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4acf2-159">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="4acf2-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
