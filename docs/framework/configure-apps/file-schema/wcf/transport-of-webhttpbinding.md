---
title: "&lt;webHttpBinding&gt; 的 &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebc9bb8b128f4b4097d4f470920dbd28d17e6f00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="1a03d-102">&lt;webHttpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="1a03d-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="1a03d-103">定義服務端點 (此服務端點是設定來接收 HTTP 要求的) 之傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1a03d-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="1a03d-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a03d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a03d-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="1a03d-105">\<bindings></span></span>  
<span data-ttu-id="1a03d-106">\<w ></span><span class="sxs-lookup"><span data-stu-id="1a03d-106">\<webHttpBinding></span></span>  
<span data-ttu-id="1a03d-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="1a03d-107">\<binding></span></span>  
<span data-ttu-id="1a03d-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="1a03d-108">\<security></span></span>  
<span data-ttu-id="1a03d-109">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="1a03d-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a03d-110">語法</span><span class="sxs-lookup"><span data-stu-id="1a03d-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="1a03d-111">類型</span><span class="sxs-lookup"><span data-stu-id="1a03d-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a03d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1a03d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1a03d-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1a03d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a03d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1a03d-114">Attributes</span></span>  
  
|<span data-ttu-id="1a03d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1a03d-115">Attribute</span></span>|<span data-ttu-id="1a03d-116">描述</span><span class="sxs-lookup"><span data-stu-id="1a03d-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="1a03d-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="1a03d-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="1a03d-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="1a03d-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="1a03d-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="1a03d-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="1a03d-121">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="1a03d-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="1a03d-122">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="1a03d-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="1a03d-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="1a03d-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="1a03d-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="1a03d-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="1a03d-125">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="1a03d-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="1a03d-126">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="1a03d-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="1a03d-127">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="1a03d-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="1a03d-128">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="1a03d-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="1a03d-129">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="1a03d-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="1a03d-130">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="1a03d-131">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="1a03d-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1a03d-132">值</span><span class="sxs-lookup"><span data-stu-id="1a03d-132">Value</span></span>|<span data-ttu-id="1a03d-133">描述</span><span class="sxs-lookup"><span data-stu-id="1a03d-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1a03d-134">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="1a03d-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="1a03d-135">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="1a03d-136">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="1a03d-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="1a03d-137">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="1a03d-138">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="1a03d-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="1a03d-139">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="1a03d-140">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="1a03d-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1a03d-141">值</span><span class="sxs-lookup"><span data-stu-id="1a03d-141">Value</span></span>|<span data-ttu-id="1a03d-142">描述</span><span class="sxs-lookup"><span data-stu-id="1a03d-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1a03d-143">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="1a03d-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="1a03d-144">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="1a03d-145">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="1a03d-146">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="1a03d-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="1a03d-147">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1a03d-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a03d-148">子元素</span><span class="sxs-lookup"><span data-stu-id="1a03d-148">Child Elements</span></span>  
 <span data-ttu-id="1a03d-149">無。</span><span class="sxs-lookup"><span data-stu-id="1a03d-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a03d-150">父項目</span><span class="sxs-lookup"><span data-stu-id="1a03d-150">Parent Elements</span></span>  
  
|<span data-ttu-id="1a03d-151">項目</span><span class="sxs-lookup"><span data-stu-id="1a03d-151">Element</span></span>|<span data-ttu-id="1a03d-152">描述</span><span class="sxs-lookup"><span data-stu-id="1a03d-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a03d-153">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="1a03d-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="1a03d-154">代表的安全性功能[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="1a03d-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a03d-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a03d-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="1a03d-156">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="1a03d-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1a03d-157">繫結</span><span class="sxs-lookup"><span data-stu-id="1a03d-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1a03d-158">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="1a03d-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1a03d-159">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="1a03d-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1a03d-160">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="1a03d-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="1a03d-161">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="1a03d-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
