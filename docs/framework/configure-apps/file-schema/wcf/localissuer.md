---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 7a48cbb3a1e17ac1fc9fa9f43301ef153cdb866c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151862"
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="b803b-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="b803b-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="b803b-103">指定要用來取得安全性權杖的本機簽發者位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="b803b-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="b803b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b803b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b803b-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b803b-105">\<behaviors></span></span>  
<span data-ttu-id="b803b-106">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="b803b-106">endpointBehaviors section</span></span>  
<span data-ttu-id="b803b-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b803b-107">\<behavior></span></span>  
<span data-ttu-id="b803b-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b803b-108">\<clientCredentials></span></span>  
<span data-ttu-id="b803b-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="b803b-109">\<issuedToken></span></span>  
<span data-ttu-id="b803b-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="b803b-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b803b-111">語法</span><span class="sxs-lookup"><span data-stu-id="b803b-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b803b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b803b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b803b-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="b803b-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b803b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b803b-114">Attributes</span></span>  
  
|<span data-ttu-id="b803b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b803b-115">Attribute</span></span>|<span data-ttu-id="b803b-116">描述</span><span class="sxs-lookup"><span data-stu-id="b803b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b803b-117">address</span><span class="sxs-lookup"><span data-stu-id="b803b-117">address</span></span>|<span data-ttu-id="b803b-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="b803b-118">Required string.</span></span> <span data-ttu-id="b803b-119">指定本機簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="b803b-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="b803b-120">繫結</span><span class="sxs-lookup"><span data-stu-id="b803b-120">binding</span></span>|<span data-ttu-id="b803b-121">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="b803b-121">Optional string.</span></span> <span data-ttu-id="b803b-122">系統提供的繫結之一。</span><span class="sxs-lookup"><span data-stu-id="b803b-122">One of the system-provided bindings.</span></span> <span data-ttu-id="b803b-123">如需清單，請參閱[System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="b803b-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="b803b-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b803b-124">bindingConfiguration</span></span>|<span data-ttu-id="b803b-125">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="b803b-125">Optional string.</span></span> <span data-ttu-id="b803b-126">指定組態檔中的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="b803b-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b803b-127">子元素</span><span class="sxs-lookup"><span data-stu-id="b803b-127">Child Elements</span></span>  
  
|<span data-ttu-id="b803b-128">項目</span><span class="sxs-lookup"><span data-stu-id="b803b-128">Element</span></span>|<span data-ttu-id="b803b-129">描述</span><span class="sxs-lookup"><span data-stu-id="b803b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b803b-130">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="b803b-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b803b-131">指定本機簽發者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="b803b-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="b803b-132">\<headers></span><span class="sxs-lookup"><span data-stu-id="b803b-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="b803b-133">位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。</span><span class="sxs-lookup"><span data-stu-id="b803b-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="b803b-134">您可以使用 `add` 關鍵字將標頭加入這個集合。</span><span class="sxs-lookup"><span data-stu-id="b803b-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b803b-135">父項目</span><span class="sxs-lookup"><span data-stu-id="b803b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b803b-136">項目</span><span class="sxs-lookup"><span data-stu-id="b803b-136">Element</span></span>|<span data-ttu-id="b803b-137">描述</span><span class="sxs-lookup"><span data-stu-id="b803b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b803b-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="b803b-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="b803b-139">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="b803b-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b803b-140">備註</span><span class="sxs-lookup"><span data-stu-id="b803b-140">Remarks</span></span>  
 <span data-ttu-id="b803b-141">當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="b803b-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="b803b-142">當<xref:System.ServiceModel.WSFederationHttpBinding>並不提供的 URL 安全性權杖服務，或是聯合繫結的簽發者位址是 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或`null`，用戶端的 Windows Communication Foundation (WCF) 通道會使用所指定的值`address`和`binding`STS，以取得發行的權杖與通訊。</span><span class="sxs-lookup"><span data-stu-id="b803b-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="b803b-143">如需有關設定本機簽發者的詳細資訊，請參閱[How to:設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="b803b-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b803b-144">範例</span><span class="sxs-lookup"><span data-stu-id="b803b-144">Example</span></span>  
 <span data-ttu-id="b803b-145">下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b803b-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b803b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b803b-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="b803b-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="b803b-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b803b-148">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="b803b-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="b803b-149">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="b803b-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b803b-150">安全性行為</span><span class="sxs-lookup"><span data-stu-id="b803b-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b803b-151">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b803b-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b803b-152">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b803b-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b803b-153">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="b803b-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="b803b-154">如何：建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="b803b-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="b803b-155">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b803b-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
