---
title: <security> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736397"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="0adf3-102">\<ws2007HttpBinding 的 \<安全性 > ></span><span class="sxs-lookup"><span data-stu-id="0adf3-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="0adf3-103">表示與[\<ws2007HttpBinding >](ws2007httpbinding.md)元素搭配使用的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0adf3-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="0adf3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0adf3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0adf3-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0adf3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0adf3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="0adf3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0adf3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0adf3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="0adf3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="0adf3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="0adf3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="0adf3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0adf3-110">語法</span><span class="sxs-lookup"><span data-stu-id="0adf3-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0adf3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0adf3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0adf3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0adf3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0adf3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0adf3-113">Attributes</span></span>  
  
|<span data-ttu-id="0adf3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0adf3-114">Attribute</span></span>|<span data-ttu-id="0adf3-115">描述</span><span class="sxs-lookup"><span data-stu-id="0adf3-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="0adf3-116">選擇性.</span><span class="sxs-lookup"><span data-stu-id="0adf3-116">-   Optional.</span></span> <span data-ttu-id="0adf3-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="0adf3-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="0adf3-118">預設為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="0adf3-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="0adf3-119">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="0adf3-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0adf3-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="0adf3-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="0adf3-121">值</span><span class="sxs-lookup"><span data-stu-id="0adf3-121">Value</span></span>|<span data-ttu-id="0adf3-122">描述</span><span class="sxs-lookup"><span data-stu-id="0adf3-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="0adf3-123">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="0adf3-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="0adf3-124">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="0adf3-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="0adf3-125">而服務必須使用安全通訊端層 (SSL) 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="0adf3-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="0adf3-126">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="0adf3-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="0adf3-127">用戶端驗證是透過[\<transport >](transport-of-ws2007httpbinding.md)元素的 `ClientCredentials` 屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="0adf3-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="0adf3-128">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="0adf3-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="0adf3-129">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="0adf3-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="0adf3-130">這個模式透過 <xref:System.ServiceModel.Security.SecurityMessageProperty> 提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="0adf3-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="0adf3-131">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="0adf3-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="0adf3-132">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="0adf3-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="0adf3-133">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="0adf3-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0adf3-134">子項目</span><span class="sxs-lookup"><span data-stu-id="0adf3-134">Child Elements</span></span>  
  
|<span data-ttu-id="0adf3-135">項目</span><span class="sxs-lookup"><span data-stu-id="0adf3-135">Element</span></span>|<span data-ttu-id="0adf3-136">描述</span><span class="sxs-lookup"><span data-stu-id="0adf3-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0adf3-137">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="0adf3-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="0adf3-138">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0adf3-138">Defines the transport security settings.</span></span> <span data-ttu-id="0adf3-139">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="0adf3-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="0adf3-140">當模式設定為 Transport，才會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="0adf3-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="0adf3-141">\<message ></span><span class="sxs-lookup"><span data-stu-id="0adf3-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="0adf3-142">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0adf3-142">Defines the security settings for the message.</span></span> <span data-ttu-id="0adf3-143">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="0adf3-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="0adf3-144">當模式設定為 Transport，就不會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="0adf3-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0adf3-145">父項目</span><span class="sxs-lookup"><span data-stu-id="0adf3-145">Parent Elements</span></span>  
  
|<span data-ttu-id="0adf3-146">項目</span><span class="sxs-lookup"><span data-stu-id="0adf3-146">Element</span></span>|<span data-ttu-id="0adf3-147">描述</span><span class="sxs-lookup"><span data-stu-id="0adf3-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0adf3-148">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0adf3-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="0adf3-149">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="0adf3-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0adf3-150">備註</span><span class="sxs-lookup"><span data-stu-id="0adf3-150">Remarks</span></span>  
 <span data-ttu-id="0adf3-151">這個項目主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="0adf3-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="0adf3-152">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="0adf3-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adf3-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="0adf3-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="0adf3-154">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="0adf3-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0adf3-155">繫結</span><span class="sxs-lookup"><span data-stu-id="0adf3-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0adf3-156">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0adf3-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0adf3-157">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="0adf3-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0adf3-158">\<binding ></span><span class="sxs-lookup"><span data-stu-id="0adf3-158">\<binding></span></span>](bindings.md)
