---
title: <certificate> 項目
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: f0cec2ad0e7747ddbc0ef566b4e8cbc7f8795b02
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675383"
---
# <a name="certificate-element"></a><span data-ttu-id="c72c4-102">\<憑證 > 項目</span><span class="sxs-lookup"><span data-stu-id="c72c4-102">\<certificate> Element</span></span>
<span data-ttu-id="c72c4-103">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="c72c4-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="c72c4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c72c4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c72c4-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c72c4-105">\<behaviors></span></span>  
<span data-ttu-id="c72c4-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c72c4-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c72c4-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c72c4-107">\<behavior></span></span>  
<span data-ttu-id="c72c4-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="c72c4-108">\<clientCredentials></span></span>  
<span data-ttu-id="c72c4-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="c72c4-109">\<peer></span></span>  
<span data-ttu-id="c72c4-110">\<certificate></span><span class="sxs-lookup"><span data-stu-id="c72c4-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c72c4-111">語法</span><span class="sxs-lookup"><span data-stu-id="c72c4-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c72c4-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c72c4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c72c4-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c72c4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c72c4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c72c4-114">Attributes</span></span>  
  
|<span data-ttu-id="c72c4-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c72c4-115">Attribute</span></span>|<span data-ttu-id="c72c4-116">描述</span><span class="sxs-lookup"><span data-stu-id="c72c4-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="c72c4-117">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="c72c4-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="c72c4-118">屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="c72c4-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="c72c4-119">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="c72c4-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="c72c4-120">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。</span><span class="sxs-lookup"><span data-stu-id="c72c4-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="c72c4-121">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="c72c4-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c72c4-122">-LocalMachine: 指派憑證存放區到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c72c4-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="c72c4-123">-CurrentUser: 指派憑證存放區目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="c72c4-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="c72c4-124">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="c72c4-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="c72c4-125">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="c72c4-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="c72c4-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="c72c4-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c72c4-127">-AddressBook:其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="c72c4-128">-   AuthRoot:第三方憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="c72c4-129">-CertificateAuthority:中繼憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="c72c4-130">-不允許：已撤銷之憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="c72c4-131">-我：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="c72c4-132">根目錄：受信任的根憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="c72c4-133">-TrustedPeople:直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="c72c4-134">-TrustedPublisher:直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c72c4-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="c72c4-135">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="c72c4-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="c72c4-136">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="c72c4-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="c72c4-137">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="c72c4-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c72c4-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="c72c4-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="c72c4-139">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="c72c4-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="c72c4-140">-   FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c72c4-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="c72c4-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="c72c4-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="c72c4-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c72c4-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="c72c4-143">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="c72c4-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="c72c4-144">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="c72c4-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="c72c4-145">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="c72c4-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="c72c4-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="c72c4-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="c72c4-147">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="c72c4-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="c72c4-148">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="c72c4-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="c72c4-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="c72c4-149">-   FindByExtension</span></span><br /><span data-ttu-id="c72c4-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="c72c4-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="c72c4-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="c72c4-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="c72c4-152">`findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="c72c4-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="c72c4-153">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="c72c4-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c72c4-154">子元素</span><span class="sxs-lookup"><span data-stu-id="c72c4-154">Child Elements</span></span>  
 <span data-ttu-id="c72c4-155">無。</span><span class="sxs-lookup"><span data-stu-id="c72c4-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c72c4-156">父項目</span><span class="sxs-lookup"><span data-stu-id="c72c4-156">Parent Elements</span></span>  
  
|<span data-ttu-id="c72c4-157">項目</span><span class="sxs-lookup"><span data-stu-id="c72c4-157">Element</span></span>|<span data-ttu-id="c72c4-158">描述</span><span class="sxs-lookup"><span data-stu-id="c72c4-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c72c4-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="c72c4-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="c72c4-160">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="c72c4-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c72c4-161">備註</span><span class="sxs-lookup"><span data-stu-id="c72c4-161">Remarks</span></span>  
 <span data-ttu-id="c72c4-162">這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 X509Certificate2 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c72c4-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="c72c4-163">如需端對端程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="c72c4-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c72c4-164">範例</span><span class="sxs-lookup"><span data-stu-id="c72c4-164">Example</span></span>  
 <span data-ttu-id="c72c4-165">下列程式碼說明如何尋找對等案例中使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="c72c4-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="c72c4-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c72c4-166">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="c72c4-167">使用憑證</span><span class="sxs-lookup"><span data-stu-id="c72c4-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c72c4-168">對等網路</span><span class="sxs-lookup"><span data-stu-id="c72c4-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="c72c4-169">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c72c4-169">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="c72c4-170">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c72c4-170">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="c72c4-171">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="c72c4-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
