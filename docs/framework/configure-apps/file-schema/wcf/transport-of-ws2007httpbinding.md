---
title: "&lt;ws2007HttpBinding&gt; 的 &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc60e72ae810578edb71b73b39e756a951b1f425
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="beeaf-102">&lt;ws2007HttpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="beeaf-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="beeaf-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="beeaf-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="beeaf-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="beeaf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="beeaf-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="beeaf-105">\<bindings></span></span>  
<span data-ttu-id="beeaf-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="beeaf-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="beeaf-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="beeaf-107">\<binding></span></span>  
<span data-ttu-id="beeaf-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="beeaf-108">\<security></span></span>  
<span data-ttu-id="beeaf-109">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="beeaf-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beeaf-110">語法</span><span class="sxs-lookup"><span data-stu-id="beeaf-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="beeaf-111">類型</span><span class="sxs-lookup"><span data-stu-id="beeaf-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beeaf-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="beeaf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="beeaf-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="beeaf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beeaf-114">屬性</span><span class="sxs-lookup"><span data-stu-id="beeaf-114">Attributes</span></span>  
  
|<span data-ttu-id="beeaf-115">屬性</span><span class="sxs-lookup"><span data-stu-id="beeaf-115">Attribute</span></span>|<span data-ttu-id="beeaf-116">描述</span><span class="sxs-lookup"><span data-stu-id="beeaf-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="beeaf-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="beeaf-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="beeaf-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="beeaf-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="beeaf-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="beeaf-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="beeaf-121">摘要式或基本驗證的驗證領域。</span><span class="sxs-lookup"><span data-stu-id="beeaf-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="beeaf-122">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="beeaf-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="beeaf-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="beeaf-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="beeaf-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="beeaf-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="beeaf-125">使用者可以查詢驗證領域，判斷其中可以使用的一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="beeaf-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="beeaf-126">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="beeaf-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="beeaf-127">值</span><span class="sxs-lookup"><span data-stu-id="beeaf-127">Value</span></span>|<span data-ttu-id="beeaf-128">描述</span><span class="sxs-lookup"><span data-stu-id="beeaf-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="beeaf-129">無</span><span class="sxs-lookup"><span data-stu-id="beeaf-129">None</span></span>|<span data-ttu-id="beeaf-130">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="beeaf-130">Security is disabled.</span></span>|  
|<span data-ttu-id="beeaf-131">基本</span><span class="sxs-lookup"><span data-stu-id="beeaf-131">Basic</span></span>|<span data-ttu-id="beeaf-132">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="beeaf-133">摘要</span><span class="sxs-lookup"><span data-stu-id="beeaf-133">Digest</span></span>|<span data-ttu-id="beeaf-134">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="beeaf-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="beeaf-135">Ntlm</span></span>|<span data-ttu-id="beeaf-136">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="beeaf-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="beeaf-137">Windows</span><span class="sxs-lookup"><span data-stu-id="beeaf-137">Windows</span></span>|<span data-ttu-id="beeaf-138">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="beeaf-139">憑證</span><span class="sxs-lookup"><span data-stu-id="beeaf-139">Certificate</span></span>|<span data-ttu-id="beeaf-140">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="beeaf-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="beeaf-141">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="beeaf-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="beeaf-142">值</span><span class="sxs-lookup"><span data-stu-id="beeaf-142">Value</span></span>|<span data-ttu-id="beeaf-143">描述</span><span class="sxs-lookup"><span data-stu-id="beeaf-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="beeaf-144">無</span><span class="sxs-lookup"><span data-stu-id="beeaf-144">None</span></span>|<span data-ttu-id="beeaf-145">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="beeaf-145">Security is disabled.</span></span>|  
|<span data-ttu-id="beeaf-146">基本</span><span class="sxs-lookup"><span data-stu-id="beeaf-146">Basic</span></span>|<span data-ttu-id="beeaf-147">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="beeaf-148">摘要</span><span class="sxs-lookup"><span data-stu-id="beeaf-148">Digest</span></span>|<span data-ttu-id="beeaf-149">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="beeaf-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="beeaf-150">Ntlm</span></span>|<span data-ttu-id="beeaf-151">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="beeaf-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="beeaf-152">Windows</span><span class="sxs-lookup"><span data-stu-id="beeaf-152">Windows</span></span>|<span data-ttu-id="beeaf-153">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="beeaf-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="beeaf-154">憑證</span><span class="sxs-lookup"><span data-stu-id="beeaf-154">Certificate</span></span>|<span data-ttu-id="beeaf-155">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="beeaf-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="beeaf-156">子元素</span><span class="sxs-lookup"><span data-stu-id="beeaf-156">Child Elements</span></span>  
 <span data-ttu-id="beeaf-157">無</span><span class="sxs-lookup"><span data-stu-id="beeaf-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="beeaf-158">父項目</span><span class="sxs-lookup"><span data-stu-id="beeaf-158">Parent Elements</span></span>  
  
|<span data-ttu-id="beeaf-159">項目</span><span class="sxs-lookup"><span data-stu-id="beeaf-159">Element</span></span>|<span data-ttu-id="beeaf-160">描述</span><span class="sxs-lookup"><span data-stu-id="beeaf-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beeaf-161">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="beeaf-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="beeaf-162">代表的安全性功能[ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="beeaf-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="beeaf-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="beeaf-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="beeaf-164">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="beeaf-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="beeaf-165">繫結</span><span class="sxs-lookup"><span data-stu-id="beeaf-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="beeaf-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="beeaf-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="beeaf-167">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="beeaf-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="beeaf-168">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="beeaf-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
