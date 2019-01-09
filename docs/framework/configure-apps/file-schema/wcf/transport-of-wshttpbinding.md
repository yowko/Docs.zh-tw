---
title: '&lt;wsHttpBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 4bd385e8c4fee1ea340e1d9df9816e25760efb02
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148626"
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="2beb3-102">&lt;wsHttpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="2beb3-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="2beb3-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="2beb3-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="2beb3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2beb3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2beb3-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2beb3-105">\<bindings></span></span>  
<span data-ttu-id="2beb3-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2beb3-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="2beb3-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2beb3-107">\<binding></span></span>  
<span data-ttu-id="2beb3-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="2beb3-108">\<security></span></span>  
<span data-ttu-id="2beb3-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="2beb3-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2beb3-110">語法</span><span class="sxs-lookup"><span data-stu-id="2beb3-110">Syntax</span></span>  
  
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
        </extendedProtecutionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="2beb3-111">類型</span><span class="sxs-lookup"><span data-stu-id="2beb3-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2beb3-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2beb3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2beb3-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2beb3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2beb3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2beb3-114">Attributes</span></span>  
  
|<span data-ttu-id="2beb3-115">屬性</span><span class="sxs-lookup"><span data-stu-id="2beb3-115">Attribute</span></span>|<span data-ttu-id="2beb3-116">描述</span><span class="sxs-lookup"><span data-stu-id="2beb3-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="2beb3-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="2beb3-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="2beb3-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="2beb3-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="2beb3-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="2beb3-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="2beb3-121">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="2beb3-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="2beb3-122">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="2beb3-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2beb3-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="2beb3-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="2beb3-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="2beb3-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="2beb3-125">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2beb3-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="2beb3-126">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="2beb3-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="2beb3-127">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="2beb3-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="2beb3-128">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="2beb3-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="2beb3-129">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="2beb3-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="2beb3-130">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2beb3-131">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="2beb3-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2beb3-132">值</span><span class="sxs-lookup"><span data-stu-id="2beb3-132">Value</span></span>|<span data-ttu-id="2beb3-133">描述</span><span class="sxs-lookup"><span data-stu-id="2beb3-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2beb3-134">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2beb3-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2beb3-135">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="2beb3-136">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2beb3-137">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="2beb3-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2beb3-138">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="2beb3-139">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="2beb3-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2beb3-140">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="2beb3-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2beb3-141">值</span><span class="sxs-lookup"><span data-stu-id="2beb3-141">Value</span></span>|<span data-ttu-id="2beb3-142">描述</span><span class="sxs-lookup"><span data-stu-id="2beb3-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2beb3-143">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2beb3-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2beb3-144">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="2beb3-145">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2beb3-146">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="2beb3-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2beb3-147">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2beb3-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="2beb3-148">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="2beb3-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2beb3-149">子元素</span><span class="sxs-lookup"><span data-stu-id="2beb3-149">Child Elements</span></span>  
 <span data-ttu-id="2beb3-150">無。</span><span class="sxs-lookup"><span data-stu-id="2beb3-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2beb3-151">父項目</span><span class="sxs-lookup"><span data-stu-id="2beb3-151">Parent Elements</span></span>  
  
|<span data-ttu-id="2beb3-152">項目</span><span class="sxs-lookup"><span data-stu-id="2beb3-152">Element</span></span>|<span data-ttu-id="2beb3-153">描述</span><span class="sxs-lookup"><span data-stu-id="2beb3-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2beb3-154">\<security></span><span class="sxs-lookup"><span data-stu-id="2beb3-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="2beb3-155">代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="2beb3-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2beb3-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2beb3-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="2beb3-157">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2beb3-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2beb3-158">繫結</span><span class="sxs-lookup"><span data-stu-id="2beb3-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2beb3-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2beb3-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2beb3-160">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="2beb3-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="2beb3-161">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2beb3-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
