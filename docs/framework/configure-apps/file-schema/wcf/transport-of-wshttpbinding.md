---
title: <transport> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: ea025751020d6d98292f6bc3ecfe9421af0cb793
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788215"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="8673e-102">\<transport> of \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8673e-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="8673e-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8673e-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="8673e-104">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="8673e-104">\<system.serviceModel>\\</span></span>
<span data-ttu-id="8673e-105">\<bindings>\\</span><span class="sxs-lookup"><span data-stu-id="8673e-105">\<bindings>\\</span></span>
<span data-ttu-id="8673e-106">\<wsHttpBinding>\\</span><span class="sxs-lookup"><span data-stu-id="8673e-106">\<wsHttpBinding>\\</span></span>
<span data-ttu-id="8673e-107">\<binding>\\</span><span class="sxs-lookup"><span data-stu-id="8673e-107">\<binding>\\</span></span>
<span data-ttu-id="8673e-108">\<安全性 > \\</span><span class="sxs-lookup"><span data-stu-id="8673e-108">\<security>\\</span></span>
<span data-ttu-id="8673e-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="8673e-109">\<transport></span></span>

## <a name="syntax"></a><span data-ttu-id="8673e-110">語法</span><span class="sxs-lookup"><span data-stu-id="8673e-110">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="8673e-111">類型</span><span class="sxs-lookup"><span data-stu-id="8673e-111">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="8673e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8673e-112">Attributes and Elements</span></span>

<span data-ttu-id="8673e-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8673e-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8673e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="8673e-114">Attributes</span></span>

|<span data-ttu-id="8673e-115">屬性</span><span class="sxs-lookup"><span data-stu-id="8673e-115">Attribute</span></span>|<span data-ttu-id="8673e-116">描述</span><span class="sxs-lookup"><span data-stu-id="8673e-116">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="8673e-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="8673e-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="8673e-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="8673e-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="8673e-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="8673e-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="8673e-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="8673e-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="8673e-121">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="8673e-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="8673e-122">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="8673e-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="8673e-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="8673e-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="8673e-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="8673e-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="8673e-125">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="8673e-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="8673e-126">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="8673e-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="8673e-127">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="8673e-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="8673e-128">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="8673e-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="8673e-129">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="8673e-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="8673e-130">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="8673e-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="8673e-131">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="8673e-131">clientCredentialType Attribute</span></span>

|<span data-ttu-id="8673e-132">值</span><span class="sxs-lookup"><span data-stu-id="8673e-132">Value</span></span>|<span data-ttu-id="8673e-133">描述</span><span class="sxs-lookup"><span data-stu-id="8673e-133">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="8673e-134">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="8673e-134">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="8673e-135">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="8673e-135">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="8673e-136">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="8673e-136">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="8673e-137">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="8673e-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="8673e-138">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="8673e-138">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="8673e-139">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="8673e-139">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="8673e-140">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="8673e-140">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="8673e-141">值</span><span class="sxs-lookup"><span data-stu-id="8673e-141">Value</span></span>|<span data-ttu-id="8673e-142">描述</span><span class="sxs-lookup"><span data-stu-id="8673e-142">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="8673e-143">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="8673e-143">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="8673e-144">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="8673e-144">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="8673e-145">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="8673e-145">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="8673e-146">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="8673e-146">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="8673e-147">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="8673e-147">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="8673e-148">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="8673e-148">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8673e-149">子元素</span><span class="sxs-lookup"><span data-stu-id="8673e-149">Child Elements</span></span>

<span data-ttu-id="8673e-150">無。</span><span class="sxs-lookup"><span data-stu-id="8673e-150">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8673e-151">父項目</span><span class="sxs-lookup"><span data-stu-id="8673e-151">Parent Elements</span></span>

|<span data-ttu-id="8673e-152">項目</span><span class="sxs-lookup"><span data-stu-id="8673e-152">Element</span></span>|<span data-ttu-id="8673e-153">描述</span><span class="sxs-lookup"><span data-stu-id="8673e-153">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8673e-154">\<security></span><span class="sxs-lookup"><span data-stu-id="8673e-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="8673e-155">代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="8673e-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="8673e-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8673e-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="8673e-157">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8673e-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8673e-158">繫結</span><span class="sxs-lookup"><span data-stu-id="8673e-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8673e-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8673e-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8673e-160">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="8673e-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8673e-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="8673e-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
