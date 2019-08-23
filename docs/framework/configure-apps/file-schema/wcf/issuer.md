---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929366"
---
# <a name="issuer"></a><span data-ttu-id="f4950-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="f4950-101">\<issuer></span></span>
<span data-ttu-id="f4950-102">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="f4950-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="f4950-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f4950-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f4950-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f4950-104">\<bindings></span></span>  
<span data-ttu-id="f4950-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f4950-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="f4950-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="f4950-106">\<binding></span></span>  
<span data-ttu-id="f4950-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="f4950-107">\<security></span></span>  
<span data-ttu-id="f4950-108">\<message></span><span class="sxs-lookup"><span data-stu-id="f4950-108">\<message></span></span>  
<span data-ttu-id="f4950-109">\<issuer></span><span class="sxs-lookup"><span data-stu-id="f4950-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4950-110">語法</span><span class="sxs-lookup"><span data-stu-id="f4950-110">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4950-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f4950-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f4950-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f4950-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4950-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f4950-113">Attributes</span></span>  
  
|<span data-ttu-id="f4950-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f4950-114">Attribute</span></span>|<span data-ttu-id="f4950-115">說明</span><span class="sxs-lookup"><span data-stu-id="f4950-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4950-116">位址</span><span class="sxs-lookup"><span data-stu-id="f4950-116">address</span></span>|<span data-ttu-id="f4950-117">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="f4950-117">Required string.</span></span> <span data-ttu-id="f4950-118">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="f4950-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4950-119">子元素</span><span class="sxs-lookup"><span data-stu-id="f4950-119">Child Elements</span></span>  
  
|<span data-ttu-id="f4950-120">項目</span><span class="sxs-lookup"><span data-stu-id="f4950-120">Element</span></span>|<span data-ttu-id="f4950-121">說明</span><span class="sxs-lookup"><span data-stu-id="f4950-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4950-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="f4950-122">\<headers></span></span>](headers-element.md)|<span data-ttu-id="f4950-123">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="f4950-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="f4950-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="f4950-124">\<identity></span></span>](identity.md)|<span data-ttu-id="f4950-125">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="f4950-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4950-126">父項目</span><span class="sxs-lookup"><span data-stu-id="f4950-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f4950-127">項目</span><span class="sxs-lookup"><span data-stu-id="f4950-127">Element</span></span>|<span data-ttu-id="f4950-128">說明</span><span class="sxs-lookup"><span data-stu-id="f4950-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4950-129">\<message></span><span class="sxs-lookup"><span data-stu-id="f4950-129">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="f4950-130">定義[ \<wsFederationHttpBinding >](wsfederationhttpbinding.md)元素的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="f4950-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4950-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4950-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="f4950-132">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="f4950-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f4950-133">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="f4950-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f4950-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="f4950-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f4950-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="f4950-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f4950-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="f4950-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="f4950-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="f4950-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
