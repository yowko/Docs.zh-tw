---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 37d935287fa7dfba640c39071295fd660f4db7c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160819"
---
# <a name="issuer"></a><span data-ttu-id="68f04-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="68f04-101">\<issuer></span></span>
<span data-ttu-id="68f04-102">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="68f04-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="68f04-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="68f04-103">\<system.serviceModel></span></span>  
<span data-ttu-id="68f04-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="68f04-104">\<bindings></span></span>  
<span data-ttu-id="68f04-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="68f04-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="68f04-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="68f04-106">\<binding></span></span>  
<span data-ttu-id="68f04-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="68f04-107">\<security></span></span>  
<span data-ttu-id="68f04-108">\<message></span><span class="sxs-lookup"><span data-stu-id="68f04-108">\<message></span></span>  
<span data-ttu-id="68f04-109">\<issuer></span><span class="sxs-lookup"><span data-stu-id="68f04-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f04-110">語法</span><span class="sxs-lookup"><span data-stu-id="68f04-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68f04-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="68f04-111">Attributes and Elements</span></span>  
 <span data-ttu-id="68f04-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="68f04-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68f04-113">屬性</span><span class="sxs-lookup"><span data-stu-id="68f04-113">Attributes</span></span>  
  
|<span data-ttu-id="68f04-114">屬性</span><span class="sxs-lookup"><span data-stu-id="68f04-114">Attribute</span></span>|<span data-ttu-id="68f04-115">描述</span><span class="sxs-lookup"><span data-stu-id="68f04-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68f04-116">位址</span><span class="sxs-lookup"><span data-stu-id="68f04-116">address</span></span>|<span data-ttu-id="68f04-117">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="68f04-117">Required string.</span></span> <span data-ttu-id="68f04-118">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="68f04-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68f04-119">子元素</span><span class="sxs-lookup"><span data-stu-id="68f04-119">Child Elements</span></span>  
  
|<span data-ttu-id="68f04-120">項目</span><span class="sxs-lookup"><span data-stu-id="68f04-120">Element</span></span>|<span data-ttu-id="68f04-121">描述</span><span class="sxs-lookup"><span data-stu-id="68f04-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68f04-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="68f04-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="68f04-123">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="68f04-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="68f04-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="68f04-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="68f04-125">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="68f04-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68f04-126">父項目</span><span class="sxs-lookup"><span data-stu-id="68f04-126">Parent Elements</span></span>  
  
|<span data-ttu-id="68f04-127">項目</span><span class="sxs-lookup"><span data-stu-id="68f04-127">Element</span></span>|<span data-ttu-id="68f04-128">描述</span><span class="sxs-lookup"><span data-stu-id="68f04-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68f04-129">\<message></span><span class="sxs-lookup"><span data-stu-id="68f04-129">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="68f04-130">定義訊息層級安全性設定[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="68f04-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68f04-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68f04-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="68f04-132">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="68f04-132">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="68f04-133">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="68f04-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="68f04-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="68f04-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="68f04-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="68f04-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="68f04-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="68f04-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="68f04-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="68f04-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
