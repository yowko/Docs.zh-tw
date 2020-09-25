---
title: <message> 的 <ws2007FederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: d71bce5e94568bdad3c52226fa1029a1dd87bfd9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204914"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="8fbff-102">\<message> 的 \<ws2007FederationHttpBinding> 項目</span><span class="sxs-lookup"><span data-stu-id="8fbff-102">\<message> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="8fbff-103">定義專案的訊息層級安全性設定 [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8fbff-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="8fbff-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fbff-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fbff-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8fbff-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8fbff-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8fbff-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fbff-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8fbff-107">Attributes</span></span>  
  
|<span data-ttu-id="8fbff-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8fbff-108">Attribute</span></span>|<span data-ttu-id="8fbff-109">描述</span><span class="sxs-lookup"><span data-stu-id="8fbff-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="8fbff-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8fbff-110">Optional.</span></span> <span data-ttu-id="8fbff-111">設定訊息加密、簽章和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="8fbff-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="8fbff-112">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="8fbff-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="8fbff-113">這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="8fbff-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="8fbff-114">請參閱下表列出的可能值。</span><span class="sxs-lookup"><span data-stu-id="8fbff-114">See the following table for possible values.</span></span> <span data-ttu-id="8fbff-115">預設值為 Basic256。</span><span class="sxs-lookup"><span data-stu-id="8fbff-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="8fbff-116">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="8fbff-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="8fbff-117">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="8fbff-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8fbff-118">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="8fbff-118">-   SymmetricKey</span></span><br /><span data-ttu-id="8fbff-119">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="8fbff-119">-   PublicKey</span></span><br /><span data-ttu-id="8fbff-120">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="8fbff-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="8fbff-121">預設為 SymmetricKey。</span><span class="sxs-lookup"><span data-stu-id="8fbff-121">The default is SymmetricKey.</span></span> <span data-ttu-id="8fbff-122">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="8fbff-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="8fbff-123">URI，指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="8fbff-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="8fbff-124">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="8fbff-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="8fbff-125">這個值會指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="8fbff-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="8fbff-126">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="8fbff-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="8fbff-127">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="8fbff-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="8fbff-128">值</span><span class="sxs-lookup"><span data-stu-id="8fbff-128">Value</span></span>|<span data-ttu-id="8fbff-129">描述</span><span class="sxs-lookup"><span data-stu-id="8fbff-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8fbff-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="8fbff-130">Basic128</span></span>|<span data-ttu-id="8fbff-131">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="8fbff-132">Basic192</span></span>|<span data-ttu-id="8fbff-133">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="8fbff-134">Basic256</span></span>|<span data-ttu-id="8fbff-135">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-136">Basic256Rsa15</span></span>|<span data-ttu-id="8fbff-137">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-138">Basic192Rsa15</span></span>|<span data-ttu-id="8fbff-139">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="8fbff-140">TripleDes</span></span>|<span data-ttu-id="8fbff-141">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-142">Basic128Rsa15</span></span>|<span data-ttu-id="8fbff-143">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-144">TripleDesRsa15</span></span>|<span data-ttu-id="8fbff-145">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="8fbff-146">Basic128Sha256</span></span>|<span data-ttu-id="8fbff-147">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="8fbff-148">Basic192Sha256</span></span>|<span data-ttu-id="8fbff-149">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="8fbff-150">Basic256Sha256</span></span>|<span data-ttu-id="8fbff-151">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="8fbff-152">TripleDesSha256</span></span>|<span data-ttu-id="8fbff-153">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="8fbff-155">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="8fbff-157">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="8fbff-159">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8fbff-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8fbff-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="8fbff-161">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="8fbff-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fbff-162">子元素</span><span class="sxs-lookup"><span data-stu-id="8fbff-162">Child Elements</span></span>  
  
|<span data-ttu-id="8fbff-163">項目</span><span class="sxs-lookup"><span data-stu-id="8fbff-163">Element</span></span>|<span data-ttu-id="8fbff-164">描述</span><span class="sxs-lookup"><span data-stu-id="8fbff-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="8fbff-165">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="8fbff-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="8fbff-166">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="8fbff-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="8fbff-167">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="8fbff-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="8fbff-168">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="8fbff-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="8fbff-169">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="8fbff-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="8fbff-170">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="8fbff-170">A collection of token request parameters.</span></span> <span data-ttu-id="8fbff-171">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="8fbff-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fbff-172">父項目</span><span class="sxs-lookup"><span data-stu-id="8fbff-172">Parent Elements</span></span>  
  
|<span data-ttu-id="8fbff-173">項目</span><span class="sxs-lookup"><span data-stu-id="8fbff-173">Element</span></span>|<span data-ttu-id="8fbff-174">描述</span><span class="sxs-lookup"><span data-stu-id="8fbff-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="8fbff-175">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="8fbff-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fbff-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fbff-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="8fbff-177">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8fbff-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8fbff-178">繫結</span><span class="sxs-lookup"><span data-stu-id="8fbff-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8fbff-179">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8fbff-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8fbff-180">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="8fbff-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
