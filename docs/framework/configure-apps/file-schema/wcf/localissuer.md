---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397868"
---
# \<localIssuer>
<span data-ttu-id="a7f22-101">指定要用來取得安全性權杖的本機簽發者位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="a7f22-101">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="a7f22-102">語法</span><span class="sxs-lookup"><span data-stu-id="a7f22-102">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f22-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a7f22-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a7f22-104">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a7f22-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f22-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a7f22-105">Attributes</span></span>  
  
|<span data-ttu-id="a7f22-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a7f22-106">Attribute</span></span>|<span data-ttu-id="a7f22-107">描述</span><span class="sxs-lookup"><span data-stu-id="a7f22-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7f22-108">address</span><span class="sxs-lookup"><span data-stu-id="a7f22-108">address</span></span>|<span data-ttu-id="a7f22-109">必要字串。</span><span class="sxs-lookup"><span data-stu-id="a7f22-109">Required string.</span></span> <span data-ttu-id="a7f22-110">指定本機簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="a7f22-110">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="a7f22-111">繫結</span><span class="sxs-lookup"><span data-stu-id="a7f22-111">binding</span></span>|<span data-ttu-id="a7f22-112">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="a7f22-112">Optional string.</span></span> <span data-ttu-id="a7f22-113">系統提供的繫結之一。</span><span class="sxs-lookup"><span data-stu-id="a7f22-113">One of the system-provided bindings.</span></span> <span data-ttu-id="a7f22-114">如需清單，請參閱[系統提供](../../../wcf/system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="a7f22-114">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="a7f22-115">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7f22-115">bindingConfiguration</span></span>|<span data-ttu-id="a7f22-116">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="a7f22-116">Optional string.</span></span> <span data-ttu-id="a7f22-117">指定組態檔中的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="a7f22-117">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7f22-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a7f22-118">Child Elements</span></span>  
  
|<span data-ttu-id="a7f22-119">元素</span><span class="sxs-lookup"><span data-stu-id="a7f22-119">Element</span></span>|<span data-ttu-id="a7f22-120">描述</span><span class="sxs-lookup"><span data-stu-id="a7f22-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="a7f22-121">指定本機簽發者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="a7f22-121">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="a7f22-122">位址標頭集合，這些位址標頭是正確定址本機簽發者時的必要項目。</span><span class="sxs-lookup"><span data-stu-id="a7f22-122">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="a7f22-123">您可以使用 `add` 關鍵字將標頭加入這個集合。</span><span class="sxs-lookup"><span data-stu-id="a7f22-123">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f22-124">父項目</span><span class="sxs-lookup"><span data-stu-id="a7f22-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f22-125">元素</span><span class="sxs-lookup"><span data-stu-id="a7f22-125">Element</span></span>|<span data-ttu-id="a7f22-126">描述</span><span class="sxs-lookup"><span data-stu-id="a7f22-126">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="a7f22-127">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="a7f22-127">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7f22-128">備註</span><span class="sxs-lookup"><span data-stu-id="a7f22-128">Remarks</span></span>  
 <span data-ttu-id="a7f22-129">當取得某個安全性權杖服務 (STS) 所核發的權杖時，用戶端應用程式必須以特定位址和繫結完成設定，才能與該 STS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a7f22-129">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="a7f22-130">當未 <xref:System.ServiceModel.WSFederationHttpBinding> 提供 Security Token Service 的 URL，或同盟系結的簽發者位址是 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或時 `null` ，用戶端的 Windows Communication Foundation （WCF）通道會使用和所指定的值 `address` `binding` 來與 STS 通訊，以取得發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="a7f22-130">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="a7f22-131">如需設定本機簽發者的詳細資訊，請參閱[如何：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="a7f22-131">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7f22-132">範例</span><span class="sxs-lookup"><span data-stu-id="a7f22-132">Example</span></span>  
 <span data-ttu-id="a7f22-133">下列範例會設定 `address` 項目的 `binding`、`bindingConfiguration` 和 `localIssuer` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a7f22-133">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7f22-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7f22-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="a7f22-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a7f22-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a7f22-136">HOW TO：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="a7f22-136">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a7f22-137">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="a7f22-137">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a7f22-138">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a7f22-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a7f22-139">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a7f22-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a7f22-140">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="a7f22-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a7f22-141">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="a7f22-141">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a7f22-142">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="a7f22-142">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a7f22-143">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a7f22-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
