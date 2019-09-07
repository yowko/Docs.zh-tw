---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397909"
---
# <a name="issuer"></a><span data-ttu-id="594d9-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="594d9-101">\<issuer></span></span>
<span data-ttu-id="594d9-102">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="594d9-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="594d9-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="594d9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="594d9-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="594d9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="594d9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="594d9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="594d9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="594d9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="594d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="594d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="594d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="594d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="594d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<訊息 >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="594d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="594d9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<簽發者 >**</span><span class="sxs-lookup"><span data-stu-id="594d9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="594d9-111">語法</span><span class="sxs-lookup"><span data-stu-id="594d9-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="594d9-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="594d9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="594d9-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="594d9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="594d9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="594d9-114">Attributes</span></span>  
  
|<span data-ttu-id="594d9-115">屬性</span><span class="sxs-lookup"><span data-stu-id="594d9-115">Attribute</span></span>|<span data-ttu-id="594d9-116">描述</span><span class="sxs-lookup"><span data-stu-id="594d9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="594d9-117">位址</span><span class="sxs-lookup"><span data-stu-id="594d9-117">address</span></span>|<span data-ttu-id="594d9-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="594d9-118">Required string.</span></span> <span data-ttu-id="594d9-119">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="594d9-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="594d9-120">子元素</span><span class="sxs-lookup"><span data-stu-id="594d9-120">Child Elements</span></span>  
  
|<span data-ttu-id="594d9-121">項目</span><span class="sxs-lookup"><span data-stu-id="594d9-121">Element</span></span>|<span data-ttu-id="594d9-122">描述</span><span class="sxs-lookup"><span data-stu-id="594d9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="594d9-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="594d9-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="594d9-124">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="594d9-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="594d9-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="594d9-125">\<identity></span></span>](identity.md)|<span data-ttu-id="594d9-126">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="594d9-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="594d9-127">父項目</span><span class="sxs-lookup"><span data-stu-id="594d9-127">Parent Elements</span></span>  
  
|<span data-ttu-id="594d9-128">項目</span><span class="sxs-lookup"><span data-stu-id="594d9-128">Element</span></span>|<span data-ttu-id="594d9-129">描述</span><span class="sxs-lookup"><span data-stu-id="594d9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="594d9-130">\<message></span><span class="sxs-lookup"><span data-stu-id="594d9-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="594d9-131">定義[ \<wsFederationHttpBinding >](wsfederationhttpbinding.md)元素的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="594d9-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="594d9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="594d9-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="594d9-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="594d9-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="594d9-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="594d9-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="594d9-135">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="594d9-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="594d9-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="594d9-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="594d9-137">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="594d9-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="594d9-138">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="594d9-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
