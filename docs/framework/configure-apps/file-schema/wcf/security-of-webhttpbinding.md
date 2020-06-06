---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738631"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="41705-102">\<security> 的 \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="41705-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="41705-103">指定以設定之端點的安全性需求 [\<webHttpBinding>](webhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="41705-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="41705-104">語法</span><span class="sxs-lookup"><span data-stu-id="41705-104">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41705-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="41705-105">Attributes and Elements</span></span>  
 <span data-ttu-id="41705-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="41705-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41705-107">屬性</span><span class="sxs-lookup"><span data-stu-id="41705-107">Attributes</span></span>  
  
|<span data-ttu-id="41705-108">屬性</span><span class="sxs-lookup"><span data-stu-id="41705-108">Attribute</span></span>|<span data-ttu-id="41705-109">描述</span><span class="sxs-lookup"><span data-stu-id="41705-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41705-110">mode</span><span class="sxs-lookup"><span data-stu-id="41705-110">mode</span></span>|<span data-ttu-id="41705-111">指定端點是否使用傳輸層級安全性或不使用安全性。</span><span class="sxs-lookup"><span data-stu-id="41705-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="41705-112">預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="41705-112">The default is `None`.</span></span> <span data-ttu-id="41705-113">此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="41705-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="41705-114">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="41705-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="41705-115">值</span><span class="sxs-lookup"><span data-stu-id="41705-115">Value</span></span>|<span data-ttu-id="41705-116">描述</span><span class="sxs-lookup"><span data-stu-id="41705-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41705-117">None</span><span class="sxs-lookup"><span data-stu-id="41705-117">None</span></span>|<span data-ttu-id="41705-118">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="41705-118">Security is disabled.</span></span>|  
|<span data-ttu-id="41705-119">傳輸</span><span class="sxs-lookup"><span data-stu-id="41705-119">Transport</span></span>|<span data-ttu-id="41705-120">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="41705-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="41705-121">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="41705-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="41705-122">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="41705-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="41705-123">用戶端驗證是透過的 `ClientCredentialType` 屬性來控制 [\<transport>](transport-of-webhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="41705-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="41705-124">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="41705-124">TransportCredentialOnly</span></span>|<span data-ttu-id="41705-125">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="41705-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="41705-126">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="41705-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="41705-127">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="41705-127">This mode should be used with caution.</span></span> <span data-ttu-id="41705-128">它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="41705-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41705-129">子元素</span><span class="sxs-lookup"><span data-stu-id="41705-129">Child Elements</span></span>  
  
|<span data-ttu-id="41705-130">元素</span><span class="sxs-lookup"><span data-stu-id="41705-130">Element</span></span>|<span data-ttu-id="41705-131">描述</span><span class="sxs-lookup"><span data-stu-id="41705-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="41705-132">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="41705-132">Defines the transport security settings.</span></span> <span data-ttu-id="41705-133">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="41705-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41705-134">父項目</span><span class="sxs-lookup"><span data-stu-id="41705-134">Parent Elements</span></span>  
  
|<span data-ttu-id="41705-135">元素</span><span class="sxs-lookup"><span data-stu-id="41705-135">Element</span></span>|<span data-ttu-id="41705-136">描述</span><span class="sxs-lookup"><span data-stu-id="41705-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="41705-137">繫結項目，用來設定 Windows Communication Foundation （WCF） Web 服務的端點，以回應 HTTP 要求，而不是 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="41705-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41705-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41705-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="41705-139">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="41705-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="41705-140">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="41705-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="41705-141">繫結</span><span class="sxs-lookup"><span data-stu-id="41705-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="41705-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="41705-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="41705-143">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="41705-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="41705-144">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="41705-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
