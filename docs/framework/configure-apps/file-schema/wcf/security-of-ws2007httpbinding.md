---
title: <security> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: 48b49bf69f791f90ed5b2eea8e6d412438cd9519
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169839"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="e032a-102">\<security> 的 \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="e032a-102">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="e032a-103">表示與元素搭配使用的安全性設定 [\<ws2007HttpBinding>](ws2007httpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e032a-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="e032a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e032a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e032a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e032a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e032a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e032a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e032a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e032a-107">Attributes</span></span>  
  
|<span data-ttu-id="e032a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e032a-108">Attribute</span></span>|<span data-ttu-id="e032a-109">描述</span><span class="sxs-lookup"><span data-stu-id="e032a-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="e032a-110">參數.</span><span class="sxs-lookup"><span data-stu-id="e032a-110">-   Optional.</span></span> <span data-ttu-id="e032a-111">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="e032a-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e032a-112">預設值為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="e032a-112">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="e032a-113">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="e032a-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e032a-114">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="e032a-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="e032a-115">值</span><span class="sxs-lookup"><span data-stu-id="e032a-115">Value</span></span>|<span data-ttu-id="e032a-116">描述</span><span class="sxs-lookup"><span data-stu-id="e032a-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="e032a-117">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="e032a-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="e032a-118">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="e032a-118">Security is provided using HTTPS.</span></span> <span data-ttu-id="e032a-119">而服務必須使用安全通訊端層 (SSL) 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="e032a-119">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="e032a-120">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="e032a-120">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="e032a-121">用戶端驗證是透過元素的 `ClientCredentials` 屬性來控制 [\<transport>](transport-of-ws2007httpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e032a-121">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="e032a-122">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="e032a-122">Security is provided using SOAP message security.</span></span> <span data-ttu-id="e032a-123">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="e032a-123">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="e032a-124">這個模式透過 <xref:System.ServiceModel.Security.SecurityMessageProperty> 提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="e032a-124">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="e032a-125">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="e032a-125">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="e032a-126">在這個模式中，HTTPS 會提供完整性、機密性和伺服器驗證，而 SOAP 訊息安全性會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="e032a-126">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="e032a-127">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="e032a-127">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e032a-128">子元素</span><span class="sxs-lookup"><span data-stu-id="e032a-128">Child Elements</span></span>  
  
|<span data-ttu-id="e032a-129">項目</span><span class="sxs-lookup"><span data-stu-id="e032a-129">Element</span></span>|<span data-ttu-id="e032a-130">描述</span><span class="sxs-lookup"><span data-stu-id="e032a-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="e032a-131">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e032a-131">Defines the transport security settings.</span></span> <span data-ttu-id="e032a-132">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="e032a-132">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="e032a-133">當模式設定為 Transport，才會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="e032a-133">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="e032a-134">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e032a-134">Defines the security settings for the message.</span></span> <span data-ttu-id="e032a-135">這個項目對應至 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="e032a-135">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="e032a-136">當模式設定為 Transport，就不會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="e032a-136">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e032a-137">父項目</span><span class="sxs-lookup"><span data-stu-id="e032a-137">Parent Elements</span></span>  
  
|<span data-ttu-id="e032a-138">項目</span><span class="sxs-lookup"><span data-stu-id="e032a-138">Element</span></span>|<span data-ttu-id="e032a-139">描述</span><span class="sxs-lookup"><span data-stu-id="e032a-139">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="e032a-140">HTTP 傳輸應用程式的安全繫結。</span><span class="sxs-lookup"><span data-stu-id="e032a-140">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e032a-141">備註</span><span class="sxs-lookup"><span data-stu-id="e032a-141">Remarks</span></span>  

 <span data-ttu-id="e032a-142">這個項目主要是用來與實作 WS-\* 規格的服務進行交互操作。</span><span class="sxs-lookup"><span data-stu-id="e032a-142">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="e032a-143">此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="e032a-143">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e032a-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e032a-144">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="e032a-145">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="e032a-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e032a-146">繫結</span><span class="sxs-lookup"><span data-stu-id="e032a-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e032a-147">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e032a-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e032a-148">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e032a-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
