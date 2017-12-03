---
title: '&lt;issuerMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d2a4669c86142a66500407edbdda44e9dec81a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="7910e-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="7910e-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="7910e-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7910e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7910e-104">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7910e-104">\<bindings></span></span>  
<span data-ttu-id="7910e-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="7910e-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="7910e-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7910e-106">\<binding></span></span>  
<span data-ttu-id="7910e-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="7910e-107">\<security></span></span>  
<span data-ttu-id="7910e-108">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="7910e-108">\<message></span></span>  
<span data-ttu-id="7910e-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="7910e-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7910e-110">語法</span><span class="sxs-lookup"><span data-stu-id="7910e-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address=String" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuerMetadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7910e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7910e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7910e-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7910e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7910e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7910e-113">Attributes</span></span>  
  
|<span data-ttu-id="7910e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7910e-114">Attribute</span></span>|<span data-ttu-id="7910e-115">描述</span><span class="sxs-lookup"><span data-stu-id="7910e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7910e-116">address</span><span class="sxs-lookup"><span data-stu-id="7910e-116">address</span></span>|<span data-ttu-id="7910e-117">必要的 `string` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7910e-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="7910e-118">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="7910e-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="7910e-119">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="7910e-119">The address must be an absolute URI.</span></span> <span data-ttu-id="7910e-120">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="7910e-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7910e-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7910e-121">Child Elements</span></span>  
  
|<span data-ttu-id="7910e-122">項目</span><span class="sxs-lookup"><span data-stu-id="7910e-122">Element</span></span>|<span data-ttu-id="7910e-123">說明</span><span class="sxs-lookup"><span data-stu-id="7910e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7910e-124">\<標頭 ></span><span class="sxs-lookup"><span data-stu-id="7910e-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="7910e-125">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="7910e-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="7910e-126">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="7910e-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7910e-127">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="7910e-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7910e-128">父項目</span><span class="sxs-lookup"><span data-stu-id="7910e-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7910e-129">項目</span><span class="sxs-lookup"><span data-stu-id="7910e-129">Element</span></span>|<span data-ttu-id="7910e-130">說明</span><span class="sxs-lookup"><span data-stu-id="7910e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7910e-131">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="7910e-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="7910e-132">定義的訊息層級安全性的設定[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="7910e-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7910e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7910e-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="7910e-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7910e-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7910e-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7910e-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7910e-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="7910e-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="7910e-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7910e-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
