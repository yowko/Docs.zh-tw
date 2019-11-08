---
title: <transport> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732797"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="6367a-102">\<webHttpBinding 的 \<傳輸 > ></span><span class="sxs-lookup"><span data-stu-id="6367a-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="6367a-103">定義服務端點 (此服務端點是設定來接收 HTTP 要求的) 之傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6367a-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="6367a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6367a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6367a-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6367a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6367a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="6367a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6367a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6367a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="6367a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="6367a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6367a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6367a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="6367a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="6367a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6367a-111">語法</span><span class="sxs-lookup"><span data-stu-id="6367a-111">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="6367a-112">輸入</span><span class="sxs-lookup"><span data-stu-id="6367a-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6367a-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6367a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6367a-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6367a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6367a-115">屬性</span><span class="sxs-lookup"><span data-stu-id="6367a-115">Attributes</span></span>  
  
|<span data-ttu-id="6367a-116">屬性</span><span class="sxs-lookup"><span data-stu-id="6367a-116">Attribute</span></span>|<span data-ttu-id="6367a-117">描述</span><span class="sxs-lookup"><span data-stu-id="6367a-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="6367a-118">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="6367a-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="6367a-119">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="6367a-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="6367a-120">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="6367a-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="6367a-121">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="6367a-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="6367a-122">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="6367a-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="6367a-123">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="6367a-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="6367a-124">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="6367a-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="6367a-125">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="6367a-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="6367a-126">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6367a-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="6367a-127">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="6367a-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="6367a-128">1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。</span><span class="sxs-lookup"><span data-stu-id="6367a-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="6367a-129">2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="6367a-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="6367a-130">3. always –一律強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="6367a-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="6367a-131">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="6367a-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="6367a-132">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="6367a-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6367a-133">值</span><span class="sxs-lookup"><span data-stu-id="6367a-133">Value</span></span>|<span data-ttu-id="6367a-134">描述</span><span class="sxs-lookup"><span data-stu-id="6367a-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6367a-135">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="6367a-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="6367a-136">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="6367a-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="6367a-137">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="6367a-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="6367a-138">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="6367a-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="6367a-139">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="6367a-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="6367a-140">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="6367a-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="6367a-141">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="6367a-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6367a-142">值</span><span class="sxs-lookup"><span data-stu-id="6367a-142">Value</span></span>|<span data-ttu-id="6367a-143">描述</span><span class="sxs-lookup"><span data-stu-id="6367a-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6367a-144">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="6367a-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="6367a-145">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="6367a-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="6367a-146">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="6367a-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="6367a-147">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="6367a-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="6367a-148">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="6367a-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6367a-149">子項目</span><span class="sxs-lookup"><span data-stu-id="6367a-149">Child Elements</span></span>  
 <span data-ttu-id="6367a-150">無。</span><span class="sxs-lookup"><span data-stu-id="6367a-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6367a-151">父項目</span><span class="sxs-lookup"><span data-stu-id="6367a-151">Parent Elements</span></span>  
  
|<span data-ttu-id="6367a-152">項目</span><span class="sxs-lookup"><span data-stu-id="6367a-152">Element</span></span>|<span data-ttu-id="6367a-153">描述</span><span class="sxs-lookup"><span data-stu-id="6367a-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6367a-154">\<security ></span><span class="sxs-lookup"><span data-stu-id="6367a-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="6367a-155">表示[\<wsHttpBinding >](wshttpbinding.md)元素的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="6367a-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6367a-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="6367a-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="6367a-157">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6367a-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6367a-158">繫結</span><span class="sxs-lookup"><span data-stu-id="6367a-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6367a-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6367a-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6367a-160">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6367a-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6367a-161">\<binding ></span><span class="sxs-lookup"><span data-stu-id="6367a-161">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="6367a-162">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="6367a-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
