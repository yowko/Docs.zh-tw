---
title: "&lt;netTcpBinding&gt; 的 &lt;message&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae44c80f99b2753b4914ff0844fd9538f3ac3f34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a><span data-ttu-id="06d22-102">&lt;netTcpBinding&gt; 的 &lt;message&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="06d22-102">&lt;message&gt; element of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="06d22-103">定義的訊息層級安全性需求與設定之端點的型別[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="06d22-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="06d22-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="06d22-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="06d22-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="06d22-105">\<bindings></span></span>  
<span data-ttu-id="06d22-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="06d22-106">\<netTcpBinding></span></span>  
<span data-ttu-id="06d22-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="06d22-107">\<binding></span></span>  
<span data-ttu-id="06d22-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="06d22-108">\<security></span></span>  
<span data-ttu-id="06d22-109">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="06d22-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d22-110">語法</span><span class="sxs-lookup"><span data-stu-id="06d22-110">Syntax</span></span>  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06d22-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="06d22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="06d22-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="06d22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06d22-113">屬性</span><span class="sxs-lookup"><span data-stu-id="06d22-113">Attributes</span></span>  
  
|<span data-ttu-id="06d22-114">屬性</span><span class="sxs-lookup"><span data-stu-id="06d22-114">Attribute</span></span>|<span data-ttu-id="06d22-115">描述</span><span class="sxs-lookup"><span data-stu-id="06d22-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="06d22-116">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="06d22-116">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="06d22-117">這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。</span><span class="sxs-lookup"><span data-stu-id="06d22-117">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="06d22-118">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="06d22-118">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="06d22-119">下表列出可能的值。</span><span class="sxs-lookup"><span data-stu-id="06d22-119">Possible values are shown in the following table.</span></span> <span data-ttu-id="06d22-120">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="06d22-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="06d22-121">如果服務繫結指定的 `algorithmSuite` 值不等於預設值，且您是使用 Svcutil.exe 產生組態檔，則該檔案將無法正確產生，這時您就必須手動編輯組態檔，將此屬性設定為需要的值。</span><span class="sxs-lookup"><span data-stu-id="06d22-121">If the service binding specifies an `algorithmSuite` value that is not equal to the default, and you generate the configuration file using Svcutil.exe, then it is not generated correctly, and you must manually edit the configuration file to set this attribute to the desired value.</span></span>|  
|`clientCredentialType`|<span data-ttu-id="06d22-122">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="06d22-122">Specifies the type of credential to be used when performing client authentication using Message-based security.</span></span> <span data-ttu-id="06d22-123">下表列出可能的值。</span><span class="sxs-lookup"><span data-stu-id="06d22-123">Possible values are shown in the following table.</span></span> <span data-ttu-id="06d22-124">預設值是 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="06d22-124">The default value is `UserName`.</span></span> <span data-ttu-id="06d22-125">此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="06d22-125">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="06d22-126">algorithmSuite 屬性</span><span class="sxs-lookup"><span data-stu-id="06d22-126">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="06d22-127">值</span><span class="sxs-lookup"><span data-stu-id="06d22-127">Value</span></span>|<span data-ttu-id="06d22-128">描述</span><span class="sxs-lookup"><span data-stu-id="06d22-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06d22-129">Basic128</span><span class="sxs-lookup"><span data-stu-id="06d22-129">Basic128</span></span>|<span data-ttu-id="06d22-130">使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-130">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-131">Basic192</span><span class="sxs-lookup"><span data-stu-id="06d22-131">Basic192</span></span>|<span data-ttu-id="06d22-132">使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-132">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-133">Basic256</span><span class="sxs-lookup"><span data-stu-id="06d22-133">Basic256</span></span>|<span data-ttu-id="06d22-134">使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-134">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-135">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-135">Basic256Rsa15</span></span>|<span data-ttu-id="06d22-136">將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-136">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="06d22-137">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-137">Basic192Rsa15</span></span>|<span data-ttu-id="06d22-138">將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-138">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="06d22-139">TripleDes</span><span class="sxs-lookup"><span data-stu-id="06d22-139">TripleDes</span></span>|<span data-ttu-id="06d22-140">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-140">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-141">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-141">Basic128Rsa15</span></span>|<span data-ttu-id="06d22-142">將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-142">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="06d22-143">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-143">TripleDesRsa15</span></span>|<span data-ttu-id="06d22-144">使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-144">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="06d22-145">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="06d22-145">Basic128Sha256</span></span>|<span data-ttu-id="06d22-146">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-146">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-147">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="06d22-147">Basic192Sha256</span></span>|<span data-ttu-id="06d22-148">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-148">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-149">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="06d22-149">Basic256Sha256</span></span>|<span data-ttu-id="06d22-150">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-150">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-151">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="06d22-151">TripleDesSha256</span></span>|<span data-ttu-id="06d22-152">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-152">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="06d22-153">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-153">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="06d22-154">將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-154">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="06d22-155">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-155">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="06d22-156">將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="06d22-157">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-157">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="06d22-158">將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="06d22-159">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="06d22-159">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="06d22-160">將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。</span><span class="sxs-lookup"><span data-stu-id="06d22-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="06d22-161">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="06d22-161">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="06d22-162">值</span><span class="sxs-lookup"><span data-stu-id="06d22-162">Value</span></span>|<span data-ttu-id="06d22-163">描述</span><span class="sxs-lookup"><span data-stu-id="06d22-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06d22-164">無</span><span class="sxs-lookup"><span data-stu-id="06d22-164">None</span></span>|<span data-ttu-id="06d22-165">這會允許服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="06d22-165">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="06d22-166">在服務上，這表示此服務不需要任何用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="06d22-166">On the service, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="06d22-167">在用戶端上，這表示此用戶端不提供任何用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="06d22-167">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="06d22-168">Windows</span><span class="sxs-lookup"><span data-stu-id="06d22-168">Windows</span></span>|<span data-ttu-id="06d22-169">允許 SOAP 交換在 Windows 認證的已驗證內容中。</span><span class="sxs-lookup"><span data-stu-id="06d22-169">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span>|  
|<span data-ttu-id="06d22-170">UserName</span><span class="sxs-lookup"><span data-stu-id="06d22-170">UserName</span></span>|<span data-ttu-id="06d22-171">允許服務要求用戶端必須使用 UserName 認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="06d22-171">Allows the service to require that the client be authenticated using a UserName credential.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="06d22-172"> 不支援傳送密碼摘要，或是使用密碼衍生金鑰，甚至對訊息安全性使用該金鑰。</span><span class="sxs-lookup"><span data-stu-id="06d22-172"> does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="06d22-173">這麼一來，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會在使用 UserName 認證時強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="06d22-173">As such, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="06d22-174">這個認證模式會產生可互通交換或是無法互通的交涉 (根據 `negotiateServiceCredential` 屬性)。</span><span class="sxs-lookup"><span data-stu-id="06d22-174">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="06d22-175">憑證</span><span class="sxs-lookup"><span data-stu-id="06d22-175">Certificate</span></span>|<span data-ttu-id="06d22-176">允許服務要求用戶端使用憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="06d22-176">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="06d22-177">如果使用訊息安全性模式且 `negotiateServiceCredential` 屬性設定為 `false`，則必須為用戶端提供服務憑證。</span><span class="sxs-lookup"><span data-stu-id="06d22-177">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client must be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="06d22-178">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="06d22-178">IssuedToken</span></span>|<span data-ttu-id="06d22-179">指定通常由安全性權杖服務 (STS) 所發出的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="06d22-179">Specifies a custom token, usually issued by a Security Token Service (STS).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06d22-180">子元素</span><span class="sxs-lookup"><span data-stu-id="06d22-180">Child Elements</span></span>  
 <span data-ttu-id="06d22-181">無</span><span class="sxs-lookup"><span data-stu-id="06d22-181">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06d22-182">父項目</span><span class="sxs-lookup"><span data-stu-id="06d22-182">Parent Elements</span></span>  
  
|<span data-ttu-id="06d22-183">項目</span><span class="sxs-lookup"><span data-stu-id="06d22-183">Element</span></span>|<span data-ttu-id="06d22-184">描述</span><span class="sxs-lookup"><span data-stu-id="06d22-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06d22-185">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="06d22-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="06d22-186">定義 <xref:System.ServiceModel.Configuration.NetTcpBindingElement> 的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="06d22-186">Defines the security capabilities for the <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06d22-187">備註</span><span class="sxs-lookup"><span data-stu-id="06d22-187">Remarks</span></span>  
 <span data-ttu-id="06d22-188">訊息會使用訊息層級安全性達成 SOAP 訊息的完整性與機密性，以及通訊對等兩端的交互驗證。</span><span class="sxs-lookup"><span data-stu-id="06d22-188">Message uses message-level security for the integrity and confidentiality of the SOAP message, and for mutual authentication of the communication peers.</span></span> <span data-ttu-id="06d22-189">如果繫結上選取了這個安全性模式，通道堆疊會以訊息安全性繫結項目進行設定，且 SOAP 訊息的安全性會符合 WS-Security* 標準。</span><span class="sxs-lookup"><span data-stu-id="06d22-189">If this security mode is selected on a binding, the channel stack is configured with message security binding elements and the SOAP messages are secured in compliance with WS-Security* standards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d22-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="06d22-190">See Also</span></span>  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="06d22-191">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="06d22-191">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="06d22-192">繫結</span><span class="sxs-lookup"><span data-stu-id="06d22-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="06d22-193">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="06d22-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="06d22-194">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="06d22-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="06d22-195">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="06d22-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
