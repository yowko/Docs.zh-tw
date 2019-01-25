---
title: '&lt;ws2007HttpBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 6f09a71a7ec7dbfae5eb6f1896f1fba68456973f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642590"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="48263-102">&lt;ws2007HttpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="48263-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="48263-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="48263-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="48263-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="48263-104">\<system.serviceModel></span></span>  
<span data-ttu-id="48263-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="48263-105">\<bindings></span></span>  
<span data-ttu-id="48263-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="48263-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="48263-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="48263-107">\<binding></span></span>  
<span data-ttu-id="48263-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="48263-108">\<security></span></span>  
<span data-ttu-id="48263-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="48263-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48263-110">語法</span><span class="sxs-lookup"><span data-stu-id="48263-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="48263-111">類型</span><span class="sxs-lookup"><span data-stu-id="48263-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48263-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="48263-112">Attributes and Elements</span></span>  
 <span data-ttu-id="48263-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="48263-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48263-114">屬性</span><span class="sxs-lookup"><span data-stu-id="48263-114">Attributes</span></span>  
  
|<span data-ttu-id="48263-115">屬性</span><span class="sxs-lookup"><span data-stu-id="48263-115">Attribute</span></span>|<span data-ttu-id="48263-116">描述</span><span class="sxs-lookup"><span data-stu-id="48263-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="48263-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="48263-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="48263-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="48263-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="48263-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="48263-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="48263-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="48263-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="48263-121">摘要式或基本驗證的驗證領域。</span><span class="sxs-lookup"><span data-stu-id="48263-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="48263-122">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="48263-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="48263-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="48263-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="48263-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="48263-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="48263-125">使用者可以查詢驗證領域，判斷其中可以使用的一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="48263-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="48263-126">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="48263-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="48263-127">值</span><span class="sxs-lookup"><span data-stu-id="48263-127">Value</span></span>|<span data-ttu-id="48263-128">描述</span><span class="sxs-lookup"><span data-stu-id="48263-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48263-129">無</span><span class="sxs-lookup"><span data-stu-id="48263-129">None</span></span>|<span data-ttu-id="48263-130">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="48263-130">Security is disabled.</span></span>|  
|<span data-ttu-id="48263-131">基本</span><span class="sxs-lookup"><span data-stu-id="48263-131">Basic</span></span>|<span data-ttu-id="48263-132">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="48263-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="48263-133">摘要</span><span class="sxs-lookup"><span data-stu-id="48263-133">Digest</span></span>|<span data-ttu-id="48263-134">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="48263-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="48263-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="48263-135">Ntlm</span></span>|<span data-ttu-id="48263-136">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="48263-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="48263-137">Windows</span><span class="sxs-lookup"><span data-stu-id="48263-137">Windows</span></span>|<span data-ttu-id="48263-138">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="48263-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="48263-139">憑證</span><span class="sxs-lookup"><span data-stu-id="48263-139">Certificate</span></span>|<span data-ttu-id="48263-140">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="48263-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="48263-141">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="48263-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="48263-142">值</span><span class="sxs-lookup"><span data-stu-id="48263-142">Value</span></span>|<span data-ttu-id="48263-143">描述</span><span class="sxs-lookup"><span data-stu-id="48263-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48263-144">無</span><span class="sxs-lookup"><span data-stu-id="48263-144">None</span></span>|<span data-ttu-id="48263-145">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="48263-145">Security is disabled.</span></span>|  
|<span data-ttu-id="48263-146">基本</span><span class="sxs-lookup"><span data-stu-id="48263-146">Basic</span></span>|<span data-ttu-id="48263-147">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="48263-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="48263-148">摘要</span><span class="sxs-lookup"><span data-stu-id="48263-148">Digest</span></span>|<span data-ttu-id="48263-149">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="48263-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="48263-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="48263-150">Ntlm</span></span>|<span data-ttu-id="48263-151">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="48263-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="48263-152">Windows</span><span class="sxs-lookup"><span data-stu-id="48263-152">Windows</span></span>|<span data-ttu-id="48263-153">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="48263-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="48263-154">憑證</span><span class="sxs-lookup"><span data-stu-id="48263-154">Certificate</span></span>|<span data-ttu-id="48263-155">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="48263-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48263-156">子元素</span><span class="sxs-lookup"><span data-stu-id="48263-156">Child Elements</span></span>  
 <span data-ttu-id="48263-157">無</span><span class="sxs-lookup"><span data-stu-id="48263-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48263-158">父項目</span><span class="sxs-lookup"><span data-stu-id="48263-158">Parent Elements</span></span>  
  
|<span data-ttu-id="48263-159">項目</span><span class="sxs-lookup"><span data-stu-id="48263-159">Element</span></span>|<span data-ttu-id="48263-160">描述</span><span class="sxs-lookup"><span data-stu-id="48263-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48263-161">\<security></span><span class="sxs-lookup"><span data-stu-id="48263-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="48263-162">代表的安全性功能[ \<lt;ws2007httpbinding&gt >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="48263-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48263-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48263-163">See also</span></span>
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="48263-164">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="48263-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="48263-165">繫結</span><span class="sxs-lookup"><span data-stu-id="48263-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="48263-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="48263-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="48263-167">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="48263-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="48263-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="48263-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
