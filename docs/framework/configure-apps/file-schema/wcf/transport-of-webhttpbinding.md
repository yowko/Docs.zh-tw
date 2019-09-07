---
title: <transport> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 98cdaa86441f91552c7133d8e5694f88019a6dbf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399285"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="b2cc8-102">\<webHttpBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="b2cc8-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="b2cc8-103">定義服務端點 (此服務端點是設定來接收 HTTP 要求的) 之傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="b2cc8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2cc8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b2cc8-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b2cc8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b2cc8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b2cc8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b2cc8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b2cc8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="b2cc8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="b2cc8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b2cc8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b2cc8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="b2cc8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="b2cc8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2cc8-111">語法</span><span class="sxs-lookup"><span data-stu-id="b2cc8-111">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="b2cc8-112">類型</span><span class="sxs-lookup"><span data-stu-id="b2cc8-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2cc8-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b2cc8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b2cc8-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2cc8-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b2cc8-115">Attributes</span></span>  
  
|<span data-ttu-id="b2cc8-116">屬性</span><span class="sxs-lookup"><span data-stu-id="b2cc8-116">Attribute</span></span>|<span data-ttu-id="b2cc8-117">說明</span><span class="sxs-lookup"><span data-stu-id="b2cc8-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="b2cc8-118">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="b2cc8-119">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="b2cc8-120">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="b2cc8-121">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="b2cc8-122">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="b2cc8-123">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="b2cc8-124">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="b2cc8-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="b2cc8-125">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="b2cc8-126">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="b2cc8-127">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b2cc8-128">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b2cc8-129">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b2cc8-130">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b2cc8-131">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b2cc8-132">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="b2cc8-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b2cc8-133">值</span><span class="sxs-lookup"><span data-stu-id="b2cc8-133">Value</span></span>|<span data-ttu-id="b2cc8-134">說明</span><span class="sxs-lookup"><span data-stu-id="b2cc8-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="b2cc8-135">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="b2cc8-136">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="b2cc8-137">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="b2cc8-138">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="b2cc8-139">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="b2cc8-140">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="b2cc8-141">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="b2cc8-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b2cc8-142">值</span><span class="sxs-lookup"><span data-stu-id="b2cc8-142">Value</span></span>|<span data-ttu-id="b2cc8-143">描述</span><span class="sxs-lookup"><span data-stu-id="b2cc8-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="b2cc8-144">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="b2cc8-145">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="b2cc8-146">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="b2cc8-147">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="b2cc8-148">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2cc8-149">子元素</span><span class="sxs-lookup"><span data-stu-id="b2cc8-149">Child Elements</span></span>  
 <span data-ttu-id="b2cc8-150">無。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2cc8-151">父項目</span><span class="sxs-lookup"><span data-stu-id="b2cc8-151">Parent Elements</span></span>  
  
|<span data-ttu-id="b2cc8-152">項目</span><span class="sxs-lookup"><span data-stu-id="b2cc8-152">Element</span></span>|<span data-ttu-id="b2cc8-153">說明</span><span class="sxs-lookup"><span data-stu-id="b2cc8-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2cc8-154">\<security></span><span class="sxs-lookup"><span data-stu-id="b2cc8-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="b2cc8-155">表示[ \<wsHttpBinding >](wshttpbinding.md)元素的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="b2cc8-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2cc8-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2cc8-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="b2cc8-157">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b2cc8-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b2cc8-158">繫結</span><span class="sxs-lookup"><span data-stu-id="b2cc8-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b2cc8-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="b2cc8-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b2cc8-160">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="b2cc8-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b2cc8-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="b2cc8-161">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="b2cc8-162">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="b2cc8-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
