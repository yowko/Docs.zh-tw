---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: bf512c427637ca65a7271ec8300a373a38632108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913511"
---
# <a name="issuermetadata"></a><span data-ttu-id="a3bcb-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="a3bcb-101">\<issuerMetadata></span></span>
<span data-ttu-id="a3bcb-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a3bcb-102">\<system.serviceModel></span></span>  
<span data-ttu-id="a3bcb-103">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a3bcb-103">\<bindings></span></span>  
<span data-ttu-id="a3bcb-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a3bcb-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="a3bcb-105">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="a3bcb-105">\<binding></span></span>  
<span data-ttu-id="a3bcb-106">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="a3bcb-106">\<security></span></span>  
<span data-ttu-id="a3bcb-107">\<message></span><span class="sxs-lookup"><span data-stu-id="a3bcb-107">\<message></span></span>  
<span data-ttu-id="a3bcb-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="a3bcb-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3bcb-109">語法</span><span class="sxs-lookup"><span data-stu-id="a3bcb-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3bcb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a3bcb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3bcb-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3bcb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a3bcb-112">Attributes</span></span>  
  
|<span data-ttu-id="a3bcb-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a3bcb-113">Attribute</span></span>|<span data-ttu-id="a3bcb-114">說明</span><span class="sxs-lookup"><span data-stu-id="a3bcb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3bcb-115">位址</span><span class="sxs-lookup"><span data-stu-id="a3bcb-115">address</span></span>|<span data-ttu-id="a3bcb-116">必要的 `string` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="a3bcb-117">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="a3bcb-118">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-118">The address must be an absolute URI.</span></span> <span data-ttu-id="a3bcb-119">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3bcb-120">子元素</span><span class="sxs-lookup"><span data-stu-id="a3bcb-120">Child Elements</span></span>  
  
|<span data-ttu-id="a3bcb-121">項目</span><span class="sxs-lookup"><span data-stu-id="a3bcb-121">Element</span></span>|<span data-ttu-id="a3bcb-122">說明</span><span class="sxs-lookup"><span data-stu-id="a3bcb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3bcb-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="a3bcb-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="a3bcb-124">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="a3bcb-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="a3bcb-125">\<identity></span></span>](identity.md)|<span data-ttu-id="a3bcb-126">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3bcb-127">父項目</span><span class="sxs-lookup"><span data-stu-id="a3bcb-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a3bcb-128">項目</span><span class="sxs-lookup"><span data-stu-id="a3bcb-128">Element</span></span>|<span data-ttu-id="a3bcb-129">描述</span><span class="sxs-lookup"><span data-stu-id="a3bcb-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3bcb-130">\<message></span><span class="sxs-lookup"><span data-stu-id="a3bcb-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a3bcb-131">定義[ \<wsFederationHttpBinding >](wsfederationhttpbinding.md)元素的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a3bcb-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3bcb-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3bcb-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="a3bcb-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="a3bcb-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a3bcb-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a3bcb-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a3bcb-135">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="a3bcb-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a3bcb-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a3bcb-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
