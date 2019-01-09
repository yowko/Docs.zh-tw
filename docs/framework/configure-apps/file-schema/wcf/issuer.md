---
title: '&lt;簽發者&gt;'
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: d2728bf3613b41ed9f0810207d27d6d67477afd2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149549"
---
# <a name="ltissuergt"></a><span data-ttu-id="09b1e-102">&lt;簽發者&gt;</span><span class="sxs-lookup"><span data-stu-id="09b1e-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="09b1e-103">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="09b1e-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="09b1e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="09b1e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="09b1e-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="09b1e-105">\<bindings></span></span>  
<span data-ttu-id="09b1e-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="09b1e-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="09b1e-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="09b1e-107">\<binding></span></span>  
<span data-ttu-id="09b1e-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="09b1e-108">\<security></span></span>  
<span data-ttu-id="09b1e-109">\<message></span><span class="sxs-lookup"><span data-stu-id="09b1e-109">\<message></span></span>  
<span data-ttu-id="09b1e-110">\<簽發者 ></span><span class="sxs-lookup"><span data-stu-id="09b1e-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b1e-111">語法</span><span class="sxs-lookup"><span data-stu-id="09b1e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09b1e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="09b1e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="09b1e-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="09b1e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09b1e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="09b1e-114">Attributes</span></span>  
  
|<span data-ttu-id="09b1e-115">屬性</span><span class="sxs-lookup"><span data-stu-id="09b1e-115">Attribute</span></span>|<span data-ttu-id="09b1e-116">描述</span><span class="sxs-lookup"><span data-stu-id="09b1e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09b1e-117">address</span><span class="sxs-lookup"><span data-stu-id="09b1e-117">address</span></span>|<span data-ttu-id="09b1e-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="09b1e-118">Required string.</span></span> <span data-ttu-id="09b1e-119">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="09b1e-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09b1e-120">子元素</span><span class="sxs-lookup"><span data-stu-id="09b1e-120">Child Elements</span></span>  
  
|<span data-ttu-id="09b1e-121">項目</span><span class="sxs-lookup"><span data-stu-id="09b1e-121">Element</span></span>|<span data-ttu-id="09b1e-122">描述</span><span class="sxs-lookup"><span data-stu-id="09b1e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09b1e-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="09b1e-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="09b1e-124">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="09b1e-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="09b1e-125">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="09b1e-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="09b1e-126">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="09b1e-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09b1e-127">父項目</span><span class="sxs-lookup"><span data-stu-id="09b1e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="09b1e-128">項目</span><span class="sxs-lookup"><span data-stu-id="09b1e-128">Element</span></span>|<span data-ttu-id="09b1e-129">描述</span><span class="sxs-lookup"><span data-stu-id="09b1e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09b1e-130">\<message></span><span class="sxs-lookup"><span data-stu-id="09b1e-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="09b1e-131">定義訊息層級安全性設定[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="09b1e-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09b1e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09b1e-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="09b1e-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="09b1e-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="09b1e-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="09b1e-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="09b1e-135">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="09b1e-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="09b1e-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="09b1e-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="09b1e-137">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="09b1e-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="09b1e-138">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="09b1e-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
