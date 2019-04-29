---
title: <message> 的 <wsFederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 79739dd715d7982555e5577c921cb65156af5923
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769872"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="75217-102">\<訊息 > 項目\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="75217-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="75217-103">定義訊息層級安全性設定[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="75217-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="75217-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="75217-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="75217-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="75217-105">\<bindings></span></span>  
<span data-ttu-id="75217-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="75217-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="75217-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="75217-107">\<binding></span></span>  
<span data-ttu-id="75217-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="75217-108">\<security></span></span>  
<span data-ttu-id="75217-109">\<message></span><span class="sxs-lookup"><span data-stu-id="75217-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75217-110">語法</span><span class="sxs-lookup"><span data-stu-id="75217-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75217-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="75217-111">Attributes and Elements</span></span>  
 <span data-ttu-id="75217-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="75217-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75217-113">屬性</span><span class="sxs-lookup"><span data-stu-id="75217-113">Attributes</span></span>  
  
|<span data-ttu-id="75217-114">屬性</span><span class="sxs-lookup"><span data-stu-id="75217-114">Attribute</span></span>|<span data-ttu-id="75217-115">描述</span><span class="sxs-lookup"><span data-stu-id="75217-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75217-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="75217-116">algorithmSuite</span></span>|<span data-ttu-id="75217-117">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="75217-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="75217-118">請參閱「algorithmSuite 屬性」表格中此屬性的有效值。</span><span class="sxs-lookup"><span data-stu-id="75217-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="75217-119">預設值為 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="75217-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="75217-120">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="75217-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="75217-121">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="75217-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="75217-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="75217-122">issuedKeyType</span></span>|<span data-ttu-id="75217-123">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="75217-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="75217-124">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="75217-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="75217-125">-   SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="75217-125">-   SymmetricKey</span></span><br /><span data-ttu-id="75217-126">-   PublicKey</span><span class="sxs-lookup"><span data-stu-id="75217-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="75217-127">預設為 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="75217-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="75217-128">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="75217-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="75217-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="75217-129">issuedTokenType</span></span>|<span data-ttu-id="75217-130">字串，其中包含的 URI 指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="75217-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="75217-131">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="75217-131">The default is `null`.</span></span>|  
|<span data-ttu-id="75217-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="75217-132">negotiateServiceCredential</span></span>|<span data-ttu-id="75217-133">布林值，指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="75217-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="75217-134">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="75217-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="75217-135">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="75217-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="75217-136">值</span><span class="sxs-lookup"><span data-stu-id="75217-136">Value</span></span>|<span data-ttu-id="75217-137">描述</span><span class="sxs-lookup"><span data-stu-id="75217-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="75217-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="75217-138">Basic128</span></span>|<span data-ttu-id="75217-139">使用 Basic128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="75217-140">Basic192</span></span>|<span data-ttu-id="75217-141">使用 Basic192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="75217-142">Basic256</span></span>|<span data-ttu-id="75217-143">使用 Basic256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="75217-144">Basic256Rsa15</span></span>|<span data-ttu-id="75217-145">將 Basic256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="75217-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="75217-146">Basic192Rsa15</span></span>|<span data-ttu-id="75217-147">將 Basic192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="75217-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="75217-148">TripleDes</span></span>|<span data-ttu-id="75217-149">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="75217-150">Basic128Rsa15</span></span>|<span data-ttu-id="75217-151">將 Basic128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="75217-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="75217-152">TripleDesRsa15</span></span>|<span data-ttu-id="75217-153">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="75217-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="75217-154">Basic128Sha256</span></span>|<span data-ttu-id="75217-155">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="75217-156">Basic192Sha256</span></span>|<span data-ttu-id="75217-157">將 Basic192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="75217-158">Basic256Sha256</span></span>|<span data-ttu-id="75217-159">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="75217-160">TripleDesSha256</span></span>|<span data-ttu-id="75217-161">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="75217-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="75217-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="75217-163">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="75217-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="75217-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="75217-165">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="75217-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="75217-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="75217-167">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="75217-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="75217-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="75217-169">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="75217-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75217-170">子元素</span><span class="sxs-lookup"><span data-stu-id="75217-170">Child Elements</span></span>  
  
|<span data-ttu-id="75217-171">項目</span><span class="sxs-lookup"><span data-stu-id="75217-171">Element</span></span>|<span data-ttu-id="75217-172">描述</span><span class="sxs-lookup"><span data-stu-id="75217-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75217-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="75217-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="75217-174">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="75217-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="75217-175">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="75217-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="75217-176">issuer</span><span class="sxs-lookup"><span data-stu-id="75217-176">issuer</span></span>|<span data-ttu-id="75217-177">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="75217-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="75217-178">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="75217-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="75217-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="75217-179">issuerMetadata</span></span>|<span data-ttu-id="75217-180">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="75217-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="75217-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="75217-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="75217-182">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="75217-182">A collection of token request parameters.</span></span> <span data-ttu-id="75217-183">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="75217-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75217-184">父項目</span><span class="sxs-lookup"><span data-stu-id="75217-184">Parent Elements</span></span>  
  
|<span data-ttu-id="75217-185">項目</span><span class="sxs-lookup"><span data-stu-id="75217-185">Element</span></span>|<span data-ttu-id="75217-186">描述</span><span class="sxs-lookup"><span data-stu-id="75217-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75217-187">\<security></span><span class="sxs-lookup"><span data-stu-id="75217-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="75217-188">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="75217-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75217-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75217-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="75217-190">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="75217-190">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="75217-191">繫結</span><span class="sxs-lookup"><span data-stu-id="75217-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="75217-192">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="75217-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="75217-193">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="75217-193">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="75217-194">\<binding></span><span class="sxs-lookup"><span data-stu-id="75217-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
