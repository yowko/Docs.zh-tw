---
title: <message> 的 <wsFederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: ea320b1d97e742d4f90ec55502f3bd429803283d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204888"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="852d2-102">\<message> 的 \<wsFederationHttpBinding> 項目</span><span class="sxs-lookup"><span data-stu-id="852d2-102">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="852d2-103">定義的訊息層級安全性設定 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="852d2-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="852d2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="852d2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="852d2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="852d2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="852d2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="852d2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="852d2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="852d2-107">Attributes</span></span>  
  
|<span data-ttu-id="852d2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="852d2-108">Attribute</span></span>|<span data-ttu-id="852d2-109">描述</span><span class="sxs-lookup"><span data-stu-id="852d2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="852d2-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="852d2-110">algorithmSuite</span></span>|<span data-ttu-id="852d2-111">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="852d2-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="852d2-112">請參閱「algorithmSuite 屬性」表格中此屬性的有效值。</span><span class="sxs-lookup"><span data-stu-id="852d2-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="852d2-113">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="852d2-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="852d2-114">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="852d2-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="852d2-115">這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="852d2-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="852d2-116">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="852d2-116">issuedKeyType</span></span>|<span data-ttu-id="852d2-117">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="852d2-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="852d2-118">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="852d2-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="852d2-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="852d2-119">-   SymmetricKey</span></span><br /><span data-ttu-id="852d2-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="852d2-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="852d2-121">預設值為 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="852d2-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="852d2-122">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="852d2-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="852d2-123">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="852d2-123">issuedTokenType</span></span>|<span data-ttu-id="852d2-124">字串，其中包含的 URI 指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="852d2-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="852d2-125">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="852d2-125">The default is `null`.</span></span>|  
|<span data-ttu-id="852d2-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="852d2-126">negotiateServiceCredential</span></span>|<span data-ttu-id="852d2-127">布林值，指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="852d2-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="852d2-128">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="852d2-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="852d2-129">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="852d2-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="852d2-130">值</span><span class="sxs-lookup"><span data-stu-id="852d2-130">Value</span></span>|<span data-ttu-id="852d2-131">描述</span><span class="sxs-lookup"><span data-stu-id="852d2-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="852d2-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="852d2-132">Basic128</span></span>|<span data-ttu-id="852d2-133">使用 Basic128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="852d2-134">Basic192</span></span>|<span data-ttu-id="852d2-135">使用 Basic192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="852d2-136">Basic256</span></span>|<span data-ttu-id="852d2-137">使用 Basic256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-138">Basic256Rsa15</span></span>|<span data-ttu-id="852d2-139">將 Basic256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="852d2-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-140">Basic192Rsa15</span></span>|<span data-ttu-id="852d2-141">將 Basic192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="852d2-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="852d2-142">TripleDes</span></span>|<span data-ttu-id="852d2-143">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-144">Basic128Rsa15</span></span>|<span data-ttu-id="852d2-145">將 Basic128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="852d2-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-146">TripleDesRsa15</span></span>|<span data-ttu-id="852d2-147">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="852d2-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="852d2-148">Basic128Sha256</span></span>|<span data-ttu-id="852d2-149">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="852d2-150">Basic192Sha256</span></span>|<span data-ttu-id="852d2-151">將 Basic192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="852d2-152">Basic256Sha256</span></span>|<span data-ttu-id="852d2-153">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="852d2-154">TripleDesSha256</span></span>|<span data-ttu-id="852d2-155">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="852d2-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="852d2-157">將 Basic128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="852d2-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="852d2-159">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="852d2-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="852d2-161">將 Basic256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="852d2-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="852d2-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="852d2-163">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="852d2-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="852d2-164">子元素</span><span class="sxs-lookup"><span data-stu-id="852d2-164">Child Elements</span></span>  
  
|<span data-ttu-id="852d2-165">項目</span><span class="sxs-lookup"><span data-stu-id="852d2-165">Element</span></span>|<span data-ttu-id="852d2-166">描述</span><span class="sxs-lookup"><span data-stu-id="852d2-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="852d2-167">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="852d2-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="852d2-168">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="852d2-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="852d2-169">簽發者</span><span class="sxs-lookup"><span data-stu-id="852d2-169">issuer</span></span>|<span data-ttu-id="852d2-170">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="852d2-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="852d2-171">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="852d2-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="852d2-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="852d2-172">issuerMetadata</span></span>|<span data-ttu-id="852d2-173">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="852d2-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="852d2-174">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="852d2-174">A collection of token request parameters.</span></span> <span data-ttu-id="852d2-175">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="852d2-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="852d2-176">父項目</span><span class="sxs-lookup"><span data-stu-id="852d2-176">Parent Elements</span></span>  
  
|<span data-ttu-id="852d2-177">項目</span><span class="sxs-lookup"><span data-stu-id="852d2-177">Element</span></span>|<span data-ttu-id="852d2-178">描述</span><span class="sxs-lookup"><span data-stu-id="852d2-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="852d2-179">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="852d2-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="852d2-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="852d2-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="852d2-181">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="852d2-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="852d2-182">繫結</span><span class="sxs-lookup"><span data-stu-id="852d2-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="852d2-183">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="852d2-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="852d2-184">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="852d2-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
