---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397909"
---
# \<issuer>
<span data-ttu-id="fa305-101">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="fa305-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="fa305-102">語法</span><span class="sxs-lookup"><span data-stu-id="fa305-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa305-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa305-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fa305-104">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="fa305-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa305-105">屬性</span><span class="sxs-lookup"><span data-stu-id="fa305-105">Attributes</span></span>  
  
|<span data-ttu-id="fa305-106">屬性</span><span class="sxs-lookup"><span data-stu-id="fa305-106">Attribute</span></span>|<span data-ttu-id="fa305-107">描述</span><span class="sxs-lookup"><span data-stu-id="fa305-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa305-108">address</span><span class="sxs-lookup"><span data-stu-id="fa305-108">address</span></span>|<span data-ttu-id="fa305-109">必要字串。</span><span class="sxs-lookup"><span data-stu-id="fa305-109">Required string.</span></span> <span data-ttu-id="fa305-110">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="fa305-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa305-111">子元素</span><span class="sxs-lookup"><span data-stu-id="fa305-111">Child Elements</span></span>  
  
|<span data-ttu-id="fa305-112">元素</span><span class="sxs-lookup"><span data-stu-id="fa305-112">Element</span></span>|<span data-ttu-id="fa305-113">描述</span><span class="sxs-lookup"><span data-stu-id="fa305-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="fa305-114">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="fa305-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="fa305-115">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="fa305-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa305-116">父項目</span><span class="sxs-lookup"><span data-stu-id="fa305-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fa305-117">元素</span><span class="sxs-lookup"><span data-stu-id="fa305-117">Element</span></span>|<span data-ttu-id="fa305-118">描述</span><span class="sxs-lookup"><span data-stu-id="fa305-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="fa305-119">定義元素的訊息層級安全性設定 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="fa305-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa305-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa305-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="fa305-121">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="fa305-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fa305-122">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="fa305-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fa305-123">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="fa305-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fa305-124">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="fa305-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fa305-125">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="fa305-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="fa305-126">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="fa305-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
