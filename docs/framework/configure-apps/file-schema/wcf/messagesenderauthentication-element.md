---
title: <messageSenderAuthentication> 項目
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397781"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="bdce0-102">\<messageSenderAuthentication > 元素</span><span class="sxs-lookup"><span data-stu-id="bdce0-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="bdce0-103">指定對等訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="bdce0-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="bdce0-104">如需對等程式設計的詳細資訊，請參閱[對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="bdce0-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="bdce0-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdce0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bdce0-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bdce0-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bdce0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bdce0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bdce0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bdce0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="bdce0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bdce0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="bdce0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bdce0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="bdce0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<對等 >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdce0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="bdce0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<messageSenderAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="bdce0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdce0-113">語法</span><span class="sxs-lookup"><span data-stu-id="bdce0-113">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdce0-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bdce0-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bdce0-115">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="bdce0-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdce0-116">屬性</span><span class="sxs-lookup"><span data-stu-id="bdce0-116">Attributes</span></span>  
  
|<span data-ttu-id="bdce0-117">屬性</span><span class="sxs-lookup"><span data-stu-id="bdce0-117">Attribute</span></span>|<span data-ttu-id="bdce0-118">描述</span><span class="sxs-lookup"><span data-stu-id="bdce0-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="bdce0-119">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="bdce0-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="bdce0-120">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="bdce0-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="bdce0-121">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="bdce0-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="bdce0-122">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-122">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="bdce0-123">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="bdce0-123">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="bdce0-124">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-124">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="bdce0-125">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="bdce0-125">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="bdce0-126">會針對指定存放區位置中的「**受信任的人**」存放區執行驗證。</span><span class="sxs-lookup"><span data-stu-id="bdce0-126">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="bdce0-127">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="bdce0-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="bdce0-128">值</span><span class="sxs-lookup"><span data-stu-id="bdce0-128">Value</span></span>|<span data-ttu-id="bdce0-129">描述</span><span class="sxs-lookup"><span data-stu-id="bdce0-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdce0-130">String</span><span class="sxs-lookup"><span data-stu-id="bdce0-130">String</span></span>|<span data-ttu-id="bdce0-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bdce0-131">Optional.</span></span> <span data-ttu-id="bdce0-132">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="bdce0-132">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="bdce0-133">至少需要命名空間和型別名稱。</span><span class="sxs-lookup"><span data-stu-id="bdce0-133">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="bdce0-134">選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="bdce0-134">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="bdce0-135">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="bdce0-135">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="bdce0-136">值</span><span class="sxs-lookup"><span data-stu-id="bdce0-136">Value</span></span>|<span data-ttu-id="bdce0-137">說明</span><span class="sxs-lookup"><span data-stu-id="bdce0-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdce0-138">列舉</span><span class="sxs-lookup"><span data-stu-id="bdce0-138">Enumeration</span></span>|<span data-ttu-id="bdce0-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bdce0-139">Optional.</span></span> <span data-ttu-id="bdce0-140">下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-140">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="bdce0-141">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-141">The default is `ChainTrust`.</span></span> <span data-ttu-id="bdce0-142">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-142">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="bdce0-143">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="bdce0-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="bdce0-144">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="bdce0-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="bdce0-145">值</span><span class="sxs-lookup"><span data-stu-id="bdce0-145">Value</span></span>|<span data-ttu-id="bdce0-146">描述</span><span class="sxs-lookup"><span data-stu-id="bdce0-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdce0-147">列舉</span><span class="sxs-lookup"><span data-stu-id="bdce0-147">Enumeration</span></span>|<span data-ttu-id="bdce0-148">下列其中一個值：`NoCheck`、`Online`、`Offline`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-148">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="bdce0-149">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-149">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="bdce0-150">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="bdce0-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="bdce0-151">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="bdce0-151">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="bdce0-152">值</span><span class="sxs-lookup"><span data-stu-id="bdce0-152">Value</span></span>|<span data-ttu-id="bdce0-153">說明</span><span class="sxs-lookup"><span data-stu-id="bdce0-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdce0-154">列舉</span><span class="sxs-lookup"><span data-stu-id="bdce0-154">Enumeration</span></span>|<span data-ttu-id="bdce0-155">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-155">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="bdce0-156">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-156">The default is `CurrentUser`.</span></span> <span data-ttu-id="bdce0-157">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="bdce0-157">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="bdce0-158">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-158">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="bdce0-159">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-159">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdce0-160">子元素</span><span class="sxs-lookup"><span data-stu-id="bdce0-160">Child Elements</span></span>  
 <span data-ttu-id="bdce0-161">無。</span><span class="sxs-lookup"><span data-stu-id="bdce0-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdce0-162">父項目</span><span class="sxs-lookup"><span data-stu-id="bdce0-162">Parent Elements</span></span>  
  
|<span data-ttu-id="bdce0-163">項目</span><span class="sxs-lookup"><span data-stu-id="bdce0-163">Element</span></span>|<span data-ttu-id="bdce0-164">說明</span><span class="sxs-lookup"><span data-stu-id="bdce0-164">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdce0-165">\<peer></span><span class="sxs-lookup"><span data-stu-id="bdce0-165">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="bdce0-166">指定向對等服務驗證用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="bdce0-166">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdce0-167">備註</span><span class="sxs-lookup"><span data-stu-id="bdce0-167">Remarks</span></span>  
 <span data-ttu-id="bdce0-168">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="bdce0-168">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="bdce0-169">針對輸出通道，每則訊息都會使用[ \<憑證 >](certificate-element.md)所提供的憑證進行簽署。</span><span class="sxs-lookup"><span data-stu-id="bdce0-169">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="bdce0-170">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="bdce0-170">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="bdce0-171">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="bdce0-171">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdce0-172">範例</span><span class="sxs-lookup"><span data-stu-id="bdce0-172">Example</span></span>  
 <span data-ttu-id="bdce0-173">下列程式碼會將訊息寄件者驗證模式設定為 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="bdce0-173">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdce0-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdce0-174">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="bdce0-175">使用憑證</span><span class="sxs-lookup"><span data-stu-id="bdce0-175">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="bdce0-176">對等網路</span><span class="sxs-lookup"><span data-stu-id="bdce0-176">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="bdce0-177">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bdce0-177">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="bdce0-178">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bdce0-178">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="bdce0-179">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="bdce0-179">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
