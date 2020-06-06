---
title: <certificate> 的 <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 2044dc6fb4ae688a0a3c7e29b3b7696df0d0d218
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398205"
---
# <a name="certificate-of-peer"></a><span data-ttu-id="2b746-102">\<certificate> 的 \<peer></span><span class="sxs-lookup"><span data-stu-id="2b746-102">\<certificate> of \<peer></span></span>
<span data-ttu-id="2b746-103">指定對等所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="2b746-103">Specifies a certificate used by a peer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="2b746-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b746-104">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b746-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b746-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2b746-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2b746-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b746-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2b746-107">Attributes</span></span>  
  
|<span data-ttu-id="2b746-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2b746-108">Attribute</span></span>|<span data-ttu-id="2b746-109">描述</span><span class="sxs-lookup"><span data-stu-id="2b746-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="2b746-110">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="2b746-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2b746-111">屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="2b746-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="2b746-112">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="2b746-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="2b746-113">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。</span><span class="sxs-lookup"><span data-stu-id="2b746-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="2b746-114">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="2b746-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2b746-115">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="2b746-116">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="2b746-117">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="2b746-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="2b746-118">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b746-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="2b746-119">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="2b746-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2b746-120">-通訊錄：其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="2b746-121">-AuthRoot：協力廠商憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-121">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="2b746-122">-CertificateAuthority：中繼憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-122">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="2b746-123">-不允許：已撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="2b746-124">-My：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="2b746-125">-Root：信任的根憑證授權單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-125">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="2b746-126">-TrustedPeople：直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="2b746-127">-TrustedPublisher：直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2b746-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="2b746-128">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="2b746-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="2b746-129">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="2b746-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="2b746-130">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="2b746-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2b746-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="2b746-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="2b746-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="2b746-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="2b746-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2b746-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="2b746-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="2b746-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="2b746-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2b746-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="2b746-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="2b746-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="2b746-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="2b746-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="2b746-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="2b746-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="2b746-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="2b746-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="2b746-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="2b746-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="2b746-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="2b746-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="2b746-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="2b746-142">-   FindByExtension</span></span><br /><span data-ttu-id="2b746-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="2b746-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="2b746-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="2b746-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="2b746-145">`findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="2b746-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="2b746-146">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="2b746-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b746-147">子元素</span><span class="sxs-lookup"><span data-stu-id="2b746-147">Child Elements</span></span>  
 <span data-ttu-id="2b746-148">無。</span><span class="sxs-lookup"><span data-stu-id="2b746-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b746-149">父項目</span><span class="sxs-lookup"><span data-stu-id="2b746-149">Parent Elements</span></span>  
  
|<span data-ttu-id="2b746-150">元素</span><span class="sxs-lookup"><span data-stu-id="2b746-150">Element</span></span>|<span data-ttu-id="2b746-151">描述</span><span class="sxs-lookup"><span data-stu-id="2b746-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="2b746-152">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="2b746-152">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b746-153">備註</span><span class="sxs-lookup"><span data-stu-id="2b746-153">Remarks</span></span>  
 <span data-ttu-id="2b746-154">這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 `X509Certificate2` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2b746-154">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="2b746-155">如需對等程式設計的詳細資訊，請參閱[對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="2b746-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b746-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b746-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="2b746-157">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="2b746-157">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2b746-158">對等網路</span><span class="sxs-lookup"><span data-stu-id="2b746-158">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2b746-159">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2b746-159">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2b746-160">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2b746-160">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2b746-161">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="2b746-161">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="2b746-162">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="2b746-162">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
