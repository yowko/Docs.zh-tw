---
title: <message> 元素 (屬於 <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: f05bd90bd2e4c7e1fd606518d9e5cb8d4e5ad974
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092990"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="ae112-102">\<訊息 > 項目\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ae112-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="ae112-103">定義訊息層級安全性設定[ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="ae112-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="ae112-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ae112-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ae112-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ae112-105">\<bindings></span></span>  
<span data-ttu-id="ae112-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ae112-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="ae112-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="ae112-107">\<binding></span></span>  
<span data-ttu-id="ae112-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="ae112-108">\<security></span></span>  
<span data-ttu-id="ae112-109">\<message></span><span class="sxs-lookup"><span data-stu-id="ae112-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae112-110">語法</span><span class="sxs-lookup"><span data-stu-id="ae112-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
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
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae112-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ae112-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ae112-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ae112-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae112-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ae112-113">Attributes</span></span>  
  
|<span data-ttu-id="ae112-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ae112-114">Attribute</span></span>|<span data-ttu-id="ae112-115">描述</span><span class="sxs-lookup"><span data-stu-id="ae112-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="ae112-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="ae112-116">Optional.</span></span> <span data-ttu-id="ae112-117">設定訊息加密、簽章和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="ae112-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="ae112-118">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="ae112-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="ae112-119">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="ae112-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="ae112-120">請參閱下表列出的可能值。</span><span class="sxs-lookup"><span data-stu-id="ae112-120">See the following table for possible values.</span></span> <span data-ttu-id="ae112-121">預設值為 Basic256。</span><span class="sxs-lookup"><span data-stu-id="ae112-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="ae112-122">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="ae112-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="ae112-123">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ae112-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ae112-124">-   SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="ae112-124">-   SymmetricKey</span></span><br /><span data-ttu-id="ae112-125">-   PublicKey</span><span class="sxs-lookup"><span data-stu-id="ae112-125">-   PublicKey</span></span><br /><span data-ttu-id="ae112-126">-   BearerKey</span><span class="sxs-lookup"><span data-stu-id="ae112-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="ae112-127">預設為 SymmetricKey。</span><span class="sxs-lookup"><span data-stu-id="ae112-127">The default is SymmetricKey.</span></span> <span data-ttu-id="ae112-128">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="ae112-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="ae112-129">URI，指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="ae112-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="ae112-130">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="ae112-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="ae112-131">這個值會指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="ae112-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="ae112-132">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="ae112-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="ae112-133">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="ae112-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="ae112-134">值</span><span class="sxs-lookup"><span data-stu-id="ae112-134">Value</span></span>|<span data-ttu-id="ae112-135">描述</span><span class="sxs-lookup"><span data-stu-id="ae112-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae112-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="ae112-136">Basic128</span></span>|<span data-ttu-id="ae112-137">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="ae112-138">Basic192</span></span>|<span data-ttu-id="ae112-139">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="ae112-140">Basic256</span></span>|<span data-ttu-id="ae112-141">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-142">Basic256Rsa15</span></span>|<span data-ttu-id="ae112-143">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ae112-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-144">Basic192Rsa15</span></span>|<span data-ttu-id="ae112-145">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ae112-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="ae112-146">TripleDes</span></span>|<span data-ttu-id="ae112-147">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-148">Basic128Rsa15</span></span>|<span data-ttu-id="ae112-149">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ae112-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-150">TripleDesRsa15</span></span>|<span data-ttu-id="ae112-151">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ae112-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="ae112-152">Basic128Sha256</span></span>|<span data-ttu-id="ae112-153">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="ae112-154">Basic192Sha256</span></span>|<span data-ttu-id="ae112-155">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="ae112-156">Basic256Sha256</span></span>|<span data-ttu-id="ae112-157">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="ae112-158">TripleDesSha256</span></span>|<span data-ttu-id="ae112-159">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ae112-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="ae112-161">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ae112-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="ae112-163">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ae112-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="ae112-165">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ae112-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ae112-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="ae112-167">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="ae112-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae112-168">子元素</span><span class="sxs-lookup"><span data-stu-id="ae112-168">Child Elements</span></span>  
  
|<span data-ttu-id="ae112-169">項目</span><span class="sxs-lookup"><span data-stu-id="ae112-169">Element</span></span>|<span data-ttu-id="ae112-170">描述</span><span class="sxs-lookup"><span data-stu-id="ae112-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae112-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="ae112-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="ae112-172">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="ae112-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="ae112-173">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="ae112-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="ae112-174">\<issuer></span><span class="sxs-lookup"><span data-stu-id="ae112-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="ae112-175">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="ae112-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="ae112-176">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="ae112-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="ae112-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="ae112-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="ae112-178">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="ae112-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="ae112-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="ae112-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="ae112-180">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="ae112-180">A collection of token request parameters.</span></span> <span data-ttu-id="ae112-181">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="ae112-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae112-182">父項目</span><span class="sxs-lookup"><span data-stu-id="ae112-182">Parent Elements</span></span>  
  
|<span data-ttu-id="ae112-183">項目</span><span class="sxs-lookup"><span data-stu-id="ae112-183">Element</span></span>|<span data-ttu-id="ae112-184">描述</span><span class="sxs-lookup"><span data-stu-id="ae112-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae112-185">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="ae112-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="ae112-186">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ae112-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae112-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae112-187">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="ae112-188">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ae112-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ae112-189">繫結</span><span class="sxs-lookup"><span data-stu-id="ae112-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ae112-190">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="ae112-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ae112-191">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="ae112-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ae112-192">\<binding></span><span class="sxs-lookup"><span data-stu-id="ae112-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
