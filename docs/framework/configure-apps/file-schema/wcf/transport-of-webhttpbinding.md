---
title: <transport> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: b9efc732832a8862373b14f657796a59fb52c1a1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162110"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="2518e-102">\<transport> 的 \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2518e-102">\<transport> of \<webHttpBinding></span></span>

<span data-ttu-id="2518e-103">定義服務端點 (此服務端點是設定來接收 HTTP 要求的) 之傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2518e-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="2518e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2518e-104">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="2518e-105">類型</span><span class="sxs-lookup"><span data-stu-id="2518e-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2518e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2518e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2518e-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2518e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2518e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2518e-108">Attributes</span></span>  
  
|<span data-ttu-id="2518e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2518e-109">Attribute</span></span>|<span data-ttu-id="2518e-110">描述</span><span class="sxs-lookup"><span data-stu-id="2518e-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="2518e-111">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="2518e-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="2518e-112">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="2518e-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="2518e-113">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="2518e-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="2518e-114">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="2518e-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="2518e-115">指定摘要式驗證或基本驗證之驗證領域的字串。</span><span class="sxs-lookup"><span data-stu-id="2518e-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="2518e-116">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="2518e-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2518e-117">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="2518e-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="2518e-118">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="2518e-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="2518e-119">使用者可以查詢驗證領域，以確定可以使用的其中一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2518e-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="2518e-120">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="2518e-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="2518e-121">1. 永不–不會強制執行原則， (已停用) 的擴充保護。</span><span class="sxs-lookup"><span data-stu-id="2518e-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="2518e-122">2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="2518e-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="2518e-123">3. 一律：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="2518e-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="2518e-124">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="2518e-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2518e-125">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="2518e-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2518e-126">值</span><span class="sxs-lookup"><span data-stu-id="2518e-126">Value</span></span>|<span data-ttu-id="2518e-127">描述</span><span class="sxs-lookup"><span data-stu-id="2518e-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2518e-128">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2518e-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2518e-129">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="2518e-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="2518e-130">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="2518e-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="2518e-131">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="2518e-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2518e-132">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="2518e-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2518e-133">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2518e-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2518e-134">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="2518e-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2518e-135">值</span><span class="sxs-lookup"><span data-stu-id="2518e-135">Value</span></span>|<span data-ttu-id="2518e-136">描述</span><span class="sxs-lookup"><span data-stu-id="2518e-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2518e-137">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2518e-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2518e-138">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="2518e-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="2518e-139">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="2518e-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2518e-140">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="2518e-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2518e-141">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2518e-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2518e-142">子元素</span><span class="sxs-lookup"><span data-stu-id="2518e-142">Child Elements</span></span>  

 <span data-ttu-id="2518e-143">無。</span><span class="sxs-lookup"><span data-stu-id="2518e-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2518e-144">父項目</span><span class="sxs-lookup"><span data-stu-id="2518e-144">Parent Elements</span></span>  
  
|<span data-ttu-id="2518e-145">項目</span><span class="sxs-lookup"><span data-stu-id="2518e-145">Element</span></span>|<span data-ttu-id="2518e-146">描述</span><span class="sxs-lookup"><span data-stu-id="2518e-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="2518e-147">代表專案的安全性功能 [\<wsHttpBinding>](wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2518e-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2518e-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2518e-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="2518e-149">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2518e-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2518e-150">繫結</span><span class="sxs-lookup"><span data-stu-id="2518e-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2518e-151">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2518e-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2518e-152">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="2518e-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="2518e-153">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="2518e-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
