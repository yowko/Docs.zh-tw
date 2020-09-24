---
title: <security> 的 <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 650483099c7d70450cfc56a9a28efac076d64675
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162228"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="67a88-102">\<security> 的 \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="67a88-102">\<security> of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="67a88-103">定義的安全性設定 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="67a88-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="67a88-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="67a88-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67a88-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67a88-105">Attributes and Elements</span></span>  

 <span data-ttu-id="67a88-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67a88-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67a88-107">屬性</span><span class="sxs-lookup"><span data-stu-id="67a88-107">Attributes</span></span>  
  
|<span data-ttu-id="67a88-108">屬性</span><span class="sxs-lookup"><span data-stu-id="67a88-108">Attribute</span></span>|<span data-ttu-id="67a88-109">描述</span><span class="sxs-lookup"><span data-stu-id="67a88-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67a88-110">[模式]</span><span class="sxs-lookup"><span data-stu-id="67a88-110">Mode</span></span>|<span data-ttu-id="67a88-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="67a88-111">Optional.</span></span> <span data-ttu-id="67a88-112">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="67a88-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="67a88-113">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="67a88-113">The default value is `Message`.</span></span> <span data-ttu-id="67a88-114">此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="67a88-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="67a88-115">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="67a88-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="67a88-116">值</span><span class="sxs-lookup"><span data-stu-id="67a88-116">Value</span></span>|<span data-ttu-id="67a88-117">描述</span><span class="sxs-lookup"><span data-stu-id="67a88-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67a88-118">無</span><span class="sxs-lookup"><span data-stu-id="67a88-118">None</span></span>|<span data-ttu-id="67a88-119">傳輸期間的 SOAP 訊息是不安全的。</span><span class="sxs-lookup"><span data-stu-id="67a88-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="67a88-120">訊息</span><span class="sxs-lookup"><span data-stu-id="67a88-120">Message</span></span>|<span data-ttu-id="67a88-121">完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="67a88-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="67a88-122">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="67a88-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="67a88-123">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="67a88-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="67a88-124">用戶端驗證是以安全性權杖服務發行至用戶端的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="67a88-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="67a88-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="67a88-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="67a88-126">完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。</span><span class="sxs-lookup"><span data-stu-id="67a88-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="67a88-127">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="67a88-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="67a88-128">用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="67a88-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67a88-129">子元素</span><span class="sxs-lookup"><span data-stu-id="67a88-129">Child Elements</span></span>  
  
|<span data-ttu-id="67a88-130">項目</span><span class="sxs-lookup"><span data-stu-id="67a88-130">Element</span></span>|<span data-ttu-id="67a88-131">描述</span><span class="sxs-lookup"><span data-stu-id="67a88-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="67a88-132">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="67a88-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="67a88-133">此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="67a88-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67a88-134">父項目</span><span class="sxs-lookup"><span data-stu-id="67a88-134">Parent Elements</span></span>  
  
|<span data-ttu-id="67a88-135">項目</span><span class="sxs-lookup"><span data-stu-id="67a88-135">Element</span></span>|<span data-ttu-id="67a88-136">描述</span><span class="sxs-lookup"><span data-stu-id="67a88-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="67a88-137">定義的所有系結功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="67a88-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67a88-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67a88-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="67a88-139">作法：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="67a88-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="67a88-140">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="67a88-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="67a88-141">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="67a88-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="67a88-142">繫結</span><span class="sxs-lookup"><span data-stu-id="67a88-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="67a88-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="67a88-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="67a88-144">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="67a88-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
