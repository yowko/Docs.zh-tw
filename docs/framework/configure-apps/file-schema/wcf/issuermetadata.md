---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 22e30e0962ec8d2eb0f7e52f4db143fba9bbf703
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491554"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="45f0a-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="45f0a-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="45f0a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="45f0a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="45f0a-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="45f0a-104">\<bindings></span></span>  
<span data-ttu-id="45f0a-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="45f0a-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="45f0a-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="45f0a-106">\<binding></span></span>  
<span data-ttu-id="45f0a-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="45f0a-107">\<security></span></span>  
<span data-ttu-id="45f0a-108">\<message></span><span class="sxs-lookup"><span data-stu-id="45f0a-108">\<message></span></span>  
<span data-ttu-id="45f0a-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="45f0a-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f0a-110">語法</span><span class="sxs-lookup"><span data-stu-id="45f0a-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
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
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45f0a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="45f0a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="45f0a-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="45f0a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45f0a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="45f0a-113">Attributes</span></span>  
  
|<span data-ttu-id="45f0a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="45f0a-114">Attribute</span></span>|<span data-ttu-id="45f0a-115">描述</span><span class="sxs-lookup"><span data-stu-id="45f0a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45f0a-116">address</span><span class="sxs-lookup"><span data-stu-id="45f0a-116">address</span></span>|<span data-ttu-id="45f0a-117">必要的 `string` 屬性。</span><span class="sxs-lookup"><span data-stu-id="45f0a-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="45f0a-118">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="45f0a-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="45f0a-119">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="45f0a-119">The address must be an absolute URI.</span></span> <span data-ttu-id="45f0a-120">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="45f0a-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45f0a-121">子元素</span><span class="sxs-lookup"><span data-stu-id="45f0a-121">Child Elements</span></span>  
  
|<span data-ttu-id="45f0a-122">項目</span><span class="sxs-lookup"><span data-stu-id="45f0a-122">Element</span></span>|<span data-ttu-id="45f0a-123">描述</span><span class="sxs-lookup"><span data-stu-id="45f0a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45f0a-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="45f0a-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="45f0a-125">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="45f0a-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="45f0a-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="45f0a-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="45f0a-127">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="45f0a-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45f0a-128">父項目</span><span class="sxs-lookup"><span data-stu-id="45f0a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="45f0a-129">項目</span><span class="sxs-lookup"><span data-stu-id="45f0a-129">Element</span></span>|<span data-ttu-id="45f0a-130">描述</span><span class="sxs-lookup"><span data-stu-id="45f0a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45f0a-131">\<message></span><span class="sxs-lookup"><span data-stu-id="45f0a-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="45f0a-132">定義訊息層級安全性設定[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="45f0a-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45f0a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45f0a-133">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="45f0a-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="45f0a-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="45f0a-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="45f0a-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="45f0a-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="45f0a-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="45f0a-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="45f0a-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
