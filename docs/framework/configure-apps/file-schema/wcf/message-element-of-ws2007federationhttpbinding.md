---
title: <message> 的 <ws2007FederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: b1128bda6068a1fe3d8f5bb5ac29cc349f023b5b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397855"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="8f755-102">\<ws2007FederationHttpBinding > 的\<message > 元素</span><span class="sxs-lookup"><span data-stu-id="8f755-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="8f755-103">定義[ \<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md)元素的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="8f755-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="8f755-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f755-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f755-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8f755-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8f755-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8f755-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8f755-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8f755-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="8f755-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="8f755-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8f755-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8f755-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="8f755-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<訊息 >**</span><span class="sxs-lookup"><span data-stu-id="8f755-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f755-111">語法</span><span class="sxs-lookup"><span data-stu-id="8f755-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f755-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8f755-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8f755-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8f755-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f755-114">屬性</span><span class="sxs-lookup"><span data-stu-id="8f755-114">Attributes</span></span>  
  
|<span data-ttu-id="8f755-115">屬性</span><span class="sxs-lookup"><span data-stu-id="8f755-115">Attribute</span></span>|<span data-ttu-id="8f755-116">說明</span><span class="sxs-lookup"><span data-stu-id="8f755-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="8f755-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8f755-117">Optional.</span></span> <span data-ttu-id="8f755-118">設定訊息加密、簽章和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="8f755-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="8f755-119">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="8f755-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="8f755-120">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="8f755-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="8f755-121">請參閱下表列出的可能值。</span><span class="sxs-lookup"><span data-stu-id="8f755-121">See the following table for possible values.</span></span> <span data-ttu-id="8f755-122">預設值為 Basic256。</span><span class="sxs-lookup"><span data-stu-id="8f755-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="8f755-123">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="8f755-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="8f755-124">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="8f755-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8f755-125">-   SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="8f755-125">-   SymmetricKey</span></span><br /><span data-ttu-id="8f755-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="8f755-126">-   PublicKey</span></span><br /><span data-ttu-id="8f755-127">-   BearerKey</span><span class="sxs-lookup"><span data-stu-id="8f755-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="8f755-128">預設為 SymmetricKey。</span><span class="sxs-lookup"><span data-stu-id="8f755-128">The default is SymmetricKey.</span></span> <span data-ttu-id="8f755-129">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="8f755-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="8f755-130">URI，指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="8f755-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="8f755-131">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="8f755-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="8f755-132">這個值會指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="8f755-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="8f755-133">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="8f755-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="8f755-134">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="8f755-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="8f755-135">值</span><span class="sxs-lookup"><span data-stu-id="8f755-135">Value</span></span>|<span data-ttu-id="8f755-136">描述</span><span class="sxs-lookup"><span data-stu-id="8f755-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f755-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="8f755-137">Basic128</span></span>|<span data-ttu-id="8f755-138">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="8f755-139">Basic192</span></span>|<span data-ttu-id="8f755-140">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="8f755-141">Basic256</span></span>|<span data-ttu-id="8f755-142">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-143">Basic256Rsa15</span></span>|<span data-ttu-id="8f755-144">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8f755-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-145">Basic192Rsa15</span></span>|<span data-ttu-id="8f755-146">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8f755-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="8f755-147">TripleDes</span></span>|<span data-ttu-id="8f755-148">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-149">Basic128Rsa15</span></span>|<span data-ttu-id="8f755-150">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8f755-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-151">TripleDesRsa15</span></span>|<span data-ttu-id="8f755-152">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8f755-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="8f755-153">Basic128Sha256</span></span>|<span data-ttu-id="8f755-154">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="8f755-155">Basic192Sha256</span></span>|<span data-ttu-id="8f755-156">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="8f755-157">Basic256Sha256</span></span>|<span data-ttu-id="8f755-158">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="8f755-159">TripleDesSha256</span></span>|<span data-ttu-id="8f755-160">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8f755-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="8f755-162">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8f755-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="8f755-164">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8f755-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="8f755-166">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8f755-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8f755-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="8f755-168">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8f755-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f755-169">子元素</span><span class="sxs-lookup"><span data-stu-id="8f755-169">Child Elements</span></span>  
  
|<span data-ttu-id="8f755-170">項目</span><span class="sxs-lookup"><span data-stu-id="8f755-170">Element</span></span>|<span data-ttu-id="8f755-171">說明</span><span class="sxs-lookup"><span data-stu-id="8f755-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f755-172">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8f755-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="8f755-173">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="8f755-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="8f755-174">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="8f755-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="8f755-175">\<issuer></span><span class="sxs-lookup"><span data-stu-id="8f755-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="8f755-176">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="8f755-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="8f755-177">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="8f755-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="8f755-178">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="8f755-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="8f755-179">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="8f755-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="8f755-180">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="8f755-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="8f755-181">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="8f755-181">A collection of token request parameters.</span></span> <span data-ttu-id="8f755-182">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="8f755-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f755-183">父項目</span><span class="sxs-lookup"><span data-stu-id="8f755-183">Parent Elements</span></span>  
  
|<span data-ttu-id="8f755-184">項目</span><span class="sxs-lookup"><span data-stu-id="8f755-184">Element</span></span>|<span data-ttu-id="8f755-185">描述</span><span class="sxs-lookup"><span data-stu-id="8f755-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f755-186">\<security></span><span class="sxs-lookup"><span data-stu-id="8f755-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="8f755-187">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="8f755-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f755-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f755-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="8f755-189">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8f755-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8f755-190">繫結</span><span class="sxs-lookup"><span data-stu-id="8f755-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8f755-191">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8f755-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8f755-192">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="8f755-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8f755-193">\<binding></span><span class="sxs-lookup"><span data-stu-id="8f755-193">\<binding></span></span>](../../../misc/binding.md)
