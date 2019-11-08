---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738631"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="f15c6-102">\<webHttpBinding 的 \<安全性 > ></span><span class="sxs-lookup"><span data-stu-id="f15c6-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="f15c6-103">指定以[\<webHttpBinding >](webhttpbinding.md)設定之端點的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="f15c6-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="f15c6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f15c6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f15c6-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="f15c6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f15c6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="f15c6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f15c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f15c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="f15c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="f15c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f15c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="f15c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15c6-110">語法</span><span class="sxs-lookup"><span data-stu-id="f15c6-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f15c6-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f15c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f15c6-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f15c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f15c6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f15c6-113">Attributes</span></span>  
  
|<span data-ttu-id="f15c6-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f15c6-114">Attribute</span></span>|<span data-ttu-id="f15c6-115">描述</span><span class="sxs-lookup"><span data-stu-id="f15c6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f15c6-116">模式</span><span class="sxs-lookup"><span data-stu-id="f15c6-116">mode</span></span>|<span data-ttu-id="f15c6-117">指定端點是否使用傳輸層級安全性或不使用安全性。</span><span class="sxs-lookup"><span data-stu-id="f15c6-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="f15c6-118">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="f15c6-118">The default is `None`.</span></span> <span data-ttu-id="f15c6-119">此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="f15c6-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f15c6-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="f15c6-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="f15c6-121">值</span><span class="sxs-lookup"><span data-stu-id="f15c6-121">Value</span></span>|<span data-ttu-id="f15c6-122">描述</span><span class="sxs-lookup"><span data-stu-id="f15c6-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f15c6-123">None</span><span class="sxs-lookup"><span data-stu-id="f15c6-123">None</span></span>|<span data-ttu-id="f15c6-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="f15c6-124">Security is disabled.</span></span>|  
|<span data-ttu-id="f15c6-125">Transport</span><span class="sxs-lookup"><span data-stu-id="f15c6-125">Transport</span></span>|<span data-ttu-id="f15c6-126">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="f15c6-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="f15c6-127">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="f15c6-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="f15c6-128">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="f15c6-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="f15c6-129">用戶端驗證是透過[\<傳輸 >](transport-of-webhttpbinding.md)的 `ClientCredentialType` 屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="f15c6-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="f15c6-130">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="f15c6-130">TransportCredentialOnly</span></span>|<span data-ttu-id="f15c6-131">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="f15c6-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f15c6-132">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="f15c6-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="f15c6-133">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="f15c6-133">This mode should be used with caution.</span></span> <span data-ttu-id="f15c6-134">它應該用於以其他方式（例如 IPSec）提供傳輸安全性，而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="f15c6-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f15c6-135">子項目</span><span class="sxs-lookup"><span data-stu-id="f15c6-135">Child Elements</span></span>  
  
|<span data-ttu-id="f15c6-136">項目</span><span class="sxs-lookup"><span data-stu-id="f15c6-136">Element</span></span>|<span data-ttu-id="f15c6-137">描述</span><span class="sxs-lookup"><span data-stu-id="f15c6-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f15c6-138">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="f15c6-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="f15c6-139">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="f15c6-139">Defines the transport security settings.</span></span> <span data-ttu-id="f15c6-140">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="f15c6-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f15c6-141">父項目</span><span class="sxs-lookup"><span data-stu-id="f15c6-141">Parent Elements</span></span>  
  
|<span data-ttu-id="f15c6-142">項目</span><span class="sxs-lookup"><span data-stu-id="f15c6-142">Element</span></span>|<span data-ttu-id="f15c6-143">描述</span><span class="sxs-lookup"><span data-stu-id="f15c6-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f15c6-144">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f15c6-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="f15c6-145">繫結項目，用來設定 Windows Communication Foundation （WCF） Web 服務的端點，以回應 HTTP 要求，而不是 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="f15c6-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f15c6-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="f15c6-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="f15c6-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="f15c6-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f15c6-148">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="f15c6-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f15c6-149">繫結</span><span class="sxs-lookup"><span data-stu-id="f15c6-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f15c6-150">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="f15c6-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f15c6-151">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="f15c6-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f15c6-152">\<binding ></span><span class="sxs-lookup"><span data-stu-id="f15c6-152">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="f15c6-153">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="f15c6-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
