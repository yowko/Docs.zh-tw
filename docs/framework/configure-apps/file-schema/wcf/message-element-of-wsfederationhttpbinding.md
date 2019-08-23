---
title: <message> 的 <wsFederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 4730d7e573eefdfcd5704621d0a7ccaa15f76d3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931583"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="d0ed2-102">\<wsFederationHttpBinding > 的\<message > 元素</span><span class="sxs-lookup"><span data-stu-id="d0ed2-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="d0ed2-103">定義[ \<wsFederationHttpBinding >](wsfederationhttpbinding.md)的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="d0ed2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0ed2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0ed2-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d0ed2-105">\<bindings></span></span>  
<span data-ttu-id="d0ed2-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="d0ed2-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d0ed2-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="d0ed2-107">\<binding></span></span>  
<span data-ttu-id="d0ed2-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="d0ed2-108">\<security></span></span>  
<span data-ttu-id="d0ed2-109">\<message></span><span class="sxs-lookup"><span data-stu-id="d0ed2-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ed2-110">語法</span><span class="sxs-lookup"><span data-stu-id="d0ed2-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0ed2-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d0ed2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d0ed2-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0ed2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d0ed2-113">Attributes</span></span>  
  
|<span data-ttu-id="d0ed2-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d0ed2-114">Attribute</span></span>|<span data-ttu-id="d0ed2-115">描述</span><span class="sxs-lookup"><span data-stu-id="d0ed2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0ed2-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d0ed2-116">algorithmSuite</span></span>|<span data-ttu-id="d0ed2-117">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="d0ed2-118">請參閱「algorithmSuite 屬性」表格中此屬性的有效值。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="d0ed2-119">預設值為 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="d0ed2-120">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="d0ed2-121">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="d0ed2-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="d0ed2-122">issuedKeyType</span></span>|<span data-ttu-id="d0ed2-123">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="d0ed2-124">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="d0ed2-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d0ed2-125">-   SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="d0ed2-125">-   SymmetricKey</span></span><br /><span data-ttu-id="d0ed2-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="d0ed2-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="d0ed2-127">預設為 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="d0ed2-128">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="d0ed2-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="d0ed2-129">issuedTokenType</span></span>|<span data-ttu-id="d0ed2-130">字串，其中包含的 URI 指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="d0ed2-131">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-131">The default is `null`.</span></span>|  
|<span data-ttu-id="d0ed2-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="d0ed2-132">negotiateServiceCredential</span></span>|<span data-ttu-id="d0ed2-133">布林值，指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="d0ed2-134">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="d0ed2-135">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="d0ed2-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="d0ed2-136">值</span><span class="sxs-lookup"><span data-stu-id="d0ed2-136">Value</span></span>|<span data-ttu-id="d0ed2-137">描述</span><span class="sxs-lookup"><span data-stu-id="d0ed2-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d0ed2-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="d0ed2-138">Basic128</span></span>|<span data-ttu-id="d0ed2-139">使用 Basic128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="d0ed2-140">Basic192</span></span>|<span data-ttu-id="d0ed2-141">使用 Basic192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="d0ed2-142">Basic256</span></span>|<span data-ttu-id="d0ed2-143">使用 Basic256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-144">Basic256Rsa15</span></span>|<span data-ttu-id="d0ed2-145">將 Basic256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-146">Basic192Rsa15</span></span>|<span data-ttu-id="d0ed2-147">將 Basic192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="d0ed2-148">TripleDes</span></span>|<span data-ttu-id="d0ed2-149">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-150">Basic128Rsa15</span></span>|<span data-ttu-id="d0ed2-151">將 Basic128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-152">TripleDesRsa15</span></span>|<span data-ttu-id="d0ed2-153">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="d0ed2-154">Basic128Sha256</span></span>|<span data-ttu-id="d0ed2-155">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="d0ed2-156">Basic192Sha256</span></span>|<span data-ttu-id="d0ed2-157">將 Basic192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="d0ed2-158">Basic256Sha256</span></span>|<span data-ttu-id="d0ed2-159">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="d0ed2-160">TripleDesSha256</span></span>|<span data-ttu-id="d0ed2-161">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="d0ed2-163">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="d0ed2-165">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="d0ed2-167">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d0ed2-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d0ed2-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="d0ed2-169">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0ed2-170">子元素</span><span class="sxs-lookup"><span data-stu-id="d0ed2-170">Child Elements</span></span>  
  
|<span data-ttu-id="d0ed2-171">項目</span><span class="sxs-lookup"><span data-stu-id="d0ed2-171">Element</span></span>|<span data-ttu-id="d0ed2-172">說明</span><span class="sxs-lookup"><span data-stu-id="d0ed2-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0ed2-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d0ed2-173">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="d0ed2-174">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="d0ed2-175">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="d0ed2-176">issuer</span><span class="sxs-lookup"><span data-stu-id="d0ed2-176">issuer</span></span>|<span data-ttu-id="d0ed2-177">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="d0ed2-178">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="d0ed2-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="d0ed2-179">issuerMetadata</span></span>|<span data-ttu-id="d0ed2-180">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="d0ed2-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="d0ed2-181">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="d0ed2-182">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-182">A collection of token request parameters.</span></span> <span data-ttu-id="d0ed2-183">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0ed2-184">父項目</span><span class="sxs-lookup"><span data-stu-id="d0ed2-184">Parent Elements</span></span>  
  
|<span data-ttu-id="d0ed2-185">項目</span><span class="sxs-lookup"><span data-stu-id="d0ed2-185">Element</span></span>|<span data-ttu-id="d0ed2-186">描述</span><span class="sxs-lookup"><span data-stu-id="d0ed2-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0ed2-187">\<security></span><span class="sxs-lookup"><span data-stu-id="d0ed2-187">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="d0ed2-188">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d0ed2-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0ed2-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0ed2-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="d0ed2-190">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d0ed2-190">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d0ed2-191">繫結</span><span class="sxs-lookup"><span data-stu-id="d0ed2-191">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d0ed2-192">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d0ed2-192">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d0ed2-193">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="d0ed2-193">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d0ed2-194">\<binding></span><span class="sxs-lookup"><span data-stu-id="d0ed2-194">\<binding></span></span>](../../../misc/binding.md)
