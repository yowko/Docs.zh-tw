---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 60b863a0a2a846a60dde2e4b323a305b5096b1cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169891"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="c45cb-102">\<security> 的 \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c45cb-102">\<security> of \<webHttpBinding></span></span>

<span data-ttu-id="c45cb-103">指定以設定之端點的安全性需求 [\<webHttpBinding>](webhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="c45cb-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="c45cb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c45cb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c45cb-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c45cb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c45cb-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c45cb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c45cb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c45cb-107">Attributes</span></span>  
  
|<span data-ttu-id="c45cb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c45cb-108">Attribute</span></span>|<span data-ttu-id="c45cb-109">描述</span><span class="sxs-lookup"><span data-stu-id="c45cb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c45cb-110">mode</span><span class="sxs-lookup"><span data-stu-id="c45cb-110">mode</span></span>|<span data-ttu-id="c45cb-111">指定端點是否使用傳輸層級安全性或不使用安全性。</span><span class="sxs-lookup"><span data-stu-id="c45cb-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="c45cb-112">預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="c45cb-112">The default is `None`.</span></span> <span data-ttu-id="c45cb-113">此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="c45cb-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c45cb-114">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="c45cb-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="c45cb-115">值</span><span class="sxs-lookup"><span data-stu-id="c45cb-115">Value</span></span>|<span data-ttu-id="c45cb-116">描述</span><span class="sxs-lookup"><span data-stu-id="c45cb-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c45cb-117">無</span><span class="sxs-lookup"><span data-stu-id="c45cb-117">None</span></span>|<span data-ttu-id="c45cb-118">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="c45cb-118">Security is disabled.</span></span>|  
|<span data-ttu-id="c45cb-119">傳輸</span><span class="sxs-lookup"><span data-stu-id="c45cb-119">Transport</span></span>|<span data-ttu-id="c45cb-120">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="c45cb-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="c45cb-121">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="c45cb-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="c45cb-122">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="c45cb-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="c45cb-123">用戶端驗證是透過的屬性來控制 `ClientCredentialType` [\<transport>](transport-of-webhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="c45cb-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="c45cb-124">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="c45cb-124">TransportCredentialOnly</span></span>|<span data-ttu-id="c45cb-125">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="c45cb-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="c45cb-126">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="c45cb-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="c45cb-127">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="c45cb-127">This mode should be used with caution.</span></span> <span data-ttu-id="c45cb-128">它應該用於以其他方式提供傳輸安全性的環境中 (例如 IPSec) ，而且只有 WCF 基礎結構會提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="c45cb-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c45cb-129">子元素</span><span class="sxs-lookup"><span data-stu-id="c45cb-129">Child Elements</span></span>  
  
|<span data-ttu-id="c45cb-130">項目</span><span class="sxs-lookup"><span data-stu-id="c45cb-130">Element</span></span>|<span data-ttu-id="c45cb-131">描述</span><span class="sxs-lookup"><span data-stu-id="c45cb-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="c45cb-132">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c45cb-132">Defines the transport security settings.</span></span> <span data-ttu-id="c45cb-133">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="c45cb-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c45cb-134">父項目</span><span class="sxs-lookup"><span data-stu-id="c45cb-134">Parent Elements</span></span>  
  
|<span data-ttu-id="c45cb-135">項目</span><span class="sxs-lookup"><span data-stu-id="c45cb-135">Element</span></span>|<span data-ttu-id="c45cb-136">描述</span><span class="sxs-lookup"><span data-stu-id="c45cb-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="c45cb-137">繫結項目，用於設定 Windows Communication Foundation (WCF) Web 服務的端點，這些服務會回應 HTTP 要求，而非 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="c45cb-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c45cb-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c45cb-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="c45cb-139">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="c45cb-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c45cb-140">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="c45cb-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c45cb-141">繫結</span><span class="sxs-lookup"><span data-stu-id="c45cb-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c45cb-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="c45cb-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c45cb-143">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="c45cb-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="c45cb-144">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="c45cb-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
