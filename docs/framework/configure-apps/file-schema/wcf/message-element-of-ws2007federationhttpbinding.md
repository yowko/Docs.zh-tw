---
title: '&lt;ws2007FederationHttpBinding&gt; 的 &lt;message&gt; 項目'
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 3f0dbc3128af812c7fd09eed5acd90ab43ec8351
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516353"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="e6b06-102">&lt;ws2007FederationHttpBinding&gt; 的 &lt;message&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="e6b06-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="e6b06-103">定義訊息層級安全性設定[ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="e6b06-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="e6b06-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6b06-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6b06-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="e6b06-105">\<bindings></span></span>  
<span data-ttu-id="e6b06-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e6b06-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="e6b06-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="e6b06-107">\<binding></span></span>  
<span data-ttu-id="e6b06-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="e6b06-108">\<security></span></span>  
<span data-ttu-id="e6b06-109">\<message></span><span class="sxs-lookup"><span data-stu-id="e6b06-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b06-110">語法</span><span class="sxs-lookup"><span data-stu-id="e6b06-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
   <binding >  
      <security>  
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
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
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
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6b06-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6b06-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e6b06-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e6b06-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6b06-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e6b06-113">Attributes</span></span>  
  
|<span data-ttu-id="e6b06-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e6b06-114">Attribute</span></span>|<span data-ttu-id="e6b06-115">描述</span><span class="sxs-lookup"><span data-stu-id="e6b06-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="e6b06-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="e6b06-116">Optional.</span></span> <span data-ttu-id="e6b06-117">設定訊息加密、簽章和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="e6b06-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="e6b06-118">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="e6b06-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="e6b06-119">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="e6b06-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="e6b06-120">請參閱下表列出的可能值。</span><span class="sxs-lookup"><span data-stu-id="e6b06-120">See the following table for possible values.</span></span> <span data-ttu-id="e6b06-121">預設值為 Basic256。</span><span class="sxs-lookup"><span data-stu-id="e6b06-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="e6b06-122">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="e6b06-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="e6b06-123">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="e6b06-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e6b06-124">-   SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="e6b06-124">-   SymmetricKey</span></span><br /><span data-ttu-id="e6b06-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="e6b06-125">-   PublicKey</span></span><br /><span data-ttu-id="e6b06-126">-   BearerKey</span><span class="sxs-lookup"><span data-stu-id="e6b06-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="e6b06-127">預設為 SymmetricKey。</span><span class="sxs-lookup"><span data-stu-id="e6b06-127">The default is SymmetricKey.</span></span> <span data-ttu-id="e6b06-128">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="e6b06-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="e6b06-129">URI，指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="e6b06-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="e6b06-130">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="e6b06-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="e6b06-131">這個值會指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="e6b06-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="e6b06-132">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="e6b06-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="e6b06-133">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="e6b06-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="e6b06-134">值</span><span class="sxs-lookup"><span data-stu-id="e6b06-134">Value</span></span>|<span data-ttu-id="e6b06-135">描述</span><span class="sxs-lookup"><span data-stu-id="e6b06-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6b06-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="e6b06-136">Basic128</span></span>|<span data-ttu-id="e6b06-137">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="e6b06-138">Basic192</span></span>|<span data-ttu-id="e6b06-139">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="e6b06-140">Basic256</span></span>|<span data-ttu-id="e6b06-141">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-142">Basic256Rsa15</span></span>|<span data-ttu-id="e6b06-143">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-144">Basic192Rsa15</span></span>|<span data-ttu-id="e6b06-145">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="e6b06-146">TripleDes</span></span>|<span data-ttu-id="e6b06-147">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-148">Basic128Rsa15</span></span>|<span data-ttu-id="e6b06-149">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-150">TripleDesRsa15</span></span>|<span data-ttu-id="e6b06-151">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="e6b06-152">Basic128Sha256</span></span>|<span data-ttu-id="e6b06-153">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="e6b06-154">Basic192Sha256</span></span>|<span data-ttu-id="e6b06-155">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="e6b06-156">Basic256Sha256</span></span>|<span data-ttu-id="e6b06-157">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="e6b06-158">TripleDesSha256</span></span>|<span data-ttu-id="e6b06-159">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="e6b06-161">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="e6b06-163">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="e6b06-165">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e6b06-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e6b06-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="e6b06-167">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="e6b06-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6b06-168">子元素</span><span class="sxs-lookup"><span data-stu-id="e6b06-168">Child Elements</span></span>  
  
|<span data-ttu-id="e6b06-169">項目</span><span class="sxs-lookup"><span data-stu-id="e6b06-169">Element</span></span>|<span data-ttu-id="e6b06-170">描述</span><span class="sxs-lookup"><span data-stu-id="e6b06-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6b06-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e6b06-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="e6b06-172">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="e6b06-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="e6b06-173">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="e6b06-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="e6b06-174">\<issuer></span><span class="sxs-lookup"><span data-stu-id="e6b06-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="e6b06-175">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="e6b06-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="e6b06-176">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="e6b06-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="e6b06-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="e6b06-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="e6b06-178">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="e6b06-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="e6b06-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="e6b06-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="e6b06-180">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="e6b06-180">A collection of token request parameters.</span></span> <span data-ttu-id="e6b06-181">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="e6b06-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6b06-182">父項目</span><span class="sxs-lookup"><span data-stu-id="e6b06-182">Parent Elements</span></span>  
  
|<span data-ttu-id="e6b06-183">項目</span><span class="sxs-lookup"><span data-stu-id="e6b06-183">Element</span></span>|<span data-ttu-id="e6b06-184">描述</span><span class="sxs-lookup"><span data-stu-id="e6b06-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6b06-185">\<security></span><span class="sxs-lookup"><span data-stu-id="e6b06-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="e6b06-186">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e6b06-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6b06-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6b06-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="e6b06-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [保護服務和用戶端](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="e6b06-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="e6b06-189">繫結</span><span class="sxs-lookup"><span data-stu-id="e6b06-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e6b06-190">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e6b06-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e6b06-191">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e6b06-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e6b06-192">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="e6b06-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
