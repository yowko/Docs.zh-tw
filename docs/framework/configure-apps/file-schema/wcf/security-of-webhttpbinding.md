---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 2f0bc97e10fcd72f2f33cc20730320cbbfc42dd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399758"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="c0db9-102">\<webHttpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="c0db9-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="c0db9-103">指定以[ \<webHttpBinding >](webhttpbinding.md)設定之端點的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="c0db9-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="c0db9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0db9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0db9-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0db9-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c0db9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c0db9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c0db9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c0db9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="c0db9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="c0db9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c0db9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="c0db9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0db9-110">語法</span><span class="sxs-lookup"><span data-stu-id="c0db9-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0db9-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0db9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c0db9-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0db9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0db9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c0db9-113">Attributes</span></span>  
  
|<span data-ttu-id="c0db9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c0db9-114">Attribute</span></span>|<span data-ttu-id="c0db9-115">說明</span><span class="sxs-lookup"><span data-stu-id="c0db9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0db9-116">模式</span><span class="sxs-lookup"><span data-stu-id="c0db9-116">mode</span></span>|<span data-ttu-id="c0db9-117">指定端點是否使用傳輸層級安全性或不使用安全性。</span><span class="sxs-lookup"><span data-stu-id="c0db9-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="c0db9-118">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="c0db9-118">The default is `None`.</span></span> <span data-ttu-id="c0db9-119">此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="c0db9-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c0db9-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="c0db9-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="c0db9-121">值</span><span class="sxs-lookup"><span data-stu-id="c0db9-121">Value</span></span>|<span data-ttu-id="c0db9-122">說明</span><span class="sxs-lookup"><span data-stu-id="c0db9-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0db9-123">無</span><span class="sxs-lookup"><span data-stu-id="c0db9-123">None</span></span>|<span data-ttu-id="c0db9-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="c0db9-124">Security is disabled.</span></span>|  
|<span data-ttu-id="c0db9-125">Transport</span><span class="sxs-lookup"><span data-stu-id="c0db9-125">Transport</span></span>|<span data-ttu-id="c0db9-126">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="c0db9-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="c0db9-127">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="c0db9-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="c0db9-128">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="c0db9-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="c0db9-129">用戶端驗證是透過`ClientCredentialType` [ \<傳輸 >](transport-of-webhttpbinding.md)的屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="c0db9-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="c0db9-130">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="c0db9-130">TransportCredentialOnly</span></span>|<span data-ttu-id="c0db9-131">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="c0db9-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="c0db9-132">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="c0db9-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="c0db9-133">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="c0db9-133">This mode should be used with caution.</span></span> <span data-ttu-id="c0db9-134">它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="c0db9-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0db9-135">子元素</span><span class="sxs-lookup"><span data-stu-id="c0db9-135">Child Elements</span></span>  
  
|<span data-ttu-id="c0db9-136">項目</span><span class="sxs-lookup"><span data-stu-id="c0db9-136">Element</span></span>|<span data-ttu-id="c0db9-137">描述</span><span class="sxs-lookup"><span data-stu-id="c0db9-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0db9-138">\<transport></span><span class="sxs-lookup"><span data-stu-id="c0db9-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="c0db9-139">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c0db9-139">Defines the transport security settings.</span></span> <span data-ttu-id="c0db9-140">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="c0db9-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0db9-141">父項目</span><span class="sxs-lookup"><span data-stu-id="c0db9-141">Parent Elements</span></span>  
  
|<span data-ttu-id="c0db9-142">項目</span><span class="sxs-lookup"><span data-stu-id="c0db9-142">Element</span></span>|<span data-ttu-id="c0db9-143">描述</span><span class="sxs-lookup"><span data-stu-id="c0db9-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0db9-144">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c0db9-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="c0db9-145">繫結項目，用來設定 Windows Communication Foundation （WCF） Web 服務的端點，以回應 HTTP 要求，而不是 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0db9-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0db9-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0db9-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="c0db9-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="c0db9-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c0db9-148">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="c0db9-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c0db9-149">繫結</span><span class="sxs-lookup"><span data-stu-id="c0db9-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c0db9-150">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="c0db9-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c0db9-151">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="c0db9-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c0db9-152">\<binding></span><span class="sxs-lookup"><span data-stu-id="c0db9-152">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="c0db9-153">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="c0db9-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
