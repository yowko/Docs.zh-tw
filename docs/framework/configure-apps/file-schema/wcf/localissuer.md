---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8836d9e57dd7c4d9cfdc20c5e4856e384e6d67b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="991c6-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="991c6-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="991c6-103">指定要用來取得安全性權杖的本機簽發者位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="991c6-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="991c6-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="991c6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="991c6-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="991c6-105">\<behaviors></span></span>  
<span data-ttu-id="991c6-106">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="991c6-106">endpointBehaviors section</span></span>  
<span data-ttu-id="991c6-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="991c6-107">\<behavior></span></span>  
<span data-ttu-id="991c6-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="991c6-108">\<clientCredentials></span></span>  
<span data-ttu-id="991c6-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="991c6-109">\<issuedToken></span></span>  
<span data-ttu-id="991c6-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="991c6-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991c6-111">語法</span><span class="sxs-lookup"><span data-stu-id="991c6-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="991c6-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="991c6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="991c6-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="991c6-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="991c6-114">屬性</span><span class="sxs-lookup"><span data-stu-id="991c6-114">Attributes</span></span>  
  
|<span data-ttu-id="991c6-115">屬性</span><span class="sxs-lookup"><span data-stu-id="991c6-115">Attribute</span></span>|<span data-ttu-id="991c6-116">描述</span><span class="sxs-lookup"><span data-stu-id="991c6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="991c6-117">address</span><span class="sxs-lookup"><span data-stu-id="991c6-117">address</span></span>|<span data-ttu-id="991c6-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="991c6-118">Required string.</span></span> <span data-ttu-id="991c6-119">指定本機簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="991c6-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="991c6-120">繫結</span><span class="sxs-lookup"><span data-stu-id="991c6-120">binding</span></span>|<span data-ttu-id="991c6-121">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="991c6-121">Optional string.</span></span> <span data-ttu-id="991c6-122">系統提供的繫結之一。</span><span class="sxs-lookup"><span data-stu-id="991c6-122">One of the system-provided bindings.</span></span> <span data-ttu-id="991c6-123">如需清單，請參閱[之繫結](../../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="991c6-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="991c6-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="991c6-124">bindingConfiguration</span></span>|<span data-ttu-id="991c6-125">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="991c6-125">Optional string.</span></span> <span data-ttu-id="991c6-126">指定組態檔中的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="991c6-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="991c6-127">子元素</span><span class="sxs-lookup"><span data-stu-id="991c6-127">Child Elements</span></span>  
  
|<span data-ttu-id="991c6-128">項目</span><span class="sxs-lookup"><span data-stu-id="991c6-128">Element</span></span>|<span data-ttu-id="991c6-129">說明</span><span class="sxs-lookup"><span data-stu-id="991c6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="991c6-130">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="991c6-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="991c6-131">指定本機簽發者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="991c6-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="991c6-132">\<標頭 ></span><span class="sxs-lookup"><span data-stu-id="991c6-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="991c6-133">位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。</span><span class="sxs-lookup"><span data-stu-id="991c6-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="991c6-134">您可以使用 `add` 關鍵字將標頭加入這個集合。</span><span class="sxs-lookup"><span data-stu-id="991c6-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="991c6-135">父項目</span><span class="sxs-lookup"><span data-stu-id="991c6-135">Parent Elements</span></span>  
  
|<span data-ttu-id="991c6-136">項目</span><span class="sxs-lookup"><span data-stu-id="991c6-136">Element</span></span>|<span data-ttu-id="991c6-137">說明</span><span class="sxs-lookup"><span data-stu-id="991c6-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="991c6-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="991c6-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="991c6-139">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="991c6-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="991c6-140">備註</span><span class="sxs-lookup"><span data-stu-id="991c6-140">Remarks</span></span>  
 <span data-ttu-id="991c6-141">當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="991c6-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="991c6-142">當 <xref:System.ServiceModel.WSFederationHttpBinding> 未提供該安全性權杖服務的 URL，或是聯合繫結的簽發者位址為 http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous 或 `null` 時，用戶端的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 通道會使用 `address` 和 `binding` 指定的值與 STS 通訊，以取得已核發的權仗。</span><span class="sxs-lookup"><span data-stu-id="991c6-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="991c6-143">如需有關設定本機簽發者的詳細資訊，請參閱[How to： 設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="991c6-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="991c6-144">範例</span><span class="sxs-lookup"><span data-stu-id="991c6-144">Example</span></span>  
 <span data-ttu-id="991c6-145">下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。</span><span class="sxs-lookup"><span data-stu-id="991c6-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="991c6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="991c6-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="991c6-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="991c6-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="991c6-148">如何： 設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="991c6-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="991c6-149">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="991c6-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="991c6-150">安全性行為</span><span class="sxs-lookup"><span data-stu-id="991c6-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="991c6-151">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="991c6-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="991c6-152">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="991c6-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="991c6-153">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="991c6-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="991c6-154">如何： 建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="991c6-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="991c6-155">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="991c6-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
