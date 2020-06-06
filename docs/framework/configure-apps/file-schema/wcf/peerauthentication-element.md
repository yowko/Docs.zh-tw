---
title: <peerAuthentication> 項目
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400087"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="6e3f4-102">\<peerAuthentication> 項目</span><span class="sxs-lookup"><span data-stu-id="6e3f4-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="6e3f4-103">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="6e3f4-104">如需對等程式設計的詳細資訊，請參閱[對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="6e3f4-105">語法</span><span class="sxs-lookup"><span data-stu-id="6e3f4-105">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e3f4-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6e3f4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6e3f4-107">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6e3f4-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e3f4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6e3f4-108">Attributes</span></span>  
  
|<span data-ttu-id="6e3f4-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6e3f4-109">Attribute</span></span>|<span data-ttu-id="6e3f4-110">描述</span><span class="sxs-lookup"><span data-stu-id="6e3f4-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="6e3f4-111">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-111">Optional string.</span></span> <span data-ttu-id="6e3f4-112">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="6e3f4-113">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="6e3f4-114">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-114">Optional enumeration.</span></span> <span data-ttu-id="6e3f4-115">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="6e3f4-116">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-116">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="6e3f4-117">預設值為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-117">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="6e3f4-118">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-118">Optional enumeration.</span></span> <span data-ttu-id="6e3f4-119">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="6e3f4-120">預設值為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-120">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="6e3f4-121">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-121">Optional enumeration.</span></span> <span data-ttu-id="6e3f4-122">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6e3f4-123">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="6e3f4-124">會針對指定存放區位置中的「**受信任的人**」存放區執行驗證。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="6e3f4-125">預設值為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="6e3f4-126">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="6e3f4-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="6e3f4-127">值</span><span class="sxs-lookup"><span data-stu-id="6e3f4-127">Value</span></span>|<span data-ttu-id="6e3f4-128">描述</span><span class="sxs-lookup"><span data-stu-id="6e3f4-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e3f4-129">String</span><span class="sxs-lookup"><span data-stu-id="6e3f4-129">String</span></span>|<span data-ttu-id="6e3f4-130">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-130">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="6e3f4-131">至少需要命名空間和型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-131">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="6e3f4-132">選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-132">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="6e3f4-133">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="6e3f4-133">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="6e3f4-134">值</span><span class="sxs-lookup"><span data-stu-id="6e3f4-134">Value</span></span>|<span data-ttu-id="6e3f4-135">描述</span><span class="sxs-lookup"><span data-stu-id="6e3f4-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e3f4-136">列舉型別</span><span class="sxs-lookup"><span data-stu-id="6e3f4-136">Enumeration</span></span>|<span data-ttu-id="6e3f4-137">下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-137">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="6e3f4-138">預設值為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-138">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="6e3f4-139">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-139">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="6e3f4-140">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="6e3f4-140">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="6e3f4-141">值</span><span class="sxs-lookup"><span data-stu-id="6e3f4-141">Value</span></span>|<span data-ttu-id="6e3f4-142">描述</span><span class="sxs-lookup"><span data-stu-id="6e3f4-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e3f4-143">列舉型別</span><span class="sxs-lookup"><span data-stu-id="6e3f4-143">Enumeration</span></span>|<span data-ttu-id="6e3f4-144">下列其中一個值：`NoCheck`、`Online`、`Offline`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-144">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="6e3f4-145">預設值為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-145">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="6e3f4-146">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="6e3f4-147">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="6e3f4-147">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="6e3f4-148">值</span><span class="sxs-lookup"><span data-stu-id="6e3f4-148">Value</span></span>|<span data-ttu-id="6e3f4-149">描述</span><span class="sxs-lookup"><span data-stu-id="6e3f4-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e3f4-150">列舉型別</span><span class="sxs-lookup"><span data-stu-id="6e3f4-150">Enumeration</span></span>|<span data-ttu-id="6e3f4-151">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-151">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6e3f4-152">預設值為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-152">The default is `CurrentUser`.</span></span> <span data-ttu-id="6e3f4-153">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-153">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="6e3f4-154">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-154">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e3f4-155">子元素</span><span class="sxs-lookup"><span data-stu-id="6e3f4-155">Child Elements</span></span>  
 <span data-ttu-id="6e3f4-156">無。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e3f4-157">父項目</span><span class="sxs-lookup"><span data-stu-id="6e3f4-157">Parent Elements</span></span>  
  
|<span data-ttu-id="6e3f4-158">元素</span><span class="sxs-lookup"><span data-stu-id="6e3f4-158">Element</span></span>|<span data-ttu-id="6e3f4-159">描述</span><span class="sxs-lookup"><span data-stu-id="6e3f4-159">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="6e3f4-160">指定向對等服務驗證用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-160">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e3f4-161">備註</span><span class="sxs-lookup"><span data-stu-id="6e3f4-161">Remarks</span></span>  
 <span data-ttu-id="6e3f4-162">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-162">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="6e3f4-163">這個項目會指定驗證程式，當網狀結構中進行鄰居對鄰居驗證時，就會叫用此驗證程式。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-163">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="6e3f4-164">當新對等嘗試建立鄰居連線時，它會將自己的認證傳遞至對應的對等。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-164">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="6e3f4-165">會叫用回應程式的驗證器來驗證遠端方的認證。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-165">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="6e3f4-166">每次在網狀結構中建立對等連線時，對等的兩方會互相驗證，亦即會叫用兩端的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-166">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e3f4-167">範例</span><span class="sxs-lookup"><span data-stu-id="6e3f4-167">Example</span></span>  
 <span data-ttu-id="6e3f4-168">下列程式碼會將憑證驗證模式設定為 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="6e3f4-168">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e3f4-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e3f4-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="6e3f4-170">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="6e3f4-170">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6e3f4-171">對等網路</span><span class="sxs-lookup"><span data-stu-id="6e3f4-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="6e3f4-172">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6e3f4-172">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="6e3f4-173">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6e3f4-173">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="6e3f4-174">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="6e3f4-174">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
