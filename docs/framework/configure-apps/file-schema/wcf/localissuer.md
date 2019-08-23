---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931732"
---
# <a name="localissuer"></a><span data-ttu-id="b5c78-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="b5c78-101">\<localIssuer></span></span>
<span data-ttu-id="b5c78-102">指定要用來取得安全性權杖的本機簽發者位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="b5c78-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="b5c78-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b5c78-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b5c78-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b5c78-104">\<behaviors></span></span>  
<span data-ttu-id="b5c78-105">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="b5c78-105">endpointBehaviors section</span></span>  
<span data-ttu-id="b5c78-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b5c78-106">\<behavior></span></span>  
<span data-ttu-id="b5c78-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b5c78-107">\<clientCredentials></span></span>  
<span data-ttu-id="b5c78-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="b5c78-108">\<issuedToken></span></span>  
<span data-ttu-id="b5c78-109">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="b5c78-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c78-110">語法</span><span class="sxs-lookup"><span data-stu-id="b5c78-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5c78-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b5c78-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b5c78-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="b5c78-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5c78-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b5c78-113">Attributes</span></span>  
  
|<span data-ttu-id="b5c78-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b5c78-114">Attribute</span></span>|<span data-ttu-id="b5c78-115">描述</span><span class="sxs-lookup"><span data-stu-id="b5c78-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5c78-116">位址</span><span class="sxs-lookup"><span data-stu-id="b5c78-116">address</span></span>|<span data-ttu-id="b5c78-117">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="b5c78-117">Required string.</span></span> <span data-ttu-id="b5c78-118">指定本機簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="b5c78-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="b5c78-119">繫結</span><span class="sxs-lookup"><span data-stu-id="b5c78-119">binding</span></span>|<span data-ttu-id="b5c78-120">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="b5c78-120">Optional string.</span></span> <span data-ttu-id="b5c78-121">系統提供的繫結之一。</span><span class="sxs-lookup"><span data-stu-id="b5c78-121">One of the system-provided bindings.</span></span> <span data-ttu-id="b5c78-122">如需清單, 請參閱[系統提供](../../../wcf/system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="b5c78-122">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="b5c78-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b5c78-123">bindingConfiguration</span></span>|<span data-ttu-id="b5c78-124">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="b5c78-124">Optional string.</span></span> <span data-ttu-id="b5c78-125">指定組態檔中的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="b5c78-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5c78-126">子元素</span><span class="sxs-lookup"><span data-stu-id="b5c78-126">Child Elements</span></span>  
  
|<span data-ttu-id="b5c78-127">項目</span><span class="sxs-lookup"><span data-stu-id="b5c78-127">Element</span></span>|<span data-ttu-id="b5c78-128">描述</span><span class="sxs-lookup"><span data-stu-id="b5c78-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5c78-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="b5c78-129">\<identity></span></span>](identity.md)|<span data-ttu-id="b5c78-130">指定本機簽發者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="b5c78-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="b5c78-131">\<headers></span><span class="sxs-lookup"><span data-stu-id="b5c78-131">\<headers></span></span>](headers-element.md)|<span data-ttu-id="b5c78-132">位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。</span><span class="sxs-lookup"><span data-stu-id="b5c78-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="b5c78-133">您可以使用 `add` 關鍵字將標頭加入這個集合。</span><span class="sxs-lookup"><span data-stu-id="b5c78-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5c78-134">父項目</span><span class="sxs-lookup"><span data-stu-id="b5c78-134">Parent Elements</span></span>  
  
|<span data-ttu-id="b5c78-135">項目</span><span class="sxs-lookup"><span data-stu-id="b5c78-135">Element</span></span>|<span data-ttu-id="b5c78-136">描述</span><span class="sxs-lookup"><span data-stu-id="b5c78-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5c78-137">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="b5c78-137">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="b5c78-138">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="b5c78-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5c78-139">備註</span><span class="sxs-lookup"><span data-stu-id="b5c78-139">Remarks</span></span>  
 <span data-ttu-id="b5c78-140">當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="b5c78-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="b5c78-141">當<xref:System.ServiceModel.WSFederationHttpBinding>並不提供的 URL 安全性權杖服務，或是聯合繫結的簽發者位址是 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或`null`，用戶端的 Windows Communication Foundation (WCF) 通道會使用所指定的值`address`和`binding`STS，以取得發行的權杖與通訊。</span><span class="sxs-lookup"><span data-stu-id="b5c78-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="b5c78-142">如需設定本機簽發者的詳細資訊, [請參閱如何:設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="b5c78-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5c78-143">範例</span><span class="sxs-lookup"><span data-stu-id="b5c78-143">Example</span></span>  
 <span data-ttu-id="b5c78-144">下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b5c78-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5c78-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5c78-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="b5c78-146">安全性行為</span><span class="sxs-lookup"><span data-stu-id="b5c78-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b5c78-147">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="b5c78-147">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="b5c78-148">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="b5c78-148">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b5c78-149">安全性行為</span><span class="sxs-lookup"><span data-stu-id="b5c78-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b5c78-150">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b5c78-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b5c78-151">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b5c78-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b5c78-152">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="b5c78-152">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b5c78-153">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="b5c78-153">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="b5c78-154">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b5c78-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
