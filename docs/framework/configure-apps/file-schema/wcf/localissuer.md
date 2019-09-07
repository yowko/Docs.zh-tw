---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397868"
---
# <a name="localissuer"></a><span data-ttu-id="576cf-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="576cf-101">\<localIssuer></span></span>
<span data-ttu-id="576cf-102">指定要用來取得安全性權杖的本機簽發者位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="576cf-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
<span data-ttu-id="576cf-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="576cf-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="576cf-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="576cf-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="576cf-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="576cf-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="576cf-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="576cf-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="576cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="576cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="576cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="576cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="576cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="576cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="576cf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<localIssuer >**</span><span class="sxs-lookup"><span data-stu-id="576cf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="576cf-111">語法</span><span class="sxs-lookup"><span data-stu-id="576cf-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="576cf-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="576cf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="576cf-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="576cf-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="576cf-114">屬性</span><span class="sxs-lookup"><span data-stu-id="576cf-114">Attributes</span></span>  
  
|<span data-ttu-id="576cf-115">屬性</span><span class="sxs-lookup"><span data-stu-id="576cf-115">Attribute</span></span>|<span data-ttu-id="576cf-116">說明</span><span class="sxs-lookup"><span data-stu-id="576cf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="576cf-117">位址</span><span class="sxs-lookup"><span data-stu-id="576cf-117">address</span></span>|<span data-ttu-id="576cf-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="576cf-118">Required string.</span></span> <span data-ttu-id="576cf-119">指定本機簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="576cf-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="576cf-120">繫結</span><span class="sxs-lookup"><span data-stu-id="576cf-120">binding</span></span>|<span data-ttu-id="576cf-121">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="576cf-121">Optional string.</span></span> <span data-ttu-id="576cf-122">系統提供的繫結之一。</span><span class="sxs-lookup"><span data-stu-id="576cf-122">One of the system-provided bindings.</span></span> <span data-ttu-id="576cf-123">如需清單，請參閱[系統提供](../../../wcf/system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="576cf-123">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="576cf-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="576cf-124">bindingConfiguration</span></span>|<span data-ttu-id="576cf-125">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="576cf-125">Optional string.</span></span> <span data-ttu-id="576cf-126">指定組態檔中的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="576cf-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="576cf-127">子元素</span><span class="sxs-lookup"><span data-stu-id="576cf-127">Child Elements</span></span>  
  
|<span data-ttu-id="576cf-128">項目</span><span class="sxs-lookup"><span data-stu-id="576cf-128">Element</span></span>|<span data-ttu-id="576cf-129">說明</span><span class="sxs-lookup"><span data-stu-id="576cf-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="576cf-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="576cf-130">\<identity></span></span>](identity.md)|<span data-ttu-id="576cf-131">指定本機簽發者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="576cf-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="576cf-132">\<headers></span><span class="sxs-lookup"><span data-stu-id="576cf-132">\<headers></span></span>](headers-element.md)|<span data-ttu-id="576cf-133">位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。</span><span class="sxs-lookup"><span data-stu-id="576cf-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="576cf-134">您可以使用 `add` 關鍵字將標頭加入這個集合。</span><span class="sxs-lookup"><span data-stu-id="576cf-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="576cf-135">父項目</span><span class="sxs-lookup"><span data-stu-id="576cf-135">Parent Elements</span></span>  
  
|<span data-ttu-id="576cf-136">項目</span><span class="sxs-lookup"><span data-stu-id="576cf-136">Element</span></span>|<span data-ttu-id="576cf-137">描述</span><span class="sxs-lookup"><span data-stu-id="576cf-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="576cf-138">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="576cf-138">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="576cf-139">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="576cf-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="576cf-140">備註</span><span class="sxs-lookup"><span data-stu-id="576cf-140">Remarks</span></span>  
 <span data-ttu-id="576cf-141">當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="576cf-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="576cf-142">當<xref:System.ServiceModel.WSFederationHttpBinding>並不提供的 URL 安全性權杖服務，或是聯合繫結的簽發者位址是 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或`null`，用戶端的 Windows Communication Foundation (WCF) 通道會使用所指定的值`address`和`binding`STS，以取得發行的權杖與通訊。</span><span class="sxs-lookup"><span data-stu-id="576cf-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="576cf-143">如需設定本機簽發者的詳細資訊， [請參閱如何：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="576cf-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="576cf-144">範例</span><span class="sxs-lookup"><span data-stu-id="576cf-144">Example</span></span>  
 <span data-ttu-id="576cf-145">下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。</span><span class="sxs-lookup"><span data-stu-id="576cf-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="576cf-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="576cf-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="576cf-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="576cf-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="576cf-148">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="576cf-148">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="576cf-149">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="576cf-149">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="576cf-150">安全性行為</span><span class="sxs-lookup"><span data-stu-id="576cf-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="576cf-151">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="576cf-151">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="576cf-152">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="576cf-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="576cf-153">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="576cf-153">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="576cf-154">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="576cf-154">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="576cf-155">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="576cf-155">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
