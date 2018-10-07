---
title: '&lt;wsFederationHttpBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
author: BrucePerlerMS
ms.openlocfilehash: 2e7ec6b73ec56aa679040e8d3ee50843c9286183
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847772"
---
# <a name="ltsecuritygt-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="58400-102">&lt;wsFederationHttpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="58400-102">&lt;security&gt; of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="58400-103">定義的安全性設定[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="58400-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="58400-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="58400-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="58400-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="58400-105">\<bindings></span></span>  
<span data-ttu-id="58400-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="58400-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="58400-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="58400-107">\<binding></span></span>  
<span data-ttu-id="58400-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="58400-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58400-109">語法</span><span class="sxs-lookup"><span data-stu-id="58400-109">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
    <binding >  
       <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
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
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
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
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58400-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58400-110">Attributes and Elements</span></span>  
 <span data-ttu-id="58400-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="58400-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58400-112">屬性</span><span class="sxs-lookup"><span data-stu-id="58400-112">Attributes</span></span>  
  
|<span data-ttu-id="58400-113">屬性</span><span class="sxs-lookup"><span data-stu-id="58400-113">Attribute</span></span>|<span data-ttu-id="58400-114">描述</span><span class="sxs-lookup"><span data-stu-id="58400-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58400-115">模式</span><span class="sxs-lookup"><span data-stu-id="58400-115">Mode</span></span>|<span data-ttu-id="58400-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="58400-116">Optional.</span></span> <span data-ttu-id="58400-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="58400-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="58400-118">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="58400-118">The default value is `Message`.</span></span> <span data-ttu-id="58400-119">此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="58400-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="58400-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="58400-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="58400-121">值</span><span class="sxs-lookup"><span data-stu-id="58400-121">Value</span></span>|<span data-ttu-id="58400-122">描述</span><span class="sxs-lookup"><span data-stu-id="58400-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="58400-123">無</span><span class="sxs-lookup"><span data-stu-id="58400-123">None</span></span>|<span data-ttu-id="58400-124">傳輸期間的 SOAP 訊息是不安全的。</span><span class="sxs-lookup"><span data-stu-id="58400-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="58400-125">訊息</span><span class="sxs-lookup"><span data-stu-id="58400-125">Message</span></span>|<span data-ttu-id="58400-126">完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="58400-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="58400-127">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="58400-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="58400-128">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="58400-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="58400-129">用戶端驗證是以安全性權杖服務發行至用戶端的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="58400-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="58400-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="58400-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="58400-131">完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。</span><span class="sxs-lookup"><span data-stu-id="58400-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="58400-132">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="58400-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="58400-133">用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="58400-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58400-134">子元素</span><span class="sxs-lookup"><span data-stu-id="58400-134">Child Elements</span></span>  
  
|<span data-ttu-id="58400-135">項目</span><span class="sxs-lookup"><span data-stu-id="58400-135">Element</span></span>|<span data-ttu-id="58400-136">描述</span><span class="sxs-lookup"><span data-stu-id="58400-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58400-137">\<message></span><span class="sxs-lookup"><span data-stu-id="58400-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="58400-138">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="58400-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="58400-139">此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="58400-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58400-140">父項目</span><span class="sxs-lookup"><span data-stu-id="58400-140">Parent Elements</span></span>  
  
|<span data-ttu-id="58400-141">項目</span><span class="sxs-lookup"><span data-stu-id="58400-141">Element</span></span>|<span data-ttu-id="58400-142">描述</span><span class="sxs-lookup"><span data-stu-id="58400-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58400-143">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="58400-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="58400-144">定義的所有繫結功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="58400-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58400-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58400-145">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="58400-146">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="58400-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="58400-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="58400-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="58400-148">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="58400-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="58400-149">繫結</span><span class="sxs-lookup"><span data-stu-id="58400-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="58400-150">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="58400-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="58400-151">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="58400-151">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="58400-152">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="58400-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
