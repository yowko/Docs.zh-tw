---
title: '&lt;webHttpBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dd65b488a2d3f18f2e19191f143243204c4303d4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="0c5d0-102">&lt;webHttpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="0c5d0-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="0c5d0-103">指定與設定之端點的安全性需求[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="0c5d0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0c5d0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0c5d0-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="0c5d0-105">\<bindings></span></span>  
<span data-ttu-id="0c5d0-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0c5d0-106">\<webHttpBinding></span></span>  
<span data-ttu-id="0c5d0-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="0c5d0-107">\<binding></span></span>  
<span data-ttu-id="0c5d0-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="0c5d0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c5d0-109">語法</span><span class="sxs-lookup"><span data-stu-id="0c5d0-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c5d0-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c5d0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c5d0-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c5d0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0c5d0-112">Attributes</span></span>  
  
|<span data-ttu-id="0c5d0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0c5d0-113">Attribute</span></span>|<span data-ttu-id="0c5d0-114">描述</span><span class="sxs-lookup"><span data-stu-id="0c5d0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c5d0-115">模式</span><span class="sxs-lookup"><span data-stu-id="0c5d0-115">mode</span></span>|<span data-ttu-id="0c5d0-116">指定端點是否使用傳輸層級安全性或不使用安全性。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="0c5d0-117">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-117">The default is `None`.</span></span> <span data-ttu-id="0c5d0-118">此屬性的型別為 <xref:System.ServiceModel.WebHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0c5d0-119">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="0c5d0-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="0c5d0-120">值</span><span class="sxs-lookup"><span data-stu-id="0c5d0-120">Value</span></span>|<span data-ttu-id="0c5d0-121">描述</span><span class="sxs-lookup"><span data-stu-id="0c5d0-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c5d0-122">無</span><span class="sxs-lookup"><span data-stu-id="0c5d0-122">None</span></span>|<span data-ttu-id="0c5d0-123">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-123">Security is disabled.</span></span>|  
|<span data-ttu-id="0c5d0-124">Transport</span><span class="sxs-lookup"><span data-stu-id="0c5d0-124">Transport</span></span>|<span data-ttu-id="0c5d0-125">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="0c5d0-126">而服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="0c5d0-127">HTTPS 會用來完全保護訊息安全，而且用戶端會使用服務的 SSL 憑證來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="0c5d0-128">用戶端驗證透過`ClientCredentialType`屬性[\<傳輸 >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="0c5d0-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="0c5d0-129">TransportCredentialOnly</span></span>|<span data-ttu-id="0c5d0-130">這個模式不提供訊息完整性和機密性，</span><span class="sxs-lookup"><span data-stu-id="0c5d0-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="0c5d0-131">但會提供 HTTP 架構的用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="0c5d0-132">請謹慎使用這個模式，</span><span class="sxs-lookup"><span data-stu-id="0c5d0-132">This mode should be used with caution.</span></span> <span data-ttu-id="0c5d0-133">它應使用在以其他方式 (如 IPSec) 提供傳輸安全性，且 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 基礎結構只提供用戶端驗證的環境中。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c5d0-134">子項目</span><span class="sxs-lookup"><span data-stu-id="0c5d0-134">Child Elements</span></span>  
  
|<span data-ttu-id="0c5d0-135">項目</span><span class="sxs-lookup"><span data-stu-id="0c5d0-135">Element</span></span>|<span data-ttu-id="0c5d0-136">描述</span><span class="sxs-lookup"><span data-stu-id="0c5d0-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c5d0-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="0c5d0-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="0c5d0-138">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-138">Defines the transport security settings.</span></span> <span data-ttu-id="0c5d0-139">這個項目對應至 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型別。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c5d0-140">父項目</span><span class="sxs-lookup"><span data-stu-id="0c5d0-140">Parent Elements</span></span>  
  
|<span data-ttu-id="0c5d0-141">項目</span><span class="sxs-lookup"><span data-stu-id="0c5d0-141">Element</span></span>|<span data-ttu-id="0c5d0-142">描述</span><span class="sxs-lookup"><span data-stu-id="0c5d0-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c5d0-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0c5d0-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="0c5d0-144">用來設定端點，Windows Communication Foundation (WCF) Web 服務會回應 HTTP 要求，而非 SOAP 訊息的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c5d0-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c5d0-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="0c5d0-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="0c5d0-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0c5d0-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="0c5d0-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="0c5d0-148">繫結</span><span class="sxs-lookup"><span data-stu-id="0c5d0-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0c5d0-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0c5d0-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0c5d0-150">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="0c5d0-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0c5d0-151">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="0c5d0-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="0c5d0-152">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="0c5d0-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
