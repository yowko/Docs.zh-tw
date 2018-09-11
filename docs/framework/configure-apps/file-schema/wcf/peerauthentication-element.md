---
title: '&lt;peerAuthentication&gt; 項目'
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4fb8cc4989313afa3ef16c90b54e0feae1ccb71d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274368"
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="07a6e-102">&lt;peerAuthentication&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="07a6e-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="07a6e-103">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="07a6e-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="07a6e-104">如需端對端程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="07a6e-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="07a6e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="07a6e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="07a6e-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="07a6e-106">\<behaviors></span></span>  
<span data-ttu-id="07a6e-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="07a6e-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="07a6e-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="07a6e-108">\<behavior></span></span>  
<span data-ttu-id="07a6e-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="07a6e-109">\<clientCredentials></span></span>  
<span data-ttu-id="07a6e-110">\<對等電腦 ></span><span class="sxs-lookup"><span data-stu-id="07a6e-110">\<peer></span></span>  
<span data-ttu-id="07a6e-111">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="07a6e-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a6e-112">語法</span><span class="sxs-lookup"><span data-stu-id="07a6e-112">Syntax</span></span>  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07a6e-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="07a6e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="07a6e-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="07a6e-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07a6e-115">屬性</span><span class="sxs-lookup"><span data-stu-id="07a6e-115">Attributes</span></span>  
  
|<span data-ttu-id="07a6e-116">屬性</span><span class="sxs-lookup"><span data-stu-id="07a6e-116">Attribute</span></span>|<span data-ttu-id="07a6e-117">描述</span><span class="sxs-lookup"><span data-stu-id="07a6e-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="07a6e-118">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="07a6e-118">Optional string.</span></span> <span data-ttu-id="07a6e-119">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="07a6e-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="07a6e-120">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="07a6e-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="07a6e-121">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="07a6e-121">Optional enumeration.</span></span> <span data-ttu-id="07a6e-122">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="07a6e-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="07a6e-123">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="07a6e-124">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="07a6e-125">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="07a6e-125">Optional enumeration.</span></span> <span data-ttu-id="07a6e-126">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="07a6e-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="07a6e-127">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="07a6e-128">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="07a6e-128">Optional enumeration.</span></span> <span data-ttu-id="07a6e-129">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="07a6e-130">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="07a6e-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="07a6e-131">針對執行驗證**受信任的人**將儲存在指定的存放區位置。</span><span class="sxs-lookup"><span data-stu-id="07a6e-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="07a6e-132">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="07a6e-133">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="07a6e-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="07a6e-134">值</span><span class="sxs-lookup"><span data-stu-id="07a6e-134">Value</span></span>|<span data-ttu-id="07a6e-135">描述</span><span class="sxs-lookup"><span data-stu-id="07a6e-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07a6e-136">String</span><span class="sxs-lookup"><span data-stu-id="07a6e-136">String</span></span>|<span data-ttu-id="07a6e-137">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="07a6e-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="07a6e-138">至少需要命名空間和型別名稱。</span><span class="sxs-lookup"><span data-stu-id="07a6e-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="07a6e-139">選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="07a6e-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="07a6e-140">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="07a6e-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="07a6e-141">值</span><span class="sxs-lookup"><span data-stu-id="07a6e-141">Value</span></span>|<span data-ttu-id="07a6e-142">描述</span><span class="sxs-lookup"><span data-stu-id="07a6e-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07a6e-143">列舉</span><span class="sxs-lookup"><span data-stu-id="07a6e-143">Enumeration</span></span>|<span data-ttu-id="07a6e-144">下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="07a6e-145">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="07a6e-146">如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="07a6e-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="07a6e-147">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="07a6e-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="07a6e-148">值</span><span class="sxs-lookup"><span data-stu-id="07a6e-148">Value</span></span>|<span data-ttu-id="07a6e-149">描述</span><span class="sxs-lookup"><span data-stu-id="07a6e-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07a6e-150">列舉</span><span class="sxs-lookup"><span data-stu-id="07a6e-150">Enumeration</span></span>|<span data-ttu-id="07a6e-151">下列其中一個值：`NoCheck`、`Online`、`Offline`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="07a6e-152">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="07a6e-153">如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="07a6e-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="07a6e-154">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="07a6e-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="07a6e-155">值</span><span class="sxs-lookup"><span data-stu-id="07a6e-155">Value</span></span>|<span data-ttu-id="07a6e-156">描述</span><span class="sxs-lookup"><span data-stu-id="07a6e-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07a6e-157">列舉</span><span class="sxs-lookup"><span data-stu-id="07a6e-157">Enumeration</span></span>|<span data-ttu-id="07a6e-158">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="07a6e-159">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="07a6e-160">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="07a6e-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="07a6e-161">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07a6e-162">子元素</span><span class="sxs-lookup"><span data-stu-id="07a6e-162">Child Elements</span></span>  
 <span data-ttu-id="07a6e-163">無。</span><span class="sxs-lookup"><span data-stu-id="07a6e-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07a6e-164">父項目</span><span class="sxs-lookup"><span data-stu-id="07a6e-164">Parent Elements</span></span>  
  
|<span data-ttu-id="07a6e-165">項目</span><span class="sxs-lookup"><span data-stu-id="07a6e-165">Element</span></span>|<span data-ttu-id="07a6e-166">描述</span><span class="sxs-lookup"><span data-stu-id="07a6e-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07a6e-167">\<peer></span><span class="sxs-lookup"><span data-stu-id="07a6e-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="07a6e-168">指定向對等服務驗證用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="07a6e-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07a6e-169">備註</span><span class="sxs-lookup"><span data-stu-id="07a6e-169">Remarks</span></span>  
 <span data-ttu-id="07a6e-170">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="07a6e-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="07a6e-171">這個項目會指定驗證程式，當網狀結構中進行鄰居對鄰居驗證時，就會叫用此驗證程式。</span><span class="sxs-lookup"><span data-stu-id="07a6e-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="07a6e-172">當新對等嘗試建立鄰居連線時，它會將自己的認證傳遞至對應的對等。</span><span class="sxs-lookup"><span data-stu-id="07a6e-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="07a6e-173">會叫用回應程式的驗證器來驗證遠端方的認證。</span><span class="sxs-lookup"><span data-stu-id="07a6e-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="07a6e-174">每次在網狀結構中建立對等連線時，對等的兩方會互相驗證，亦即會叫用兩端的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="07a6e-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a6e-175">範例</span><span class="sxs-lookup"><span data-stu-id="07a6e-175">Example</span></span>  
 <span data-ttu-id="07a6e-176">下列程式碼會將憑證驗證模式設定為 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="07a6e-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07a6e-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07a6e-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="07a6e-178">使用憑證</span><span class="sxs-lookup"><span data-stu-id="07a6e-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="07a6e-179">對等網路</span><span class="sxs-lookup"><span data-stu-id="07a6e-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="07a6e-180">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="07a6e-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="07a6e-181">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="07a6e-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="07a6e-182">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="07a6e-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
