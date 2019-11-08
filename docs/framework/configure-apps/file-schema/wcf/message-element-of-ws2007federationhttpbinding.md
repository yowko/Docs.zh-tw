---
title: <message> 的 <ws2007FederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738992"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="7f7ed-102">\<ws2007FederationHttpBinding 的 \<message > 元素 ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="7f7ed-103">定義[\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md)元素的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="7f7ed-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f7ed-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7f7ed-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7f7ed-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7f7ed-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7f7ed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7f7ed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="7f7ed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7f7ed-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7f7ed-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="7f7ed-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**訊息 >**</span><span class="sxs-lookup"><span data-stu-id="7f7ed-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f7ed-111">語法</span><span class="sxs-lookup"><span data-stu-id="7f7ed-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f7ed-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f7ed-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7f7ed-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f7ed-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7f7ed-114">Attributes</span></span>  
  
|<span data-ttu-id="7f7ed-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7f7ed-115">Attribute</span></span>|<span data-ttu-id="7f7ed-116">描述</span><span class="sxs-lookup"><span data-stu-id="7f7ed-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="7f7ed-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-117">Optional.</span></span> <span data-ttu-id="7f7ed-118">設定訊息加密、簽章和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="7f7ed-119">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="7f7ed-120">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="7f7ed-121">請參閱下表列出的可能值。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-121">See the following table for possible values.</span></span> <span data-ttu-id="7f7ed-122">預設值為 Basic256。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="7f7ed-123">指定要發行的金鑰類型。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="7f7ed-124">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="7f7ed-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7f7ed-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="7f7ed-125">-   SymmetricKey</span></span><br /><span data-ttu-id="7f7ed-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="7f7ed-126">-   PublicKey</span></span><br /><span data-ttu-id="7f7ed-127">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="7f7ed-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="7f7ed-128">預設為 SymmetricKey。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-128">The default is SymmetricKey.</span></span> <span data-ttu-id="7f7ed-129">此屬性的型別為 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="7f7ed-130">URI，指定要發行的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="7f7ed-131">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="7f7ed-132">這個值會指定服務認證是否應交換做為交涉的一部分，或可供超出範圍使用。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="7f7ed-133">預設為 `true`，意指交涉服務認證。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="7f7ed-134">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="7f7ed-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="7f7ed-135">值</span><span class="sxs-lookup"><span data-stu-id="7f7ed-135">Value</span></span>|<span data-ttu-id="7f7ed-136">描述</span><span class="sxs-lookup"><span data-stu-id="7f7ed-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f7ed-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="7f7ed-137">Basic128</span></span>|<span data-ttu-id="7f7ed-138">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="7f7ed-139">Basic192</span></span>|<span data-ttu-id="7f7ed-140">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="7f7ed-141">Basic256</span></span>|<span data-ttu-id="7f7ed-142">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-143">Basic256Rsa15</span></span>|<span data-ttu-id="7f7ed-144">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-145">Basic192Rsa15</span></span>|<span data-ttu-id="7f7ed-146">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="7f7ed-147">TripleDes</span></span>|<span data-ttu-id="7f7ed-148">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-149">Basic128Rsa15</span></span>|<span data-ttu-id="7f7ed-150">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-151">TripleDesRsa15</span></span>|<span data-ttu-id="7f7ed-152">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="7f7ed-153">Basic128Sha256</span></span>|<span data-ttu-id="7f7ed-154">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="7f7ed-155">Basic192Sha256</span></span>|<span data-ttu-id="7f7ed-156">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="7f7ed-157">Basic256Sha256</span></span>|<span data-ttu-id="7f7ed-158">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="7f7ed-159">TripleDesSha256</span></span>|<span data-ttu-id="7f7ed-160">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="7f7ed-162">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="7f7ed-164">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="7f7ed-166">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7f7ed-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7f7ed-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="7f7ed-168">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f7ed-169">子項目</span><span class="sxs-lookup"><span data-stu-id="7f7ed-169">Child Elements</span></span>  
  
|<span data-ttu-id="7f7ed-170">項目</span><span class="sxs-lookup"><span data-stu-id="7f7ed-170">Element</span></span>|<span data-ttu-id="7f7ed-171">描述</span><span class="sxs-lookup"><span data-stu-id="7f7ed-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f7ed-172">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="7f7ed-173">指定這個繫結之宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="7f7ed-174">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="7f7ed-175">\<簽發者 ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="7f7ed-176">指定發行安全性權杖的端點。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="7f7ed-177">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="7f7ed-178">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="7f7ed-179">指定簽發者的端點位址。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="7f7ed-180">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="7f7ed-181">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-181">A collection of token request parameters.</span></span> <span data-ttu-id="7f7ed-182">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f7ed-183">父項目</span><span class="sxs-lookup"><span data-stu-id="7f7ed-183">Parent Elements</span></span>  
  
|<span data-ttu-id="7f7ed-184">項目</span><span class="sxs-lookup"><span data-stu-id="7f7ed-184">Element</span></span>|<span data-ttu-id="7f7ed-185">描述</span><span class="sxs-lookup"><span data-stu-id="7f7ed-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f7ed-186">\<security ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="7f7ed-187">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7f7ed-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f7ed-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f7ed-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="7f7ed-189">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="7f7ed-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7f7ed-190">繫結</span><span class="sxs-lookup"><span data-stu-id="7f7ed-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7f7ed-191">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="7f7ed-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7f7ed-192">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="7f7ed-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7f7ed-193">\<binding ></span><span class="sxs-lookup"><span data-stu-id="7f7ed-193">\<binding></span></span>](bindings.md)
