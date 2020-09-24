---
title: <transport> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 60e8758d653848176ca3f287e253bd7990e78470
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162045"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="81623-102">\<transport> 的 \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="81623-102">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="81623-103">定義 HTTP 傳輸的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="81623-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="81623-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="81623-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="81623-105">類型</span><span class="sxs-lookup"><span data-stu-id="81623-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81623-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="81623-106">Attributes and Elements</span></span>  

 <span data-ttu-id="81623-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="81623-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81623-108">屬性</span><span class="sxs-lookup"><span data-stu-id="81623-108">Attributes</span></span>  
  
|<span data-ttu-id="81623-109">屬性</span><span class="sxs-lookup"><span data-stu-id="81623-109">Attribute</span></span>|<span data-ttu-id="81623-110">描述</span><span class="sxs-lookup"><span data-stu-id="81623-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="81623-111">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="81623-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="81623-112">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="81623-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="81623-113">指定用來對網域 Proxy 驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="81623-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="81623-114">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="81623-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="81623-115">摘要式或基本驗證的驗證領域。</span><span class="sxs-lookup"><span data-stu-id="81623-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="81623-116">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="81623-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="81623-117">驗證領域至少會指定負責執行驗證之主機的名稱，</span><span class="sxs-lookup"><span data-stu-id="81623-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="81623-118">也可以指定具有存取權之使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="81623-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="81623-119">使用者可以查詢驗證領域，判斷其中可以使用的一組使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="81623-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="81623-120">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="81623-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="81623-121">值</span><span class="sxs-lookup"><span data-stu-id="81623-121">Value</span></span>|<span data-ttu-id="81623-122">描述</span><span class="sxs-lookup"><span data-stu-id="81623-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81623-123">無</span><span class="sxs-lookup"><span data-stu-id="81623-123">None</span></span>|<span data-ttu-id="81623-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="81623-124">Security is disabled.</span></span>|  
|<span data-ttu-id="81623-125">基本</span><span class="sxs-lookup"><span data-stu-id="81623-125">Basic</span></span>|<span data-ttu-id="81623-126">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="81623-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="81623-127">Digest</span><span class="sxs-lookup"><span data-stu-id="81623-127">Digest</span></span>|<span data-ttu-id="81623-128">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="81623-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="81623-129">Ntlm</span><span class="sxs-lookup"><span data-stu-id="81623-129">Ntlm</span></span>|<span data-ttu-id="81623-130">使用 NTLM 驗證做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="81623-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="81623-131">Windows</span><span class="sxs-lookup"><span data-stu-id="81623-131">Windows</span></span>|<span data-ttu-id="81623-132">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="81623-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="81623-133">憑證</span><span class="sxs-lookup"><span data-stu-id="81623-133">Certificate</span></span>|<span data-ttu-id="81623-134">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="81623-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="81623-135">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="81623-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="81623-136">值</span><span class="sxs-lookup"><span data-stu-id="81623-136">Value</span></span>|<span data-ttu-id="81623-137">描述</span><span class="sxs-lookup"><span data-stu-id="81623-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81623-138">無</span><span class="sxs-lookup"><span data-stu-id="81623-138">None</span></span>|<span data-ttu-id="81623-139">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="81623-139">Security is disabled.</span></span>|  
|<span data-ttu-id="81623-140">基本</span><span class="sxs-lookup"><span data-stu-id="81623-140">Basic</span></span>|<span data-ttu-id="81623-141">使用基本驗證。</span><span class="sxs-lookup"><span data-stu-id="81623-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="81623-142">Digest</span><span class="sxs-lookup"><span data-stu-id="81623-142">Digest</span></span>|<span data-ttu-id="81623-143">使用摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="81623-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="81623-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="81623-144">Ntlm</span></span>|<span data-ttu-id="81623-145">使用 NTLM 做為 Windows 網域的後援。</span><span class="sxs-lookup"><span data-stu-id="81623-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="81623-146">Windows</span><span class="sxs-lookup"><span data-stu-id="81623-146">Windows</span></span>|<span data-ttu-id="81623-147">使用整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="81623-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="81623-148">憑證</span><span class="sxs-lookup"><span data-stu-id="81623-148">Certificate</span></span>|<span data-ttu-id="81623-149">使用 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="81623-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81623-150">子元素</span><span class="sxs-lookup"><span data-stu-id="81623-150">Child Elements</span></span>  

 <span data-ttu-id="81623-151">無</span><span class="sxs-lookup"><span data-stu-id="81623-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81623-152">父項目</span><span class="sxs-lookup"><span data-stu-id="81623-152">Parent Elements</span></span>  
  
|<span data-ttu-id="81623-153">項目</span><span class="sxs-lookup"><span data-stu-id="81623-153">Element</span></span>|<span data-ttu-id="81623-154">描述</span><span class="sxs-lookup"><span data-stu-id="81623-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="81623-155">代表專案的安全性功能 [\<ws2007HttpBinding>](ws2007httpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="81623-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81623-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81623-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="81623-157">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="81623-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="81623-158">繫結</span><span class="sxs-lookup"><span data-stu-id="81623-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81623-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="81623-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81623-160">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="81623-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
