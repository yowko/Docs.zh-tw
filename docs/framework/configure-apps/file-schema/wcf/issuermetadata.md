---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 10a6d2aaad7d63d00b3a57032d0d218f756454d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175950"
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
  
## <a name="syntax"></a><span data-ttu-id="bc681-101">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc681-101">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc681-102">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc681-102">Attributes and Elements</span></span>  

 <span data-ttu-id="bc681-103">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bc681-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc681-104">屬性</span><span class="sxs-lookup"><span data-stu-id="bc681-104">Attributes</span></span>  
  
|<span data-ttu-id="bc681-105">屬性</span><span class="sxs-lookup"><span data-stu-id="bc681-105">Attribute</span></span>|<span data-ttu-id="bc681-106">描述</span><span class="sxs-lookup"><span data-stu-id="bc681-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc681-107">address</span><span class="sxs-lookup"><span data-stu-id="bc681-107">address</span></span>|<span data-ttu-id="bc681-108">必要的 `string` 屬性。</span><span class="sxs-lookup"><span data-stu-id="bc681-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="bc681-109">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="bc681-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="bc681-110">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="bc681-110">The address must be an absolute URI.</span></span> <span data-ttu-id="bc681-111">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="bc681-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc681-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bc681-112">Child Elements</span></span>  
  
|<span data-ttu-id="bc681-113">項目</span><span class="sxs-lookup"><span data-stu-id="bc681-113">Element</span></span>|<span data-ttu-id="bc681-114">描述</span><span class="sxs-lookup"><span data-stu-id="bc681-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="bc681-115">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="bc681-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="bc681-116">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="bc681-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc681-117">父項目</span><span class="sxs-lookup"><span data-stu-id="bc681-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bc681-118">項目</span><span class="sxs-lookup"><span data-stu-id="bc681-118">Element</span></span>|<span data-ttu-id="bc681-119">描述</span><span class="sxs-lookup"><span data-stu-id="bc681-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="bc681-120">定義專案的訊息層級安全性設定 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="bc681-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc681-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc681-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="bc681-122">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="bc681-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="bc681-123">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="bc681-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="bc681-124">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="bc681-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="bc681-125">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="bc681-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
