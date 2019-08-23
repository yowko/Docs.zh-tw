---
title: <transport> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: f78add5397644dc40bfd22f10bd84aa5c5eb29e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923203"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="6a826-102">\<webHttpBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="6a826-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="6a826-103">定義服務端點 (此服務端點是設定來接收 HTTP 要求的) 之傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6a826-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="6a826-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a826-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a826-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6a826-105">\<bindings></span></span>  
<span data-ttu-id="6a826-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6a826-106">\<webHttpBinding></span></span>  
<span data-ttu-id="6a826-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="6a826-107">\<binding></span></span>  
<span data-ttu-id="6a826-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6a826-108">\<security></span></span>  
<span data-ttu-id="6a826-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="6a826-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a826-110">語法</span><span class="sxs-lookup"><span data-stu-id="6a826-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="6a826-111">類型</span><span class="sxs-lookup"><span data-stu-id="6a826-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a826-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6a826-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6a826-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6a826-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a826-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6a826-114">Attributes</span></span>  
  
|<span data-ttu-id="6a826-115">屬性</span><span class="sxs-lookup"><span data-stu-id="6a826-115">Attribute</span></span>|<span data-ttu-id="6a826-116">描述</span><span class="sxs-lookup"><span data-stu-id="6a826-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="6a826-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="6a826-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="6a826-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="6a826-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="6a826-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="6a826-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="6a826-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="6a826-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="6a826-121">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="6a826-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="6a826-122">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="6a826-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="6a826-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="6a826-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="6a826-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="6a826-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="6a826-125">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6a826-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="6a826-126">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="6a826-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="6a826-127">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="6a826-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="6a826-128">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="6a826-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="6a826-129">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="6a826-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="6a826-130">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="6a826-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="6a826-131">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="6a826-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6a826-132">值</span><span class="sxs-lookup"><span data-stu-id="6a826-132">Value</span></span>|<span data-ttu-id="6a826-133">說明</span><span class="sxs-lookup"><span data-stu-id="6a826-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6a826-134">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="6a826-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="6a826-135">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="6a826-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="6a826-136">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="6a826-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="6a826-137">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="6a826-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="6a826-138">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="6a826-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="6a826-139">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="6a826-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="6a826-140">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="6a826-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6a826-141">值</span><span class="sxs-lookup"><span data-stu-id="6a826-141">Value</span></span>|<span data-ttu-id="6a826-142">說明</span><span class="sxs-lookup"><span data-stu-id="6a826-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6a826-143">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="6a826-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="6a826-144">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="6a826-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="6a826-145">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="6a826-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="6a826-146">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="6a826-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="6a826-147">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="6a826-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a826-148">子元素</span><span class="sxs-lookup"><span data-stu-id="6a826-148">Child Elements</span></span>  
 <span data-ttu-id="6a826-149">無。</span><span class="sxs-lookup"><span data-stu-id="6a826-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a826-150">父項目</span><span class="sxs-lookup"><span data-stu-id="6a826-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6a826-151">項目</span><span class="sxs-lookup"><span data-stu-id="6a826-151">Element</span></span>|<span data-ttu-id="6a826-152">描述</span><span class="sxs-lookup"><span data-stu-id="6a826-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a826-153">\<security></span><span class="sxs-lookup"><span data-stu-id="6a826-153">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="6a826-154">表示[ \<wsHttpBinding >](wshttpbinding.md)元素的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6a826-154">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a826-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a826-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="6a826-156">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6a826-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6a826-157">繫結</span><span class="sxs-lookup"><span data-stu-id="6a826-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6a826-158">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6a826-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6a826-159">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6a826-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6a826-160">\<binding></span><span class="sxs-lookup"><span data-stu-id="6a826-160">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="6a826-161">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="6a826-161">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
