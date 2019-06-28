---
title: <messageSenderAuthentication> 項目
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 804c280bcdb0fecc87f71121b7d95b5fd0268de9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423115"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="f7ee9-102">\<messageSenderAuthentication > 項目</span><span class="sxs-lookup"><span data-stu-id="f7ee9-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="f7ee9-103">指定對等訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="f7ee9-104">如需端對端程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="f7ee9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f7ee9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f7ee9-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f7ee9-106">\<behaviors></span></span>  
<span data-ttu-id="f7ee9-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f7ee9-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="f7ee9-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f7ee9-108">\<behavior></span></span>  
<span data-ttu-id="f7ee9-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="f7ee9-109">\<clientCredentials></span></span>  
<span data-ttu-id="f7ee9-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="f7ee9-110">\<peer></span></span>  
<span data-ttu-id="f7ee9-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="f7ee9-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7ee9-112">語法</span><span class="sxs-lookup"><span data-stu-id="f7ee9-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7ee9-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f7ee9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f7ee9-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f7ee9-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7ee9-115">屬性</span><span class="sxs-lookup"><span data-stu-id="f7ee9-115">Attributes</span></span>  
  
|<span data-ttu-id="f7ee9-116">屬性</span><span class="sxs-lookup"><span data-stu-id="f7ee9-116">Attribute</span></span>|<span data-ttu-id="f7ee9-117">描述</span><span class="sxs-lookup"><span data-stu-id="f7ee9-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="f7ee9-118">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f7ee9-119">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="f7ee9-120">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f7ee9-121">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="f7ee9-122">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f7ee9-123">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f7ee9-124">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="f7ee9-125">針對執行驗證**受信任的人**將儲存在指定的存放區位置。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="f7ee9-126">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="f7ee9-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="f7ee9-127">值</span><span class="sxs-lookup"><span data-stu-id="f7ee9-127">Value</span></span>|<span data-ttu-id="f7ee9-128">描述</span><span class="sxs-lookup"><span data-stu-id="f7ee9-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f7ee9-129">String</span><span class="sxs-lookup"><span data-stu-id="f7ee9-129">String</span></span>|<span data-ttu-id="f7ee9-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-130">Optional.</span></span> <span data-ttu-id="f7ee9-131">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="f7ee9-132">至少需要命名空間和型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="f7ee9-133">選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="f7ee9-134">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="f7ee9-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="f7ee9-135">值</span><span class="sxs-lookup"><span data-stu-id="f7ee9-135">Value</span></span>|<span data-ttu-id="f7ee9-136">描述</span><span class="sxs-lookup"><span data-stu-id="f7ee9-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f7ee9-137">列舉</span><span class="sxs-lookup"><span data-stu-id="f7ee9-137">Enumeration</span></span>|<span data-ttu-id="f7ee9-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-138">Optional.</span></span> <span data-ttu-id="f7ee9-139">下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="f7ee9-140">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="f7ee9-141">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="f7ee9-142">如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="f7ee9-143">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="f7ee9-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="f7ee9-144">值</span><span class="sxs-lookup"><span data-stu-id="f7ee9-144">Value</span></span>|<span data-ttu-id="f7ee9-145">描述</span><span class="sxs-lookup"><span data-stu-id="f7ee9-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f7ee9-146">列舉</span><span class="sxs-lookup"><span data-stu-id="f7ee9-146">Enumeration</span></span>|<span data-ttu-id="f7ee9-147">下列其中一個值：`NoCheck`、`Online`、`Offline`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="f7ee9-148">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="f7ee9-149">如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-149">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="f7ee9-150">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="f7ee9-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="f7ee9-151">值</span><span class="sxs-lookup"><span data-stu-id="f7ee9-151">Value</span></span>|<span data-ttu-id="f7ee9-152">描述</span><span class="sxs-lookup"><span data-stu-id="f7ee9-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f7ee9-153">列舉</span><span class="sxs-lookup"><span data-stu-id="f7ee9-153">Enumeration</span></span>|<span data-ttu-id="f7ee9-154">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f7ee9-155">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="f7ee9-156">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="f7ee9-157">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="f7ee9-158">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7ee9-159">子元素</span><span class="sxs-lookup"><span data-stu-id="f7ee9-159">Child Elements</span></span>  
 <span data-ttu-id="f7ee9-160">無。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7ee9-161">父項目</span><span class="sxs-lookup"><span data-stu-id="f7ee9-161">Parent Elements</span></span>  
  
|<span data-ttu-id="f7ee9-162">項目</span><span class="sxs-lookup"><span data-stu-id="f7ee9-162">Element</span></span>|<span data-ttu-id="f7ee9-163">描述</span><span class="sxs-lookup"><span data-stu-id="f7ee9-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7ee9-164">\<peer></span><span class="sxs-lookup"><span data-stu-id="f7ee9-164">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="f7ee9-165">指定向對等服務驗證用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7ee9-166">備註</span><span class="sxs-lookup"><span data-stu-id="f7ee9-166">Remarks</span></span>  
 <span data-ttu-id="f7ee9-167">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="f7ee9-168">針對輸出通道，每個訊息會使用簽章所提供的憑證[\<憑證 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-168">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="f7ee9-169">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="f7ee9-170">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7ee9-171">範例</span><span class="sxs-lookup"><span data-stu-id="f7ee9-171">Example</span></span>  
 <span data-ttu-id="f7ee9-172">下列程式碼會將訊息寄件者驗證模式設定為 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="f7ee9-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="f7ee9-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7ee9-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="f7ee9-174">使用憑證</span><span class="sxs-lookup"><span data-stu-id="f7ee9-174">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f7ee9-175">對等網路</span><span class="sxs-lookup"><span data-stu-id="f7ee9-175">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f7ee9-176">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f7ee9-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f7ee9-177">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f7ee9-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f7ee9-178">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="f7ee9-178">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
