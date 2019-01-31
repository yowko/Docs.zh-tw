---
title: <transport> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: d2c7ee3512ddeefae6e5551a58b3bab76742ed30
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286412"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="ba33f-102">\<transport> of \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ba33f-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="ba33f-103">定義服務端點 (此服務端點是設定來接收 HTTP 要求的) 之傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ba33f-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="ba33f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ba33f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba33f-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ba33f-105">\<bindings></span></span>  
<span data-ttu-id="ba33f-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ba33f-106">\<webHttpBinding></span></span>  
<span data-ttu-id="ba33f-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="ba33f-107">\<binding></span></span>  
<span data-ttu-id="ba33f-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="ba33f-108">\<security></span></span>  
<span data-ttu-id="ba33f-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="ba33f-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba33f-110">語法</span><span class="sxs-lookup"><span data-stu-id="ba33f-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="ba33f-111">類型</span><span class="sxs-lookup"><span data-stu-id="ba33f-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba33f-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ba33f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ba33f-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ba33f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba33f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ba33f-114">Attributes</span></span>  
  
|<span data-ttu-id="ba33f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ba33f-115">Attribute</span></span>|<span data-ttu-id="ba33f-116">描述</span><span class="sxs-lookup"><span data-stu-id="ba33f-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="ba33f-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ba33f-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="ba33f-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="ba33f-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ba33f-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="ba33f-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="ba33f-121">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="ba33f-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ba33f-122">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="ba33f-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ba33f-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="ba33f-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ba33f-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="ba33f-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="ba33f-125">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="ba33f-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="ba33f-126">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="ba33f-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="ba33f-127">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="ba33f-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="ba33f-128">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="ba33f-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="ba33f-129">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="ba33f-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="ba33f-130">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ba33f-131">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="ba33f-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ba33f-132">值</span><span class="sxs-lookup"><span data-stu-id="ba33f-132">Value</span></span>|<span data-ttu-id="ba33f-133">描述</span><span class="sxs-lookup"><span data-stu-id="ba33f-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ba33f-134">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="ba33f-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ba33f-135">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="ba33f-136">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="ba33f-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="ba33f-137">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ba33f-138">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="ba33f-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ba33f-139">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ba33f-140">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="ba33f-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ba33f-141">值</span><span class="sxs-lookup"><span data-stu-id="ba33f-141">Value</span></span>|<span data-ttu-id="ba33f-142">描述</span><span class="sxs-lookup"><span data-stu-id="ba33f-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ba33f-143">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="ba33f-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ba33f-144">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="ba33f-145">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ba33f-146">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="ba33f-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ba33f-147">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ba33f-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba33f-148">子元素</span><span class="sxs-lookup"><span data-stu-id="ba33f-148">Child Elements</span></span>  
 <span data-ttu-id="ba33f-149">無。</span><span class="sxs-lookup"><span data-stu-id="ba33f-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba33f-150">父項目</span><span class="sxs-lookup"><span data-stu-id="ba33f-150">Parent Elements</span></span>  
  
|<span data-ttu-id="ba33f-151">項目</span><span class="sxs-lookup"><span data-stu-id="ba33f-151">Element</span></span>|<span data-ttu-id="ba33f-152">描述</span><span class="sxs-lookup"><span data-stu-id="ba33f-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba33f-153">\<security></span><span class="sxs-lookup"><span data-stu-id="ba33f-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="ba33f-154">代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="ba33f-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba33f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba33f-155">See also</span></span>
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="ba33f-156">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ba33f-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ba33f-157">繫結</span><span class="sxs-lookup"><span data-stu-id="ba33f-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ba33f-158">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="ba33f-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ba33f-159">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="ba33f-159">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ba33f-160">\<binding></span><span class="sxs-lookup"><span data-stu-id="ba33f-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="ba33f-161">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="ba33f-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
