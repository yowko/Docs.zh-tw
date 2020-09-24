---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 9e92bbcacf529a97e1ae936e93e38c98eab19cab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157261"
---
# \<issuer>

<span data-ttu-id="d5ee4-101">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="d5ee4-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5ee4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5ee4-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d5ee4-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d5ee4-104">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="d5ee4-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5ee4-105">屬性</span><span class="sxs-lookup"><span data-stu-id="d5ee4-105">Attributes</span></span>  
  
|<span data-ttu-id="d5ee4-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d5ee4-106">Attribute</span></span>|<span data-ttu-id="d5ee4-107">描述</span><span class="sxs-lookup"><span data-stu-id="d5ee4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5ee4-108">address</span><span class="sxs-lookup"><span data-stu-id="d5ee4-108">address</span></span>|<span data-ttu-id="d5ee4-109">必要字串。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-109">Required string.</span></span> <span data-ttu-id="d5ee4-110">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5ee4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d5ee4-111">Child Elements</span></span>  
  
|<span data-ttu-id="d5ee4-112">項目</span><span class="sxs-lookup"><span data-stu-id="d5ee4-112">Element</span></span>|<span data-ttu-id="d5ee4-113">描述</span><span class="sxs-lookup"><span data-stu-id="d5ee4-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="d5ee4-114">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="d5ee4-115">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5ee4-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d5ee4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d5ee4-117">項目</span><span class="sxs-lookup"><span data-stu-id="d5ee4-117">Element</span></span>|<span data-ttu-id="d5ee4-118">描述</span><span class="sxs-lookup"><span data-stu-id="d5ee4-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d5ee4-119">定義專案的訊息層級安全性設定 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5ee4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5ee4-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="d5ee4-121">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="d5ee4-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d5ee4-122">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="d5ee4-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d5ee4-123">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="d5ee4-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d5ee4-124">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="d5ee4-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d5ee4-125">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="d5ee4-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d5ee4-126">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="d5ee4-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
