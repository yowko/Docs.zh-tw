---
title: <certificate> 項目
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 8cc0404a5896dd23cffce6f1f77b91a2f01f23d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151086"
---
# <a name="certificate-element"></a><span data-ttu-id="e4f10-102">\<certificate> 項目</span><span class="sxs-lookup"><span data-stu-id="e4f10-102">\<certificate> Element</span></span>

<span data-ttu-id="e4f10-103">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="e4f10-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="e4f10-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4f10-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4f10-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4f10-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e4f10-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4f10-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4f10-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e4f10-107">Attributes</span></span>  
  
|<span data-ttu-id="e4f10-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e4f10-108">Attribute</span></span>|<span data-ttu-id="e4f10-109">描述</span><span class="sxs-lookup"><span data-stu-id="e4f10-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="e4f10-110">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="e4f10-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="e4f10-111">屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="e4f10-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="e4f10-112">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="e4f10-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="e4f10-113">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。</span><span class="sxs-lookup"><span data-stu-id="e4f10-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="e4f10-114">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="e4f10-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e4f10-115">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e4f10-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="e4f10-116">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e4f10-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="e4f10-117">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="e4f10-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="e4f10-118">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4f10-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="e4f10-119">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="e4f10-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e4f10-120">-AddressBook：其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e4f10-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="e4f10-121">-AuthRoot：協力廠商憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="e4f10-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="e4f10-122">-CertificateAuthority：中繼憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="e4f10-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="e4f10-123">-不允許：撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e4f10-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="e4f10-124">-My：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e4f10-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="e4f10-125">-Root：信任根憑證授權單位的憑證存放區， (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="e4f10-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="e4f10-126">-TrustedPeople：直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e4f10-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="e4f10-127">-TrustedPublisher：直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e4f10-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="e4f10-128">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="e4f10-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="e4f10-129">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="e4f10-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="e4f10-130">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="e4f10-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e4f10-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="e4f10-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="e4f10-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="e4f10-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="e4f10-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e4f10-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="e4f10-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="e4f10-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="e4f10-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e4f10-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="e4f10-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="e4f10-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="e4f10-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="e4f10-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="e4f10-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="e4f10-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="e4f10-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="e4f10-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="e4f10-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="e4f10-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="e4f10-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="e4f10-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="e4f10-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="e4f10-142">-   FindByExtension</span></span><br /><span data-ttu-id="e4f10-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="e4f10-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="e4f10-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="e4f10-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="e4f10-145">`findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="e4f10-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="e4f10-146">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="e4f10-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4f10-147">子元素</span><span class="sxs-lookup"><span data-stu-id="e4f10-147">Child Elements</span></span>  

 <span data-ttu-id="e4f10-148">無。</span><span class="sxs-lookup"><span data-stu-id="e4f10-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4f10-149">父項目</span><span class="sxs-lookup"><span data-stu-id="e4f10-149">Parent Elements</span></span>  
  
|<span data-ttu-id="e4f10-150">項目</span><span class="sxs-lookup"><span data-stu-id="e4f10-150">Element</span></span>|<span data-ttu-id="e4f10-151">描述</span><span class="sxs-lookup"><span data-stu-id="e4f10-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="e4f10-152">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="e4f10-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f10-153">備註</span><span class="sxs-lookup"><span data-stu-id="e4f10-153">Remarks</span></span>  

 <span data-ttu-id="e4f10-154">這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 X509Certificate2 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e4f10-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="e4f10-155">如需點對點程式設計的詳細資訊，請參閱 [對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="e4f10-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4f10-156">範例</span><span class="sxs-lookup"><span data-stu-id="e4f10-156">Example</span></span>  

 <span data-ttu-id="e4f10-157">下列程式碼說明如何尋找對等案例中使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="e4f10-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4f10-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4f10-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="e4f10-159">使用憑證</span><span class="sxs-lookup"><span data-stu-id="e4f10-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e4f10-160">對等網路</span><span class="sxs-lookup"><span data-stu-id="e4f10-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="e4f10-161">[對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e4f10-161">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="e4f10-162">[對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e4f10-162">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="e4f10-163">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="e4f10-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
