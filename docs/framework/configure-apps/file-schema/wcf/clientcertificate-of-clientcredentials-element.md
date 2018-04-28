---
title: '&lt;clientCredentials&gt; 的 &lt;clientCertificate&gt; 項目'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c5616aab5cb54e94a62370ad682eaa55eceb8ef
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="ltclientcertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="18a8e-102">&lt;clientCredentials&gt; 的 &lt;clientCertificate&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="18a8e-102">&lt;clientCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="18a8e-103">定義用於向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="18a8e-103">Defines an X.509 certificate used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="18a8e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18a8e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18a8e-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="18a8e-105">\<behaviors></span></span>  
<span data-ttu-id="18a8e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="18a8e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="18a8e-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="18a8e-107">\<behavior></span></span>  
<span data-ttu-id="18a8e-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="18a8e-108">\<clientCredentials></span></span>  
<span data-ttu-id="18a8e-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="18a8e-109">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18a8e-110">語法</span><span class="sxs-lookup"><span data-stu-id="18a8e-110">Syntax</span></span>  
  
```xml  
<clientCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18a8e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18a8e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="18a8e-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="18a8e-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18a8e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="18a8e-113">Attributes</span></span>  
  
|<span data-ttu-id="18a8e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="18a8e-114">Attribute</span></span>|<span data-ttu-id="18a8e-115">描述</span><span class="sxs-lookup"><span data-stu-id="18a8e-115">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="18a8e-116">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="18a8e-116">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="18a8e-117">這個屬性所包含的型別必須滿足 `X509FindType` 屬性值的需求。</span><span class="sxs-lookup"><span data-stu-id="18a8e-117">The type contained in the attribute must satisfy the requirements of the `X509FindType` attribute value.</span></span> <span data-ttu-id="18a8e-118">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="18a8e-118">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="18a8e-119">指定 X.509 憑證的位置，用戶端會使用該憑證來進行對服務的自我驗證。</span><span class="sxs-lookup"><span data-stu-id="18a8e-119">Specifies the location of the X.509 certificate that the client uses to authenticate itself to the service.</span></span> <span data-ttu-id="18a8e-120">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="18a8e-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="18a8e-121">-LocalMachine: 指派憑證存放區至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="18a8e-121">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="18a8e-122">-CurrentUser: 指派憑證存放區目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="18a8e-122">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="18a8e-123">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="18a8e-123">The default is LocalMachine.</span></span> <span data-ttu-id="18a8e-124">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="18a8e-124">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|`storeName`|<span data-ttu-id="18a8e-125">指定要搜尋之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="18a8e-125">Specifies the name of the X.509 certificate store to search.</span></span> <span data-ttu-id="18a8e-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="18a8e-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="18a8e-127">-AddressBook： 其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="18a8e-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="18a8e-128">-AuthRoot： 協力廠商憑證授權單位 (Ca) 的存放區的憑證。</span><span class="sxs-lookup"><span data-stu-id="18a8e-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="18a8e-129">-CertificateAuthority： 中繼憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="18a8e-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="18a8e-130">-不允許： 憑證已撤銷之憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="18a8e-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="18a8e-131">-My： 憑證個人憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="18a8e-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="18a8e-132">-Root： 信任的根憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="18a8e-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="18a8e-133">-TrustedPeople： 直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="18a8e-133">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="18a8e-134">-TrustedPublisher： 直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="18a8e-134">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="18a8e-135">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="18a8e-135">The default is My.</span></span> <span data-ttu-id="18a8e-136">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreName>。</span><span class="sxs-lookup"><span data-stu-id="18a8e-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="18a8e-137">X509FindType</span><span class="sxs-lookup"><span data-stu-id="18a8e-137">X509FindType</span></span>|<span data-ttu-id="18a8e-138">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="18a8e-138">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="18a8e-139">`findValue` 屬性中所包含的型別必須滿足此屬性的需求。</span><span class="sxs-lookup"><span data-stu-id="18a8e-139">The type contained in the `findValue` attribute must satisfy the requirements of this attribute.</span></span> <span data-ttu-id="18a8e-140">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="18a8e-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="18a8e-141">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="18a8e-141">-   FindByThumbPrint</span></span><br /><span data-ttu-id="18a8e-142">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="18a8e-142">-   FindBySubjectName</span></span><br /><span data-ttu-id="18a8e-143">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="18a8e-143">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="18a8e-144">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="18a8e-144">-   FindByIssuerName</span></span><br /><span data-ttu-id="18a8e-145">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="18a8e-145">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="18a8e-146">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="18a8e-146">-   FindBySerialNumber</span></span><br /><span data-ttu-id="18a8e-147">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="18a8e-147">-   FindByTimeValid</span></span><br /><span data-ttu-id="18a8e-148">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="18a8e-148">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="18a8e-149">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="18a8e-149">-   FindByTemplateName</span></span><br /><span data-ttu-id="18a8e-150">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="18a8e-150">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="18a8e-151">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="18a8e-151">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="18a8e-152">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="18a8e-152">-   FindByExtension</span></span><br /><span data-ttu-id="18a8e-153">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="18a8e-153">-   FindByKeyUsage</span></span><br /><span data-ttu-id="18a8e-154">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="18a8e-154">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="18a8e-155">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="18a8e-155">The default value is FindBySubjectDistinguishedName.</span></span> <span data-ttu-id="18a8e-156">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。</span><span class="sxs-lookup"><span data-stu-id="18a8e-156">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18a8e-157">子項目</span><span class="sxs-lookup"><span data-stu-id="18a8e-157">Child Elements</span></span>  
 <span data-ttu-id="18a8e-158">無。</span><span class="sxs-lookup"><span data-stu-id="18a8e-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18a8e-159">父項目</span><span class="sxs-lookup"><span data-stu-id="18a8e-159">Parent Elements</span></span>  
  
|<span data-ttu-id="18a8e-160">項目</span><span class="sxs-lookup"><span data-stu-id="18a8e-160">Element</span></span>|<span data-ttu-id="18a8e-161">描述</span><span class="sxs-lookup"><span data-stu-id="18a8e-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18a8e-162">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="18a8e-162">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="18a8e-163">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="18a8e-163">Specifies the credentials used to authenticate the client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18a8e-164">備註</span><span class="sxs-lookup"><span data-stu-id="18a8e-164">Remarks</span></span>  
 <span data-ttu-id="18a8e-165">這個組態項目會指定憑證，此憑證會用來驗證具有這個項目的用戶端。</span><span class="sxs-lookup"><span data-stu-id="18a8e-165">This configuration element specifies the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="18a8e-166">如需詳細資訊，請參閱[How to： 指定用戶端認證值](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="18a8e-166">For more information, see [How to: Specify Client Credential Values](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a8e-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18a8e-167">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [<span data-ttu-id="18a8e-168">安全性行為</span><span class="sxs-lookup"><span data-stu-id="18a8e-168">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="18a8e-169">如何：指定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="18a8e-169">How to: Specify Client Credential Values</span></span>](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="18a8e-170">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="18a8e-170">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="18a8e-171">使用憑證</span><span class="sxs-lookup"><span data-stu-id="18a8e-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="18a8e-172">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="18a8e-172">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
