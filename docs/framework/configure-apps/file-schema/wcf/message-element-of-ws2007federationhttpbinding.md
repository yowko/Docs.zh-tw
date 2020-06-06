---
title: <message> 的 <ws2007FederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738992"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="6ecf4-102">\<message> 的 \<ws2007FederationHttpBinding> 項目</span><span class="sxs-lookup"><span data-stu-id="6ecf4-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="6ecf4-103">定義元素的訊息層級安全性設定 [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="6ecf4-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ecf4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ecf4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6ecf4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6ecf4-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ecf4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6ecf4-107">Attributes</span></span>  
  
|<span data-ttu-id="6ecf4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6ecf4-108">Attribute</span></span>|<span data-ttu-id="6ecf4-109">描述</span><span class="sxs-lookup"><span data-stu-id="6ecf4-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="6ecf4-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-110">Optional.</span></span> <span data-ttu-id="6ecf4-111">設定訊息加密、簽章和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="6ecf4-112">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="6ecf4-113">這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="6ecf4-114">請參閱下表列出的可能值。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-114">See the following table for possible values.</span></span> <span data-ttu-id="6ecf4-115">預設值為 Basic256。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="6ecf4-116">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="6ecf4-117">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="6ecf4-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6ecf4-118">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="6ecf4-118">-   SymmetricKey</span></span><br /><span data-ttu-id="6ecf4-119">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="6ecf4-119">-   PublicKey</span></span><br /><span data-ttu-id="6ecf4-120">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="6ecf4-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="6ecf4-121">預設為 SymmetricKey。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-121">The default is SymmetricKey.</span></span> <span data-ttu-id="6ecf4-122">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="6ecf4-123">URI，指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="6ecf4-124">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="6ecf4-125">這個值會指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="6ecf4-126">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="6ecf4-127">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="6ecf4-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="6ecf4-128">值</span><span class="sxs-lookup"><span data-stu-id="6ecf4-128">Value</span></span>|<span data-ttu-id="6ecf4-129">描述</span><span class="sxs-lookup"><span data-stu-id="6ecf4-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6ecf4-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="6ecf4-130">Basic128</span></span>|<span data-ttu-id="6ecf4-131">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="6ecf4-132">Basic192</span></span>|<span data-ttu-id="6ecf4-133">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="6ecf4-134">Basic256</span></span>|<span data-ttu-id="6ecf4-135">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-136">Basic256Rsa15</span></span>|<span data-ttu-id="6ecf4-137">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-138">Basic192Rsa15</span></span>|<span data-ttu-id="6ecf4-139">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="6ecf4-140">TripleDes</span></span>|<span data-ttu-id="6ecf4-141">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-142">Basic128Rsa15</span></span>|<span data-ttu-id="6ecf4-143">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-144">TripleDesRsa15</span></span>|<span data-ttu-id="6ecf4-145">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="6ecf4-146">Basic128Sha256</span></span>|<span data-ttu-id="6ecf4-147">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="6ecf4-148">Basic192Sha256</span></span>|<span data-ttu-id="6ecf4-149">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="6ecf4-150">Basic256Sha256</span></span>|<span data-ttu-id="6ecf4-151">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="6ecf4-152">TripleDesSha256</span></span>|<span data-ttu-id="6ecf4-153">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="6ecf4-155">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="6ecf4-157">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="6ecf4-159">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="6ecf4-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="6ecf4-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="6ecf4-161">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ecf4-162">子元素</span><span class="sxs-lookup"><span data-stu-id="6ecf4-162">Child Elements</span></span>  
  
|<span data-ttu-id="6ecf4-163">元素</span><span class="sxs-lookup"><span data-stu-id="6ecf4-163">Element</span></span>|<span data-ttu-id="6ecf4-164">描述</span><span class="sxs-lookup"><span data-stu-id="6ecf4-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="6ecf4-165">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="6ecf4-166">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="6ecf4-167">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="6ecf4-168">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="6ecf4-169">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="6ecf4-170">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-170">A collection of token request parameters.</span></span> <span data-ttu-id="6ecf4-171">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ecf4-172">父項目</span><span class="sxs-lookup"><span data-stu-id="6ecf4-172">Parent Elements</span></span>  
  
|<span data-ttu-id="6ecf4-173">元素</span><span class="sxs-lookup"><span data-stu-id="6ecf4-173">Element</span></span>|<span data-ttu-id="6ecf4-174">描述</span><span class="sxs-lookup"><span data-stu-id="6ecf4-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="6ecf4-175">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6ecf4-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ecf4-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ecf4-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="6ecf4-177">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="6ecf4-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6ecf4-178">繫結</span><span class="sxs-lookup"><span data-stu-id="6ecf4-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6ecf4-179">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6ecf4-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6ecf4-180">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6ecf4-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
