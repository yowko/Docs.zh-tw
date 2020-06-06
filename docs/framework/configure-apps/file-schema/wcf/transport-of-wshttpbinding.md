---
title: <transport> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732732"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="a8838-102">\<transport> 的 \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a8838-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="a8838-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="a8838-103">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="a8838-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8838-104">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="a8838-105">類型</span><span class="sxs-lookup"><span data-stu-id="a8838-105">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="a8838-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8838-106">Attributes and Elements</span></span>

<span data-ttu-id="a8838-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a8838-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8838-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a8838-108">Attributes</span></span>

|<span data-ttu-id="a8838-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a8838-109">Attribute</span></span>|<span data-ttu-id="a8838-110">描述</span><span class="sxs-lookup"><span data-stu-id="a8838-110">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="a8838-111">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="a8838-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="a8838-112">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="a8838-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="a8838-113">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="a8838-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="a8838-114">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="a8838-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="a8838-115">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="a8838-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="a8838-116">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="a8838-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a8838-117">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="a8838-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="a8838-118">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="a8838-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="a8838-119">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a8838-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="a8838-120">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="a8838-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a8838-121">1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。</span><span class="sxs-lookup"><span data-stu-id="a8838-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a8838-122">2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="a8838-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a8838-123">3. always –一律強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="a8838-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a8838-124">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="a8838-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a8838-125">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="a8838-125">clientCredentialType Attribute</span></span>

|<span data-ttu-id="a8838-126">值</span><span class="sxs-lookup"><span data-stu-id="a8838-126">Value</span></span>|<span data-ttu-id="a8838-127">描述</span><span class="sxs-lookup"><span data-stu-id="a8838-127">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="a8838-128">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="a8838-128">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="a8838-129">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="a8838-129">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="a8838-130">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="a8838-130">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="a8838-131">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="a8838-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="a8838-132">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a8838-132">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="a8838-133">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="a8838-133">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a8838-134">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="a8838-134">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="a8838-135">值</span><span class="sxs-lookup"><span data-stu-id="a8838-135">Value</span></span>|<span data-ttu-id="a8838-136">描述</span><span class="sxs-lookup"><span data-stu-id="a8838-136">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="a8838-137">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="a8838-137">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="a8838-138">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="a8838-138">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="a8838-139">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="a8838-139">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="a8838-140">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="a8838-140">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="a8838-141">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a8838-141">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="a8838-142">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="a8838-142">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a8838-143">子元素</span><span class="sxs-lookup"><span data-stu-id="a8838-143">Child Elements</span></span>

<span data-ttu-id="a8838-144">無。</span><span class="sxs-lookup"><span data-stu-id="a8838-144">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8838-145">父項目</span><span class="sxs-lookup"><span data-stu-id="a8838-145">Parent Elements</span></span>

|<span data-ttu-id="a8838-146">元素</span><span class="sxs-lookup"><span data-stu-id="a8838-146">Element</span></span>|<span data-ttu-id="a8838-147">描述</span><span class="sxs-lookup"><span data-stu-id="a8838-147">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="a8838-148">表示的安全性功能 [\<wsHttpBinding>](wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="a8838-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="a8838-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8838-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="a8838-150">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="a8838-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a8838-151">繫結</span><span class="sxs-lookup"><span data-stu-id="a8838-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a8838-152">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a8838-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a8838-153">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a8838-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
