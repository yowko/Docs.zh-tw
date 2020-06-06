---
title: <message> 的 <netTcpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 76c4a0a30b637bc168855b091029a959b858401e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739017"
---
# <a name="message-element-of-nettcpbinding"></a><span data-ttu-id="949bd-102">\<message> 的 \<netTcpBinding> 項目</span><span class="sxs-lookup"><span data-stu-id="949bd-102">\<message> element of \<netTcpBinding></span></span>
<span data-ttu-id="949bd-103">定義以設定之端點的訊息層級安全性需求類型 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="949bd-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="949bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="949bd-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="949bd-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="949bd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="949bd-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="949bd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="949bd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="949bd-107">Attributes</span></span>  
  
|<span data-ttu-id="949bd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="949bd-108">Attribute</span></span>|<span data-ttu-id="949bd-109">描述</span><span class="sxs-lookup"><span data-stu-id="949bd-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="949bd-110">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="949bd-110">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="949bd-111">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="949bd-111">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="949bd-112">這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="949bd-112">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="949bd-113">下表顯示可能的值。</span><span class="sxs-lookup"><span data-stu-id="949bd-113">Possible values are shown in the following table.</span></span> <span data-ttu-id="949bd-114">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="949bd-114">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="949bd-115">如果服務繫結指定的 `algorithmSuite` 值不等於預設值，且您是使用 Svcutil.exe 產生組態檔，則該檔案將無法正確產生，這時您就必須手動編輯組態檔，將此屬性設定為需要的值。</span><span class="sxs-lookup"><span data-stu-id="949bd-115">If the service binding specifies an `algorithmSuite` value that is not equal to the default, and you generate the configuration file using Svcutil.exe, then it is not generated correctly, and you must manually edit the configuration file to set this attribute to the desired value.</span></span>|  
|`clientCredentialType`|<span data-ttu-id="949bd-116">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="949bd-116">Specifies the type of credential to be used when performing client authentication using Message-based security.</span></span> <span data-ttu-id="949bd-117">下表顯示可能的值。</span><span class="sxs-lookup"><span data-stu-id="949bd-117">Possible values are shown in the following table.</span></span> <span data-ttu-id="949bd-118">預設值是 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="949bd-118">The default value is `UserName`.</span></span> <span data-ttu-id="949bd-119">此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="949bd-119">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="949bd-120">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="949bd-120">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="949bd-121">值</span><span class="sxs-lookup"><span data-stu-id="949bd-121">Value</span></span>|<span data-ttu-id="949bd-122">描述</span><span class="sxs-lookup"><span data-stu-id="949bd-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="949bd-123">Basic128</span><span class="sxs-lookup"><span data-stu-id="949bd-123">Basic128</span></span>|<span data-ttu-id="949bd-124">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-124">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-125">Basic192</span><span class="sxs-lookup"><span data-stu-id="949bd-125">Basic192</span></span>|<span data-ttu-id="949bd-126">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-126">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-127">Basic256</span><span class="sxs-lookup"><span data-stu-id="949bd-127">Basic256</span></span>|<span data-ttu-id="949bd-128">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-128">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-129">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-129">Basic256Rsa15</span></span>|<span data-ttu-id="949bd-130">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-130">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="949bd-131">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-131">Basic192Rsa15</span></span>|<span data-ttu-id="949bd-132">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-132">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="949bd-133">TripleDes</span><span class="sxs-lookup"><span data-stu-id="949bd-133">TripleDes</span></span>|<span data-ttu-id="949bd-134">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-134">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-135">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-135">Basic128Rsa15</span></span>|<span data-ttu-id="949bd-136">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-136">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="949bd-137">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-137">TripleDesRsa15</span></span>|<span data-ttu-id="949bd-138">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-138">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="949bd-139">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="949bd-139">Basic128Sha256</span></span>|<span data-ttu-id="949bd-140">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-140">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-141">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="949bd-141">Basic192Sha256</span></span>|<span data-ttu-id="949bd-142">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-142">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-143">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="949bd-143">Basic256Sha256</span></span>|<span data-ttu-id="949bd-144">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-144">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-145">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="949bd-145">TripleDesSha256</span></span>|<span data-ttu-id="949bd-146">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-146">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="949bd-147">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-147">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="949bd-148">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-148">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="949bd-149">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-149">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="949bd-150">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-150">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="949bd-151">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-151">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="949bd-152">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-152">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="949bd-153">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="949bd-153">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="949bd-154">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="949bd-154">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="949bd-155">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="949bd-155">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="949bd-156">值</span><span class="sxs-lookup"><span data-stu-id="949bd-156">Value</span></span>|<span data-ttu-id="949bd-157">描述</span><span class="sxs-lookup"><span data-stu-id="949bd-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="949bd-158">None</span><span class="sxs-lookup"><span data-stu-id="949bd-158">None</span></span>|<span data-ttu-id="949bd-159">這會允許服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="949bd-159">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="949bd-160">在服務上，這表示此服務不需要任何用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="949bd-160">On the service, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="949bd-161">在用戶端上，這表示此用戶端不提供任何用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="949bd-161">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="949bd-162">Windows</span><span class="sxs-lookup"><span data-stu-id="949bd-162">Windows</span></span>|<span data-ttu-id="949bd-163">允許 SOAP 交換在 Windows 認證的已驗證內容中。</span><span class="sxs-lookup"><span data-stu-id="949bd-163">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span>|  
|<span data-ttu-id="949bd-164">UserName</span><span class="sxs-lookup"><span data-stu-id="949bd-164">UserName</span></span>|<span data-ttu-id="949bd-165">允許服務要求用戶端必須使用 UserName 認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="949bd-165">Allows the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="949bd-166">WCF 不支援使用密碼傳送密碼摘要或衍生金鑰，也不支援使用這類金鑰維持訊息安全。</span><span class="sxs-lookup"><span data-stu-id="949bd-166">WCF does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="949bd-167">因此，在使用使用者名稱認證時，WCF 會強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="949bd-167">As such, WCF enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="949bd-168">這個認證模式會產生可互通交換或是無法互通的交涉 (根據 `negotiateServiceCredential` 屬性)。</span><span class="sxs-lookup"><span data-stu-id="949bd-168">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="949bd-169">憑證</span><span class="sxs-lookup"><span data-stu-id="949bd-169">Certificate</span></span>|<span data-ttu-id="949bd-170">允許服務要求用戶端使用憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="949bd-170">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="949bd-171">如果使用訊息安全性模式且 `negotiateServiceCredential` 屬性設定為 `false`，則必須為用戶端提供服務憑證。</span><span class="sxs-lookup"><span data-stu-id="949bd-171">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client must be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="949bd-172">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="949bd-172">IssuedToken</span></span>|<span data-ttu-id="949bd-173">指定通常由安全性權杖服務 (STS) 所發出的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="949bd-173">Specifies a custom token, usually issued by a Security Token Service (STS).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="949bd-174">子元素</span><span class="sxs-lookup"><span data-stu-id="949bd-174">Child Elements</span></span>  
 <span data-ttu-id="949bd-175">無</span><span class="sxs-lookup"><span data-stu-id="949bd-175">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="949bd-176">父項目</span><span class="sxs-lookup"><span data-stu-id="949bd-176">Parent Elements</span></span>  
  
|<span data-ttu-id="949bd-177">元素</span><span class="sxs-lookup"><span data-stu-id="949bd-177">Element</span></span>|<span data-ttu-id="949bd-178">描述</span><span class="sxs-lookup"><span data-stu-id="949bd-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="949bd-179">定義 <xref:System.ServiceModel.Configuration.NetTcpBindingElement> 的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="949bd-179">Defines the security capabilities for the <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="949bd-180">備註</span><span class="sxs-lookup"><span data-stu-id="949bd-180">Remarks</span></span>  
 <span data-ttu-id="949bd-181">訊息會使用訊息層級安全性達成 SOAP 訊息的完整性與機密性，以及通訊對等兩端的交互驗證。</span><span class="sxs-lookup"><span data-stu-id="949bd-181">Message uses message-level security for the integrity and confidentiality of the SOAP message, and for mutual authentication of the communication peers.</span></span> <span data-ttu-id="949bd-182">如果繫結上選取了這個安全性模式，通道堆疊會以訊息安全性繫結項目進行設定，且 SOAP 訊息的安全性會符合 WS-Security\* 標準。</span><span class="sxs-lookup"><span data-stu-id="949bd-182">If this security mode is selected on a binding, the channel stack is configured with message security binding elements and the SOAP messages are secured in compliance with WS-Security\* standards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949bd-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="949bd-183">See also</span></span>

- <xref:System.ServiceModel.MessageSecurityOverTcp>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="949bd-184">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="949bd-184">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="949bd-185">繫結</span><span class="sxs-lookup"><span data-stu-id="949bd-185">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="949bd-186">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="949bd-186">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="949bd-187">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="949bd-187">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
