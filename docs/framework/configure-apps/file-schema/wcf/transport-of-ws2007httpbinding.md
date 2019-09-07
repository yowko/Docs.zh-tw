---
title: <transport> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 4ea60ccaba58bc0b3fa8f2263295bf1413d25e89
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399260"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="7ef6b-102">\<ws2007HttpBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="7ef6b-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="7ef6b-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="7ef6b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7ef6b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7ef6b-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7ef6b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7ef6b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7ef6b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7ef6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7ef6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="7ef6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="7ef6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7ef6b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7ef6b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="7ef6b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="7ef6b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ef6b-111">語法</span><span class="sxs-lookup"><span data-stu-id="7ef6b-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="7ef6b-112">類型</span><span class="sxs-lookup"><span data-stu-id="7ef6b-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ef6b-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7ef6b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7ef6b-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ef6b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7ef6b-115">Attributes</span></span>  
  
|<span data-ttu-id="7ef6b-116">屬性</span><span class="sxs-lookup"><span data-stu-id="7ef6b-116">Attribute</span></span>|<span data-ttu-id="7ef6b-117">描述</span><span class="sxs-lookup"><span data-stu-id="7ef6b-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="7ef6b-118">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="7ef6b-119">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="7ef6b-120">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="7ef6b-121">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="7ef6b-122">摘要式或基本驗證的驗證領域。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="7ef6b-123">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="7ef6b-124">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="7ef6b-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="7ef6b-125">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="7ef6b-126">使用者可以查詢驗證領域，判斷其中可以使用的一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="7ef6b-127">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="7ef6b-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7ef6b-128">值</span><span class="sxs-lookup"><span data-stu-id="7ef6b-128">Value</span></span>|<span data-ttu-id="7ef6b-129">描述</span><span class="sxs-lookup"><span data-stu-id="7ef6b-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ef6b-130">無</span><span class="sxs-lookup"><span data-stu-id="7ef6b-130">None</span></span>|<span data-ttu-id="7ef6b-131">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-131">Security is disabled.</span></span>|  
|<span data-ttu-id="7ef6b-132">基本</span><span class="sxs-lookup"><span data-stu-id="7ef6b-132">Basic</span></span>|<span data-ttu-id="7ef6b-133">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="7ef6b-134">摘要</span><span class="sxs-lookup"><span data-stu-id="7ef6b-134">Digest</span></span>|<span data-ttu-id="7ef6b-135">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="7ef6b-136">Ntlm</span><span class="sxs-lookup"><span data-stu-id="7ef6b-136">Ntlm</span></span>|<span data-ttu-id="7ef6b-137">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="7ef6b-138">Windows</span><span class="sxs-lookup"><span data-stu-id="7ef6b-138">Windows</span></span>|<span data-ttu-id="7ef6b-139">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="7ef6b-140">憑證</span><span class="sxs-lookup"><span data-stu-id="7ef6b-140">Certificate</span></span>|<span data-ttu-id="7ef6b-141">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="7ef6b-142">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="7ef6b-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7ef6b-143">值</span><span class="sxs-lookup"><span data-stu-id="7ef6b-143">Value</span></span>|<span data-ttu-id="7ef6b-144">說明</span><span class="sxs-lookup"><span data-stu-id="7ef6b-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ef6b-145">None</span><span class="sxs-lookup"><span data-stu-id="7ef6b-145">None</span></span>|<span data-ttu-id="7ef6b-146">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-146">Security is disabled.</span></span>|  
|<span data-ttu-id="7ef6b-147">基本</span><span class="sxs-lookup"><span data-stu-id="7ef6b-147">Basic</span></span>|<span data-ttu-id="7ef6b-148">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="7ef6b-149">摘要</span><span class="sxs-lookup"><span data-stu-id="7ef6b-149">Digest</span></span>|<span data-ttu-id="7ef6b-150">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="7ef6b-151">Ntlm</span><span class="sxs-lookup"><span data-stu-id="7ef6b-151">Ntlm</span></span>|<span data-ttu-id="7ef6b-152">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="7ef6b-153">Windows</span><span class="sxs-lookup"><span data-stu-id="7ef6b-153">Windows</span></span>|<span data-ttu-id="7ef6b-154">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="7ef6b-155">憑證</span><span class="sxs-lookup"><span data-stu-id="7ef6b-155">Certificate</span></span>|<span data-ttu-id="7ef6b-156">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ef6b-157">子元素</span><span class="sxs-lookup"><span data-stu-id="7ef6b-157">Child Elements</span></span>  
 <span data-ttu-id="7ef6b-158">無</span><span class="sxs-lookup"><span data-stu-id="7ef6b-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ef6b-159">父項目</span><span class="sxs-lookup"><span data-stu-id="7ef6b-159">Parent Elements</span></span>  
  
|<span data-ttu-id="7ef6b-160">項目</span><span class="sxs-lookup"><span data-stu-id="7ef6b-160">Element</span></span>|<span data-ttu-id="7ef6b-161">描述</span><span class="sxs-lookup"><span data-stu-id="7ef6b-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ef6b-162">\<security></span><span class="sxs-lookup"><span data-stu-id="7ef6b-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="7ef6b-163">表示[ \<ws2007HttpBinding >](ws2007httpbinding.md)元素的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="7ef6b-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ef6b-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ef6b-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="7ef6b-165">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="7ef6b-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7ef6b-166">繫結</span><span class="sxs-lookup"><span data-stu-id="7ef6b-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7ef6b-167">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="7ef6b-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7ef6b-168">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="7ef6b-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7ef6b-169">\<binding></span><span class="sxs-lookup"><span data-stu-id="7ef6b-169">\<binding></span></span>](../../../misc/binding.md)
