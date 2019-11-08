---
title: <transport> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732732"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="1b634-102">\<wsHttpBinding 的 \<傳輸 > ></span><span class="sxs-lookup"><span data-stu-id="1b634-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="1b634-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="1b634-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="1b634-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1b634-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1b634-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="1b634-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1b634-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="1b634-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1b634-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1b634-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="1b634-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="1b634-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1b634-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1b634-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="1b634-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="1b634-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="1b634-111">語法</span><span class="sxs-lookup"><span data-stu-id="1b634-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="1b634-112">輸入</span><span class="sxs-lookup"><span data-stu-id="1b634-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="1b634-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1b634-113">Attributes and Elements</span></span>

<span data-ttu-id="1b634-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1b634-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b634-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1b634-115">Attributes</span></span>

|<span data-ttu-id="1b634-116">屬性</span><span class="sxs-lookup"><span data-stu-id="1b634-116">Attribute</span></span>|<span data-ttu-id="1b634-117">描述</span><span class="sxs-lookup"><span data-stu-id="1b634-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="1b634-118">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="1b634-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="1b634-119">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="1b634-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="1b634-120">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="1b634-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="1b634-121">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="1b634-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="1b634-122">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="1b634-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="1b634-123">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="1b634-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="1b634-124">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="1b634-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="1b634-125">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="1b634-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="1b634-126">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="1b634-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="1b634-127">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="1b634-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="1b634-128">1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。</span><span class="sxs-lookup"><span data-stu-id="1b634-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="1b634-129">2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="1b634-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="1b634-130">3. always –一律強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="1b634-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="1b634-131">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="1b634-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="1b634-132">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="1b634-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="1b634-133">值</span><span class="sxs-lookup"><span data-stu-id="1b634-133">Value</span></span>|<span data-ttu-id="1b634-134">描述</span><span class="sxs-lookup"><span data-stu-id="1b634-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="1b634-135">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="1b634-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="1b634-136">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="1b634-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="1b634-137">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="1b634-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="1b634-138">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="1b634-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="1b634-139">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b634-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="1b634-140">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="1b634-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="1b634-141">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="1b634-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="1b634-142">值</span><span class="sxs-lookup"><span data-stu-id="1b634-142">Value</span></span>|<span data-ttu-id="1b634-143">描述</span><span class="sxs-lookup"><span data-stu-id="1b634-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="1b634-144">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="1b634-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="1b634-145">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="1b634-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="1b634-146">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="1b634-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="1b634-147">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="1b634-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="1b634-148">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1b634-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="1b634-149">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="1b634-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1b634-150">子項目</span><span class="sxs-lookup"><span data-stu-id="1b634-150">Child Elements</span></span>

<span data-ttu-id="1b634-151">無。</span><span class="sxs-lookup"><span data-stu-id="1b634-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b634-152">父項目</span><span class="sxs-lookup"><span data-stu-id="1b634-152">Parent Elements</span></span>

|<span data-ttu-id="1b634-153">項目</span><span class="sxs-lookup"><span data-stu-id="1b634-153">Element</span></span>|<span data-ttu-id="1b634-154">描述</span><span class="sxs-lookup"><span data-stu-id="1b634-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b634-155">\<security ></span><span class="sxs-lookup"><span data-stu-id="1b634-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="1b634-156">表示[\<wsHttpBinding >](wshttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="1b634-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="1b634-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b634-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="1b634-158">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="1b634-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1b634-159">繫結</span><span class="sxs-lookup"><span data-stu-id="1b634-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1b634-160">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="1b634-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1b634-161">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="1b634-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1b634-162">\<binding ></span><span class="sxs-lookup"><span data-stu-id="1b634-162">\<binding></span></span>](bindings.md)
