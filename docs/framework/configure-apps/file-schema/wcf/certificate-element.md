---
title: <certificate> 項目
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400559"
---
# <a name="certificate-element"></a><span data-ttu-id="3bfb3-102">\<憑證 > 元素</span><span class="sxs-lookup"><span data-stu-id="3bfb3-102">\<certificate> Element</span></span>
<span data-ttu-id="3bfb3-103">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
<span data-ttu-id="3bfb3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3bfb3-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3bfb3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="3bfb3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="3bfb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="3bfb3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="3bfb3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<對等 >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="3bfb3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<憑證 >**</span><span class="sxs-lookup"><span data-stu-id="3bfb3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bfb3-112">語法</span><span class="sxs-lookup"><span data-stu-id="3bfb3-112">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bfb3-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3bfb3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3bfb3-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bfb3-115">屬性</span><span class="sxs-lookup"><span data-stu-id="3bfb3-115">Attributes</span></span>  
  
|<span data-ttu-id="3bfb3-116">屬性</span><span class="sxs-lookup"><span data-stu-id="3bfb3-116">Attribute</span></span>|<span data-ttu-id="3bfb3-117">描述</span><span class="sxs-lookup"><span data-stu-id="3bfb3-117">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="3bfb3-118">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-118">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="3bfb3-119">屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-119">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="3bfb3-120">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-120">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="3bfb3-121">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-121">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="3bfb3-122">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="3bfb3-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3bfb3-123">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-123">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="3bfb3-124">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-124">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="3bfb3-125">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-125">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="3bfb3-126">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-126">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="3bfb3-127">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="3bfb3-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3bfb3-128">通訊錄其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-128">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="3bfb3-129">AuthRoot協力廠商憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-129">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="3bfb3-130">CertificateAuthority中繼憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-130">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="3bfb3-131">禁止已撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-131">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="3bfb3-132">'個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-132">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="3bfb3-133">路徑信任的根憑證授權單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-133">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="3bfb3-134">TrustedPeople直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-134">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="3bfb3-135">TrustedPublisher直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-135">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="3bfb3-136">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-136">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="3bfb3-137">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-137">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="3bfb3-138">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="3bfb3-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3bfb3-139">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="3bfb3-139">-   FindByThumbPrint</span></span><br /><span data-ttu-id="3bfb3-140">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="3bfb3-140">-   FindBySubjectName</span></span><br /><span data-ttu-id="3bfb3-141">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3bfb3-141">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="3bfb3-142">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="3bfb3-142">-   FindByIssuerName</span></span><br /><span data-ttu-id="3bfb3-143">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3bfb3-143">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="3bfb3-144">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="3bfb3-144">-   FindBySerialNumber</span></span><br /><span data-ttu-id="3bfb3-145">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="3bfb3-145">-   FindByTimeValid</span></span><br /><span data-ttu-id="3bfb3-146">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="3bfb3-146">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="3bfb3-147">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="3bfb3-147">-   FindByTemplateName</span></span><br /><span data-ttu-id="3bfb3-148">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="3bfb3-148">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="3bfb3-149">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3bfb3-149">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="3bfb3-150">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="3bfb3-150">-   FindByExtension</span></span><br /><span data-ttu-id="3bfb3-151">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="3bfb3-151">-   FindByKeyUsage</span></span><br /><span data-ttu-id="3bfb3-152">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="3bfb3-152">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="3bfb3-153">`findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-153">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="3bfb3-154">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-154">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bfb3-155">子元素</span><span class="sxs-lookup"><span data-stu-id="3bfb3-155">Child Elements</span></span>  
 <span data-ttu-id="3bfb3-156">無。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bfb3-157">父項目</span><span class="sxs-lookup"><span data-stu-id="3bfb3-157">Parent Elements</span></span>  
  
|<span data-ttu-id="3bfb3-158">項目</span><span class="sxs-lookup"><span data-stu-id="3bfb3-158">Element</span></span>|<span data-ttu-id="3bfb3-159">說明</span><span class="sxs-lookup"><span data-stu-id="3bfb3-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bfb3-160">\<peer></span><span class="sxs-lookup"><span data-stu-id="3bfb3-160">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="3bfb3-161">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-161">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bfb3-162">備註</span><span class="sxs-lookup"><span data-stu-id="3bfb3-162">Remarks</span></span>  
 <span data-ttu-id="3bfb3-163">這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 X509Certificate2 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-163">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="3bfb3-164">如需對等程式設計的詳細資訊，請參閱[對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-164">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bfb3-165">範例</span><span class="sxs-lookup"><span data-stu-id="3bfb3-165">Example</span></span>  
 <span data-ttu-id="3bfb3-166">下列程式碼說明如何尋找對等案例中使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="3bfb3-166">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bfb3-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bfb3-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="3bfb3-168">使用憑證</span><span class="sxs-lookup"><span data-stu-id="3bfb3-168">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3bfb3-169">對等網路</span><span class="sxs-lookup"><span data-stu-id="3bfb3-169">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3bfb3-170">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3bfb3-170">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3bfb3-171">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3bfb3-171">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3bfb3-172">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="3bfb3-172">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
