---
title: "&lt;serviceCredentials&gt; 的 &lt;serviceCertificate&gt; "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ee21218ad9dd9103b90cd7be00a172ad321ba266
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="2216b-102">&lt;serviceCredentials&gt; 的 &lt;serviceCertificate&gt; </span><span class="sxs-lookup"><span data-stu-id="2216b-102">&lt;serviceCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="2216b-103">指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。</span><span class="sxs-lookup"><span data-stu-id="2216b-103">Specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span>  
  
 <span data-ttu-id="2216b-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2216b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2216b-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="2216b-105">\<behaviors></span></span>  
<span data-ttu-id="2216b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2216b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2216b-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="2216b-107">\<behavior></span></span>  
<span data-ttu-id="2216b-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="2216b-108">\<serviceCredentials></span></span>  
<span data-ttu-id="2216b-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2216b-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2216b-110">語法</span><span class="sxs-lookup"><span data-stu-id="2216b-110">Syntax</span></span>  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2216b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2216b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2216b-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2216b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2216b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2216b-113">Attributes</span></span>  
  
|<span data-ttu-id="2216b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2216b-114">Attribute</span></span>|<span data-ttu-id="2216b-115">描述</span><span class="sxs-lookup"><span data-stu-id="2216b-115">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="2216b-116">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="2216b-116">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2216b-117">屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="2216b-117">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="2216b-118">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="2216b-118">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="2216b-119">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="2216b-119">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="2216b-120">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="2216b-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2216b-121">-LocalMachine: 指派憑證存放區至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="2216b-121">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="2216b-122">-CurrentUser: 指派憑證存放區目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="2216b-122">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="2216b-123">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="2216b-123">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="2216b-124">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="2216b-124">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="2216b-125">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="2216b-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2216b-126">-AddressBook： 其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2216b-126">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="2216b-127">-AuthRoot： 協力廠商憑證授權單位 (Ca) 的存放區的憑證。</span><span class="sxs-lookup"><span data-stu-id="2216b-127">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="2216b-128">-CertificatAuthority： 中繼憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2216b-128">-   CertificatAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="2216b-129">-不允許： 憑證已撤銷之憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2216b-129">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="2216b-130">-My： 憑證個人憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2216b-130">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="2216b-131">-Root： 信任的根憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2216b-131">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="2216b-132">-TrustedPeople： 直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2216b-132">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="2216b-133">-TrustedPublisher： 直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="2216b-133">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="2216b-134">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="2216b-134">The default is My.</span></span>|  
|`x509FindType`|<span data-ttu-id="2216b-135">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="2216b-135">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="2216b-136">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="2216b-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2216b-137">-FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="2216b-137">-   FindByThumbprint</span></span><br /><span data-ttu-id="2216b-138">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="2216b-138">-   FindBySubjectName</span></span><br /><span data-ttu-id="2216b-139">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2216b-139">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="2216b-140">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="2216b-140">-   FindByIssuerName</span></span><br /><span data-ttu-id="2216b-141">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2216b-141">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="2216b-142">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="2216b-142">-   FindBySerialNumber</span></span><br /><span data-ttu-id="2216b-143">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="2216b-143">-   FindByTimeValid</span></span><br /><span data-ttu-id="2216b-144">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="2216b-144">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="2216b-145">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="2216b-145">-   FindByTemplateName</span></span><br /><span data-ttu-id="2216b-146">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="2216b-146">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="2216b-147">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="2216b-147">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="2216b-148">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="2216b-148">-   FindByExtension</span></span><br /><span data-ttu-id="2216b-149">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="2216b-149">-   FindByKeyUsage</span></span><br /><span data-ttu-id="2216b-150">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="2216b-150">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="2216b-151">`findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="2216b-151">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="2216b-152">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="2216b-152">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2216b-153">子元素</span><span class="sxs-lookup"><span data-stu-id="2216b-153">Child Elements</span></span>  
 <span data-ttu-id="2216b-154">無</span><span class="sxs-lookup"><span data-stu-id="2216b-154">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2216b-155">父項目</span><span class="sxs-lookup"><span data-stu-id="2216b-155">Parent Elements</span></span>  
  
|<span data-ttu-id="2216b-156">項目</span><span class="sxs-lookup"><span data-stu-id="2216b-156">Element</span></span>|<span data-ttu-id="2216b-157">說明</span><span class="sxs-lookup"><span data-stu-id="2216b-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2216b-158">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="2216b-158">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="2216b-159">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="2216b-159">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2216b-160">備註</span><span class="sxs-lookup"><span data-stu-id="2216b-160">Remarks</span></span>  
 <span data-ttu-id="2216b-161">使用此項目指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。</span><span class="sxs-lookup"><span data-stu-id="2216b-161">Use this element to specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="2216b-162">如果您使用的是會定期更新的憑證，則其指紋將會變更。</span><span class="sxs-lookup"><span data-stu-id="2216b-162">If you are using a certificate that will be periodically renewed, then its thumbprint will change.</span></span> <span data-ttu-id="2216b-163">在這種情況下，請使用主體名稱當成 `x509FindType`，因為憑證可以使用相同的主體名稱重新發出。</span><span class="sxs-lookup"><span data-stu-id="2216b-163">In that case, use the subject name as the `x509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="2216b-164">使用項目，請參閱[How to： 指定用戶端認證值](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="2216b-164"> using the element, see [How to: Specify Client Credential Values](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2216b-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2216b-165">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [<span data-ttu-id="2216b-166">如何：指定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="2216b-166">How to: Specify Client Credential Values</span></span>](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="2216b-167">安全性行為</span><span class="sxs-lookup"><span data-stu-id="2216b-167">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
