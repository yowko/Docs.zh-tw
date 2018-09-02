---
title: '&lt;peer&gt; 的 &lt;certificate&gt;'
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 59aaee5549aae5df173174651ee3a520a0ac10fb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423451"
---
# <a name="ltcertificategt-of-ltpeergt"></a><span data-ttu-id="210a7-102">&lt;peer&gt; 的 &lt;certificate&gt;</span><span class="sxs-lookup"><span data-stu-id="210a7-102">&lt;certificate&gt; of &lt;peer&gt;</span></span>
<span data-ttu-id="210a7-103">指定對等所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="210a7-103">Specifies a certificate used by a peer.</span></span>  
  
 <span data-ttu-id="210a7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="210a7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="210a7-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="210a7-105">\<behaviors></span></span>  
<span data-ttu-id="210a7-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="210a7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="210a7-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="210a7-107">\<behavior></span></span>  
<span data-ttu-id="210a7-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="210a7-108">\<serviceCredentials></span></span>  
<span data-ttu-id="210a7-109">\<對等電腦 ></span><span class="sxs-lookup"><span data-stu-id="210a7-109">\<peer></span></span>  
<span data-ttu-id="210a7-110">\<憑證 ></span><span class="sxs-lookup"><span data-stu-id="210a7-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="210a7-111">語法</span><span class="sxs-lookup"><span data-stu-id="210a7-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="210a7-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="210a7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="210a7-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="210a7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="210a7-114">屬性</span><span class="sxs-lookup"><span data-stu-id="210a7-114">Attributes</span></span>  
  
|<span data-ttu-id="210a7-115">屬性</span><span class="sxs-lookup"><span data-stu-id="210a7-115">Attribute</span></span>|<span data-ttu-id="210a7-116">描述</span><span class="sxs-lookup"><span data-stu-id="210a7-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="210a7-117">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="210a7-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="210a7-118">屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="210a7-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="210a7-119">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="210a7-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="210a7-120">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。</span><span class="sxs-lookup"><span data-stu-id="210a7-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="210a7-121">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="210a7-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="210a7-122">-LocalMachine: 指派憑證存放區到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="210a7-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="210a7-123">-CurrentUser: 指派憑證存放區目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="210a7-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="210a7-124">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="210a7-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="210a7-125">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="210a7-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="210a7-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="210a7-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="210a7-127">-AddressBook： 其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="210a7-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="210a7-128">-AuthRoot： 協力廠商憑證授權單位 (Ca) 的存放區的憑證。</span><span class="sxs-lookup"><span data-stu-id="210a7-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="210a7-129">-CertificateAuthority： 中繼憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="210a7-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="210a7-130">-不允許： 憑證已撤銷之憑證的存放區。</span><span class="sxs-lookup"><span data-stu-id="210a7-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="210a7-131">-我： 憑證個人憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="210a7-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="210a7-132">-Root： 信任的根憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="210a7-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="210a7-133">-TrustedPeople： 直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="210a7-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="210a7-134">-TrustedPublisher： 直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="210a7-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="210a7-135">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="210a7-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="210a7-136">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="210a7-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="210a7-137">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="210a7-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="210a7-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="210a7-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="210a7-139">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="210a7-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="210a7-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="210a7-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="210a7-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="210a7-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="210a7-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="210a7-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="210a7-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="210a7-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="210a7-144">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="210a7-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="210a7-145">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="210a7-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="210a7-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="210a7-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="210a7-147">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="210a7-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="210a7-148">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="210a7-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="210a7-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="210a7-149">-   FindByExtension</span></span><br /><span data-ttu-id="210a7-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="210a7-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="210a7-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="210a7-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="210a7-152">`findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。</span><span class="sxs-lookup"><span data-stu-id="210a7-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="210a7-153">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="210a7-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="210a7-154">子元素</span><span class="sxs-lookup"><span data-stu-id="210a7-154">Child Elements</span></span>  
 <span data-ttu-id="210a7-155">無。</span><span class="sxs-lookup"><span data-stu-id="210a7-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="210a7-156">父項目</span><span class="sxs-lookup"><span data-stu-id="210a7-156">Parent Elements</span></span>  
  
|<span data-ttu-id="210a7-157">項目</span><span class="sxs-lookup"><span data-stu-id="210a7-157">Element</span></span>|<span data-ttu-id="210a7-158">描述</span><span class="sxs-lookup"><span data-stu-id="210a7-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="210a7-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="210a7-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="210a7-160">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="210a7-160">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="210a7-161">備註</span><span class="sxs-lookup"><span data-stu-id="210a7-161">Remarks</span></span>  
 <span data-ttu-id="210a7-162">這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 `X509Certificate2` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="210a7-162">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="210a7-163">如需端對端程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="210a7-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="210a7-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="210a7-164">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="210a7-165">使用憑證</span><span class="sxs-lookup"><span data-stu-id="210a7-165">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="210a7-166">對等網路</span><span class="sxs-lookup"><span data-stu-id="210a7-166">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="210a7-167">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="210a7-167">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="210a7-168">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="210a7-168">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="210a7-169">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="210a7-169">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="210a7-170">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="210a7-170">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
