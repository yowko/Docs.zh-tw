---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 806cf8524ed1a1439ca85a4b918e8e486e5dc94b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936593"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="80246-102">\<webHttpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="80246-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="80246-103">指定以[ \<webHttpBinding >](webhttpbinding.md)設定之端點的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="80246-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
 <span data-ttu-id="80246-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80246-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80246-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="80246-105">\<bindings></span></span>  
<span data-ttu-id="80246-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="80246-106">\<webHttpBinding></span></span>  
<span data-ttu-id="80246-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="80246-107">\<binding></span></span>  
<span data-ttu-id="80246-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="80246-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80246-109">語法</span><span class="sxs-lookup"><span data-stu-id="80246-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80246-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="80246-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80246-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="80246-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80246-112">屬性</span><span class="sxs-lookup"><span data-stu-id="80246-112">Attributes</span></span>  
  
|<span data-ttu-id="80246-113">屬性</span><span class="sxs-lookup"><span data-stu-id="80246-113">Attribute</span></span>|<span data-ttu-id="80246-114">描述</span><span class="sxs-lookup"><span data-stu-id="80246-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80246-115">模式</span><span class="sxs-lookup"><span data-stu-id="80246-115">mode</span></span>|<span data-ttu-id="80246-116">指定端點是否使用傳輸層級安全性或不使用安全性。</span><span class="sxs-lookup"><span data-stu-id="80246-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="80246-117">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="80246-117">The default is `None`.</span></span> <span data-ttu-id="80246-118">此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="80246-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="80246-119">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="80246-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="80246-120">值</span><span class="sxs-lookup"><span data-stu-id="80246-120">Value</span></span>|<span data-ttu-id="80246-121">描述</span><span class="sxs-lookup"><span data-stu-id="80246-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80246-122">無</span><span class="sxs-lookup"><span data-stu-id="80246-122">None</span></span>|<span data-ttu-id="80246-123">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="80246-123">Security is disabled.</span></span>|  
|<span data-ttu-id="80246-124">Transport</span><span class="sxs-lookup"><span data-stu-id="80246-124">Transport</span></span>|<span data-ttu-id="80246-125">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="80246-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="80246-126">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="80246-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="80246-127">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="80246-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="80246-128">用戶端驗證是透過`ClientCredentialType` [ \<傳輸 >](transport-of-webhttpbinding.md)的屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="80246-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="80246-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="80246-129">TransportCredentialOnly</span></span>|<span data-ttu-id="80246-130">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="80246-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="80246-131">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="80246-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="80246-132">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="80246-132">This mode should be used with caution.</span></span> <span data-ttu-id="80246-133">它應該用於以其他方式 (例如 IPSec) 提供傳輸安全性, 而且 WCF 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="80246-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80246-134">子元素</span><span class="sxs-lookup"><span data-stu-id="80246-134">Child Elements</span></span>  
  
|<span data-ttu-id="80246-135">項目</span><span class="sxs-lookup"><span data-stu-id="80246-135">Element</span></span>|<span data-ttu-id="80246-136">描述</span><span class="sxs-lookup"><span data-stu-id="80246-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80246-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="80246-137">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="80246-138">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="80246-138">Defines the transport security settings.</span></span> <span data-ttu-id="80246-139">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="80246-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80246-140">父項目</span><span class="sxs-lookup"><span data-stu-id="80246-140">Parent Elements</span></span>  
  
|<span data-ttu-id="80246-141">項目</span><span class="sxs-lookup"><span data-stu-id="80246-141">Element</span></span>|<span data-ttu-id="80246-142">說明</span><span class="sxs-lookup"><span data-stu-id="80246-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80246-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="80246-143">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="80246-144">繫結項目, 用來設定 Windows Communication Foundation (WCF) Web 服務的端點, 以回應 HTTP 要求, 而不是 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="80246-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80246-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80246-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="80246-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="80246-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="80246-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="80246-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="80246-148">繫結</span><span class="sxs-lookup"><span data-stu-id="80246-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="80246-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="80246-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="80246-150">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="80246-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="80246-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="80246-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="80246-152">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="80246-152">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
