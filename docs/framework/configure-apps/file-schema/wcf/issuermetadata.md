---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397886"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="7b5f8-101">語法</span><span class="sxs-lookup"><span data-stu-id="7b5f8-101">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b5f8-102">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7b5f8-102">Attributes and Elements</span></span>  
 <span data-ttu-id="7b5f8-103">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b5f8-104">屬性</span><span class="sxs-lookup"><span data-stu-id="7b5f8-104">Attributes</span></span>  
  
|<span data-ttu-id="7b5f8-105">屬性</span><span class="sxs-lookup"><span data-stu-id="7b5f8-105">Attribute</span></span>|<span data-ttu-id="7b5f8-106">描述</span><span class="sxs-lookup"><span data-stu-id="7b5f8-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b5f8-107">address</span><span class="sxs-lookup"><span data-stu-id="7b5f8-107">address</span></span>|<span data-ttu-id="7b5f8-108">必要的 `string` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="7b5f8-109">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="7b5f8-110">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-110">The address must be an absolute URI.</span></span> <span data-ttu-id="7b5f8-111">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b5f8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7b5f8-112">Child Elements</span></span>  
  
|<span data-ttu-id="7b5f8-113">元素</span><span class="sxs-lookup"><span data-stu-id="7b5f8-113">Element</span></span>|<span data-ttu-id="7b5f8-114">描述</span><span class="sxs-lookup"><span data-stu-id="7b5f8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="7b5f8-115">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="7b5f8-116">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b5f8-117">父項目</span><span class="sxs-lookup"><span data-stu-id="7b5f8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7b5f8-118">元素</span><span class="sxs-lookup"><span data-stu-id="7b5f8-118">Element</span></span>|<span data-ttu-id="7b5f8-119">描述</span><span class="sxs-lookup"><span data-stu-id="7b5f8-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="7b5f8-120">定義元素的訊息層級安全性設定 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="7b5f8-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b5f8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b5f8-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="7b5f8-122">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7b5f8-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7b5f8-123">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7b5f8-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7b5f8-124">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="7b5f8-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7b5f8-125">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7b5f8-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
