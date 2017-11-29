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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 31c5404b29f025af5193386eccafdbeab95cb2cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="dc4d3-102">&lt;ws2007HttpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="dc4d3-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="dc4d3-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="dc4d3-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dc4d3-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-105">\<bindings></span></span>  
<span data-ttu-id="dc4d3-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="dc4d3-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-107">\<binding></span></span>  
<span data-ttu-id="dc4d3-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-108">\<security></span></span>  
<span data-ttu-id="dc4d3-109">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4d3-110">語法</span><span class="sxs-lookup"><span data-stu-id="dc4d3-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="dc4d3-111">類型</span><span class="sxs-lookup"><span data-stu-id="dc4d3-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc4d3-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc4d3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dc4d3-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc4d3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="dc4d3-114">Attributes</span></span>  
  
|<span data-ttu-id="dc4d3-115">屬性</span><span class="sxs-lookup"><span data-stu-id="dc4d3-115">Attribute</span></span>|<span data-ttu-id="dc4d3-116">描述</span><span class="sxs-lookup"><span data-stu-id="dc4d3-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="dc4d3-117">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="dc4d3-118">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="dc4d3-119">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="dc4d3-120">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="dc4d3-121">摘要式或基本驗證的驗證領域。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="dc4d3-122">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="dc4d3-123">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="dc4d3-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="dc4d3-124">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="dc4d3-125">使用者可以查詢驗證領域，判斷其中可以使用的一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="dc4d3-126">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="dc4d3-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="dc4d3-127">值</span><span class="sxs-lookup"><span data-stu-id="dc4d3-127">Value</span></span>|<span data-ttu-id="dc4d3-128">描述</span><span class="sxs-lookup"><span data-stu-id="dc4d3-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dc4d3-129">無</span><span class="sxs-lookup"><span data-stu-id="dc4d3-129">None</span></span>|<span data-ttu-id="dc4d3-130">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-130">Security is disabled.</span></span>|  
|<span data-ttu-id="dc4d3-131">基本</span><span class="sxs-lookup"><span data-stu-id="dc4d3-131">Basic</span></span>|<span data-ttu-id="dc4d3-132">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="dc4d3-133">摘要</span><span class="sxs-lookup"><span data-stu-id="dc4d3-133">Digest</span></span>|<span data-ttu-id="dc4d3-134">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="dc4d3-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="dc4d3-135">Ntlm</span></span>|<span data-ttu-id="dc4d3-136">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="dc4d3-137">Windows</span><span class="sxs-lookup"><span data-stu-id="dc4d3-137">Windows</span></span>|<span data-ttu-id="dc4d3-138">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="dc4d3-139">憑證</span><span class="sxs-lookup"><span data-stu-id="dc4d3-139">Certificate</span></span>|<span data-ttu-id="dc4d3-140">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="dc4d3-141">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="dc4d3-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="dc4d3-142">值</span><span class="sxs-lookup"><span data-stu-id="dc4d3-142">Value</span></span>|<span data-ttu-id="dc4d3-143">描述</span><span class="sxs-lookup"><span data-stu-id="dc4d3-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dc4d3-144">無</span><span class="sxs-lookup"><span data-stu-id="dc4d3-144">None</span></span>|<span data-ttu-id="dc4d3-145">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-145">Security is disabled.</span></span>|  
|<span data-ttu-id="dc4d3-146">基本</span><span class="sxs-lookup"><span data-stu-id="dc4d3-146">Basic</span></span>|<span data-ttu-id="dc4d3-147">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="dc4d3-148">摘要</span><span class="sxs-lookup"><span data-stu-id="dc4d3-148">Digest</span></span>|<span data-ttu-id="dc4d3-149">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="dc4d3-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="dc4d3-150">Ntlm</span></span>|<span data-ttu-id="dc4d3-151">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="dc4d3-152">Windows</span><span class="sxs-lookup"><span data-stu-id="dc4d3-152">Windows</span></span>|<span data-ttu-id="dc4d3-153">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="dc4d3-154">憑證</span><span class="sxs-lookup"><span data-stu-id="dc4d3-154">Certificate</span></span>|<span data-ttu-id="dc4d3-155">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc4d3-156">子元素</span><span class="sxs-lookup"><span data-stu-id="dc4d3-156">Child Elements</span></span>  
 <span data-ttu-id="dc4d3-157">無</span><span class="sxs-lookup"><span data-stu-id="dc4d3-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc4d3-158">父項目</span><span class="sxs-lookup"><span data-stu-id="dc4d3-158">Parent Elements</span></span>  
  
|<span data-ttu-id="dc4d3-159">項目</span><span class="sxs-lookup"><span data-stu-id="dc4d3-159">Element</span></span>|<span data-ttu-id="dc4d3-160">說明</span><span class="sxs-lookup"><span data-stu-id="dc4d3-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc4d3-161">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="dc4d3-162">代表的安全性功能[ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="dc4d3-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc4d3-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4d3-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="dc4d3-164">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="dc4d3-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="dc4d3-165">繫結</span><span class="sxs-lookup"><span data-stu-id="dc4d3-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dc4d3-166">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="dc4d3-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="dc4d3-167">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="dc4d3-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="dc4d3-168">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
