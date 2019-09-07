---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397886"
---
# <a name="issuermetadata"></a><span data-ttu-id="d4f6f-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="d4f6f-101">\<issuerMetadata></span></span>

<span data-ttu-id="d4f6f-102">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4f6f-102">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4f6f-103">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d4f6f-103">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d4f6f-104">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d4f6f-104">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d4f6f-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d4f6f-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d4f6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="d4f6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d4f6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d4f6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d4f6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<訊息 >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d4f6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d4f6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="d4f6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f6f-110">語法</span><span class="sxs-lookup"><span data-stu-id="d4f6f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4f6f-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d4f6f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d4f6f-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4f6f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d4f6f-113">Attributes</span></span>  
  
|<span data-ttu-id="d4f6f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d4f6f-114">Attribute</span></span>|<span data-ttu-id="d4f6f-115">描述</span><span class="sxs-lookup"><span data-stu-id="d4f6f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4f6f-116">位址</span><span class="sxs-lookup"><span data-stu-id="d4f6f-116">address</span></span>|<span data-ttu-id="d4f6f-117">必要的 `string` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="d4f6f-118">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="d4f6f-119">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-119">The address must be an absolute URI.</span></span> <span data-ttu-id="d4f6f-120">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4f6f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="d4f6f-121">Child Elements</span></span>  
  
|<span data-ttu-id="d4f6f-122">項目</span><span class="sxs-lookup"><span data-stu-id="d4f6f-122">Element</span></span>|<span data-ttu-id="d4f6f-123">描述</span><span class="sxs-lookup"><span data-stu-id="d4f6f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4f6f-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="d4f6f-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="d4f6f-125">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="d4f6f-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="d4f6f-126">\<identity></span></span>](identity.md)|<span data-ttu-id="d4f6f-127">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4f6f-128">父項目</span><span class="sxs-lookup"><span data-stu-id="d4f6f-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d4f6f-129">項目</span><span class="sxs-lookup"><span data-stu-id="d4f6f-129">Element</span></span>|<span data-ttu-id="d4f6f-130">描述</span><span class="sxs-lookup"><span data-stu-id="d4f6f-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4f6f-131">\<message></span><span class="sxs-lookup"><span data-stu-id="d4f6f-131">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d4f6f-132">定義[ \<wsFederationHttpBinding >](wsfederationhttpbinding.md)元素的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d4f6f-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4f6f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4f6f-133">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="d4f6f-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="d4f6f-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d4f6f-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="d4f6f-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d4f6f-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="d4f6f-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d4f6f-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="d4f6f-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
