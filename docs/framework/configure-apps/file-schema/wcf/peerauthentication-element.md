---
title: <peerAuthentication> 項目
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400087"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="06964-102">\<peerAuthentication > 元素</span><span class="sxs-lookup"><span data-stu-id="06964-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="06964-103">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="06964-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="06964-104">如需對等程式設計的詳細資訊，請參閱[對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="06964-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="06964-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06964-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06964-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="06964-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="06964-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="06964-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="06964-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="06964-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="06964-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="06964-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="06964-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="06964-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="06964-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<對等 >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="06964-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="06964-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="06964-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06964-113">語法</span><span class="sxs-lookup"><span data-stu-id="06964-113">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06964-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="06964-114">Attributes and Elements</span></span>  
 <span data-ttu-id="06964-115">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="06964-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06964-116">屬性</span><span class="sxs-lookup"><span data-stu-id="06964-116">Attributes</span></span>  
  
|<span data-ttu-id="06964-117">屬性</span><span class="sxs-lookup"><span data-stu-id="06964-117">Attribute</span></span>|<span data-ttu-id="06964-118">描述</span><span class="sxs-lookup"><span data-stu-id="06964-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="06964-119">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="06964-119">Optional string.</span></span> <span data-ttu-id="06964-120">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="06964-120">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="06964-121">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="06964-121">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="06964-122">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="06964-122">Optional enumeration.</span></span> <span data-ttu-id="06964-123">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="06964-123">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="06964-124">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="06964-124">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="06964-125">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="06964-125">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="06964-126">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="06964-126">Optional enumeration.</span></span> <span data-ttu-id="06964-127">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="06964-127">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="06964-128">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="06964-128">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="06964-129">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="06964-129">Optional enumeration.</span></span> <span data-ttu-id="06964-130">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="06964-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="06964-131">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="06964-131">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="06964-132">會針對指定存放區位置中的「**受信任的人**」存放區執行驗證。</span><span class="sxs-lookup"><span data-stu-id="06964-132">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="06964-133">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="06964-133">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="06964-134">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="06964-134">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="06964-135">值</span><span class="sxs-lookup"><span data-stu-id="06964-135">Value</span></span>|<span data-ttu-id="06964-136">描述</span><span class="sxs-lookup"><span data-stu-id="06964-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06964-137">String</span><span class="sxs-lookup"><span data-stu-id="06964-137">String</span></span>|<span data-ttu-id="06964-138">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="06964-138">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="06964-139">至少需要命名空間和型別名稱。</span><span class="sxs-lookup"><span data-stu-id="06964-139">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="06964-140">選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="06964-140">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="06964-141">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="06964-141">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="06964-142">值</span><span class="sxs-lookup"><span data-stu-id="06964-142">Value</span></span>|<span data-ttu-id="06964-143">描述</span><span class="sxs-lookup"><span data-stu-id="06964-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06964-144">列舉</span><span class="sxs-lookup"><span data-stu-id="06964-144">Enumeration</span></span>|<span data-ttu-id="06964-145">下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。</span><span class="sxs-lookup"><span data-stu-id="06964-145">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="06964-146">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="06964-146">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="06964-147">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="06964-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="06964-148">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="06964-148">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="06964-149">值</span><span class="sxs-lookup"><span data-stu-id="06964-149">Value</span></span>|<span data-ttu-id="06964-150">描述</span><span class="sxs-lookup"><span data-stu-id="06964-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06964-151">列舉</span><span class="sxs-lookup"><span data-stu-id="06964-151">Enumeration</span></span>|<span data-ttu-id="06964-152">下列其中一個值：`NoCheck`、`Online`、`Offline`。</span><span class="sxs-lookup"><span data-stu-id="06964-152">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="06964-153">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="06964-153">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="06964-154">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="06964-154">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="06964-155">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="06964-155">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="06964-156">值</span><span class="sxs-lookup"><span data-stu-id="06964-156">Value</span></span>|<span data-ttu-id="06964-157">描述</span><span class="sxs-lookup"><span data-stu-id="06964-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06964-158">列舉</span><span class="sxs-lookup"><span data-stu-id="06964-158">Enumeration</span></span>|<span data-ttu-id="06964-159">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="06964-159">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="06964-160">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="06964-160">The default is `CurrentUser`.</span></span> <span data-ttu-id="06964-161">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="06964-161">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="06964-162">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="06964-162">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06964-163">子元素</span><span class="sxs-lookup"><span data-stu-id="06964-163">Child Elements</span></span>  
 <span data-ttu-id="06964-164">無。</span><span class="sxs-lookup"><span data-stu-id="06964-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06964-165">父項目</span><span class="sxs-lookup"><span data-stu-id="06964-165">Parent Elements</span></span>  
  
|<span data-ttu-id="06964-166">項目</span><span class="sxs-lookup"><span data-stu-id="06964-166">Element</span></span>|<span data-ttu-id="06964-167">描述</span><span class="sxs-lookup"><span data-stu-id="06964-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06964-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="06964-168">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="06964-169">指定向對等服務驗證用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="06964-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06964-170">備註</span><span class="sxs-lookup"><span data-stu-id="06964-170">Remarks</span></span>  
 <span data-ttu-id="06964-171">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="06964-171">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="06964-172">這個項目會指定驗證程式，當網狀結構中進行鄰居對鄰居驗證時，就會叫用此驗證程式。</span><span class="sxs-lookup"><span data-stu-id="06964-172">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="06964-173">當新對等嘗試建立鄰居連線時，它會將自己的認證傳遞至對應的對等。</span><span class="sxs-lookup"><span data-stu-id="06964-173">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="06964-174">會叫用回應程式的驗證器來驗證遠端方的認證。</span><span class="sxs-lookup"><span data-stu-id="06964-174">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="06964-175">每次在網狀結構中建立對等連線時，對等的兩方會互相驗證，亦即會叫用兩端的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="06964-175">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06964-176">範例</span><span class="sxs-lookup"><span data-stu-id="06964-176">Example</span></span>  
 <span data-ttu-id="06964-177">下列程式碼會將憑證驗證模式設定為 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="06964-177">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="06964-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06964-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="06964-179">使用憑證</span><span class="sxs-lookup"><span data-stu-id="06964-179">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="06964-180">對等網路</span><span class="sxs-lookup"><span data-stu-id="06964-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="06964-181">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="06964-181">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="06964-182">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="06964-182">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="06964-183">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="06964-183">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
