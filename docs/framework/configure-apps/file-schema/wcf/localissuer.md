---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 9a51387cd75d57a6828ecde1dcd788b056f7e27a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766398"
---
# <a name="localissuer"></a><span data-ttu-id="2b5a0-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="2b5a0-101">\<localIssuer></span></span>
<span data-ttu-id="2b5a0-102">指定要用來取得安全性權杖的本機簽發者位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="2b5a0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2b5a0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2b5a0-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="2b5a0-104">\<behaviors></span></span>  
<span data-ttu-id="2b5a0-105">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="2b5a0-105">endpointBehaviors section</span></span>  
<span data-ttu-id="2b5a0-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2b5a0-106">\<behavior></span></span>  
<span data-ttu-id="2b5a0-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="2b5a0-107">\<clientCredentials></span></span>  
<span data-ttu-id="2b5a0-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="2b5a0-108">\<issuedToken></span></span>  
<span data-ttu-id="2b5a0-109">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="2b5a0-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b5a0-110">語法</span><span class="sxs-lookup"><span data-stu-id="2b5a0-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b5a0-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b5a0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2b5a0-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="2b5a0-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b5a0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2b5a0-113">Attributes</span></span>  
  
|<span data-ttu-id="2b5a0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2b5a0-114">Attribute</span></span>|<span data-ttu-id="2b5a0-115">描述</span><span class="sxs-lookup"><span data-stu-id="2b5a0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b5a0-116">位址</span><span class="sxs-lookup"><span data-stu-id="2b5a0-116">address</span></span>|<span data-ttu-id="2b5a0-117">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-117">Required string.</span></span> <span data-ttu-id="2b5a0-118">指定本機簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="2b5a0-119">繫結</span><span class="sxs-lookup"><span data-stu-id="2b5a0-119">binding</span></span>|<span data-ttu-id="2b5a0-120">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-120">Optional string.</span></span> <span data-ttu-id="2b5a0-121">系統提供的繫結之一。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-121">One of the system-provided bindings.</span></span> <span data-ttu-id="2b5a0-122">如需清單，請參閱[System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-122">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="2b5a0-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b5a0-123">bindingConfiguration</span></span>|<span data-ttu-id="2b5a0-124">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-124">Optional string.</span></span> <span data-ttu-id="2b5a0-125">指定組態檔中的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b5a0-126">子元素</span><span class="sxs-lookup"><span data-stu-id="2b5a0-126">Child Elements</span></span>  
  
|<span data-ttu-id="2b5a0-127">項目</span><span class="sxs-lookup"><span data-stu-id="2b5a0-127">Element</span></span>|<span data-ttu-id="2b5a0-128">描述</span><span class="sxs-lookup"><span data-stu-id="2b5a0-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b5a0-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="2b5a0-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2b5a0-130">指定本機簽發者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="2b5a0-131">\<headers></span><span class="sxs-lookup"><span data-stu-id="2b5a0-131">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="2b5a0-132">位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="2b5a0-133">您可以使用 `add` 關鍵字將標頭加入這個集合。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b5a0-134">父項目</span><span class="sxs-lookup"><span data-stu-id="2b5a0-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2b5a0-135">項目</span><span class="sxs-lookup"><span data-stu-id="2b5a0-135">Element</span></span>|<span data-ttu-id="2b5a0-136">描述</span><span class="sxs-lookup"><span data-stu-id="2b5a0-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b5a0-137">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="2b5a0-137">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="2b5a0-138">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b5a0-139">備註</span><span class="sxs-lookup"><span data-stu-id="2b5a0-139">Remarks</span></span>  
 <span data-ttu-id="2b5a0-140">當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="2b5a0-141">當<xref:System.ServiceModel.WSFederationHttpBinding>並不提供的 URL 安全性權杖服務，或是聯合繫結的簽發者位址是 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或`null`，用戶端的 Windows Communication Foundation (WCF) 通道會使用所指定的值`address`和`binding`STS，以取得發行的權杖與通訊。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="2b5a0-142">如需有關設定本機簽發者的詳細資訊，請參閱[How to:設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b5a0-143">範例</span><span class="sxs-lookup"><span data-stu-id="2b5a0-143">Example</span></span>  
 <span data-ttu-id="2b5a0-144">下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b5a0-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b5a0-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="2b5a0-146">安全性行為</span><span class="sxs-lookup"><span data-stu-id="2b5a0-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2b5a0-147">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="2b5a0-147">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="2b5a0-148">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="2b5a0-148">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2b5a0-149">安全性行為</span><span class="sxs-lookup"><span data-stu-id="2b5a0-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2b5a0-150">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="2b5a0-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2b5a0-151">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2b5a0-151">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2b5a0-152">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="2b5a0-152">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="2b5a0-153">如何：建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="2b5a0-153">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="2b5a0-154">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="2b5a0-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
