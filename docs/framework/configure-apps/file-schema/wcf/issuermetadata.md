---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 0dffad6a17720dd0506acbcd60efe4aafe24ed28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090104"
---
# <a name="issuermetadata"></a><span data-ttu-id="adb75-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="adb75-101">\<issuerMetadata></span></span>
<span data-ttu-id="adb75-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="adb75-102">\<system.serviceModel></span></span>  
<span data-ttu-id="adb75-103">\<bindings></span><span class="sxs-lookup"><span data-stu-id="adb75-103">\<bindings></span></span>  
<span data-ttu-id="adb75-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="adb75-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="adb75-105">\<binding></span><span class="sxs-lookup"><span data-stu-id="adb75-105">\<binding></span></span>  
<span data-ttu-id="adb75-106">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="adb75-106">\<security></span></span>  
<span data-ttu-id="adb75-107">\<message></span><span class="sxs-lookup"><span data-stu-id="adb75-107">\<message></span></span>  
<span data-ttu-id="adb75-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="adb75-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb75-109">語法</span><span class="sxs-lookup"><span data-stu-id="adb75-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adb75-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="adb75-110">Attributes and Elements</span></span>  
 <span data-ttu-id="adb75-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="adb75-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adb75-112">屬性</span><span class="sxs-lookup"><span data-stu-id="adb75-112">Attributes</span></span>  
  
|<span data-ttu-id="adb75-113">屬性</span><span class="sxs-lookup"><span data-stu-id="adb75-113">Attribute</span></span>|<span data-ttu-id="adb75-114">描述</span><span class="sxs-lookup"><span data-stu-id="adb75-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adb75-115">位址</span><span class="sxs-lookup"><span data-stu-id="adb75-115">address</span></span>|<span data-ttu-id="adb75-116">必要的 `string` 屬性。</span><span class="sxs-lookup"><span data-stu-id="adb75-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="adb75-117">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="adb75-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="adb75-118">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="adb75-118">The address must be an absolute URI.</span></span> <span data-ttu-id="adb75-119">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="adb75-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adb75-120">子元素</span><span class="sxs-lookup"><span data-stu-id="adb75-120">Child Elements</span></span>  
  
|<span data-ttu-id="adb75-121">項目</span><span class="sxs-lookup"><span data-stu-id="adb75-121">Element</span></span>|<span data-ttu-id="adb75-122">描述</span><span class="sxs-lookup"><span data-stu-id="adb75-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adb75-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="adb75-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="adb75-124">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="adb75-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="adb75-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="adb75-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="adb75-126">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="adb75-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adb75-127">父項目</span><span class="sxs-lookup"><span data-stu-id="adb75-127">Parent Elements</span></span>  
  
|<span data-ttu-id="adb75-128">項目</span><span class="sxs-lookup"><span data-stu-id="adb75-128">Element</span></span>|<span data-ttu-id="adb75-129">描述</span><span class="sxs-lookup"><span data-stu-id="adb75-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adb75-130">\<message></span><span class="sxs-lookup"><span data-stu-id="adb75-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="adb75-131">定義訊息層級安全性設定[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="adb75-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adb75-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adb75-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="adb75-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="adb75-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="adb75-134">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="adb75-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="adb75-135">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="adb75-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="adb75-136">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="adb75-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
