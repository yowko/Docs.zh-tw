---
title: <security> 的 <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736324"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="697c9-102">\<wsFederationHttpBinding 的 \<安全性 > ></span><span class="sxs-lookup"><span data-stu-id="697c9-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="697c9-103">定義[\<wsFederationHttpBinding >](wsfederationhttpbinding.md)的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="697c9-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="697c9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="697c9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="697c9-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="697c9-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="697c9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="697c9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="697c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="697c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="697c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="697c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="697c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="697c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="697c9-110">語法</span><span class="sxs-lookup"><span data-stu-id="697c9-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
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
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
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
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="697c9-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="697c9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="697c9-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="697c9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="697c9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="697c9-113">Attributes</span></span>  
  
|<span data-ttu-id="697c9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="697c9-114">Attribute</span></span>|<span data-ttu-id="697c9-115">描述</span><span class="sxs-lookup"><span data-stu-id="697c9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="697c9-116">模式</span><span class="sxs-lookup"><span data-stu-id="697c9-116">Mode</span></span>|<span data-ttu-id="697c9-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="697c9-117">Optional.</span></span> <span data-ttu-id="697c9-118">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="697c9-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="697c9-119">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="697c9-119">The default value is `Message`.</span></span> <span data-ttu-id="697c9-120">此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="697c9-120">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="697c9-121">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="697c9-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="697c9-122">值</span><span class="sxs-lookup"><span data-stu-id="697c9-122">Value</span></span>|<span data-ttu-id="697c9-123">描述</span><span class="sxs-lookup"><span data-stu-id="697c9-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="697c9-124">None</span><span class="sxs-lookup"><span data-stu-id="697c9-124">None</span></span>|<span data-ttu-id="697c9-125">傳輸期間的 SOAP 訊息是不安全的。</span><span class="sxs-lookup"><span data-stu-id="697c9-125">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="697c9-126">訊息</span><span class="sxs-lookup"><span data-stu-id="697c9-126">Message</span></span>|<span data-ttu-id="697c9-127">完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="697c9-127">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="697c9-128">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="697c9-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="697c9-129">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="697c9-129">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="697c9-130">用戶端驗證是以安全性權杖服務發行至用戶端的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="697c9-130">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="697c9-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="697c9-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="697c9-132">完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。</span><span class="sxs-lookup"><span data-stu-id="697c9-132">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="697c9-133">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="697c9-133">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="697c9-134">用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="697c9-134">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="697c9-135">子項目</span><span class="sxs-lookup"><span data-stu-id="697c9-135">Child Elements</span></span>  
  
|<span data-ttu-id="697c9-136">項目</span><span class="sxs-lookup"><span data-stu-id="697c9-136">Element</span></span>|<span data-ttu-id="697c9-137">描述</span><span class="sxs-lookup"><span data-stu-id="697c9-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="697c9-138">\<message ></span><span class="sxs-lookup"><span data-stu-id="697c9-138">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="697c9-139">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="697c9-139">Defines the settings for the message-level security.</span></span> <span data-ttu-id="697c9-140">此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="697c9-140">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="697c9-141">父項目</span><span class="sxs-lookup"><span data-stu-id="697c9-141">Parent Elements</span></span>  
  
|<span data-ttu-id="697c9-142">項目</span><span class="sxs-lookup"><span data-stu-id="697c9-142">Element</span></span>|<span data-ttu-id="697c9-143">描述</span><span class="sxs-lookup"><span data-stu-id="697c9-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="697c9-144">\<binding ></span><span class="sxs-lookup"><span data-stu-id="697c9-144">\<binding></span></span>](bindings.md)|<span data-ttu-id="697c9-145">定義[\<wsDualHttpBinding >](wsdualhttpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="697c9-145">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="697c9-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="697c9-146">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="697c9-147">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="697c9-147">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="697c9-148">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="697c9-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="697c9-149">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="697c9-149">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="697c9-150">繫結</span><span class="sxs-lookup"><span data-stu-id="697c9-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="697c9-151">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="697c9-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="697c9-152">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="697c9-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="697c9-153">\<binding ></span><span class="sxs-lookup"><span data-stu-id="697c9-153">\<binding></span></span>](bindings.md)
