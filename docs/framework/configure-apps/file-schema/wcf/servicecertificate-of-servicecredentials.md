---
title: <serviceCertificate> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 936661595813d7b8f3e894efb7bf6cf3aab7e89e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167092"
---
# <a name="servicecertificate-of-servicecredentials"></a><span data-ttu-id="5f0f8-102">\<serviceCertificate> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="5f0f8-102">\<serviceCertificate> of \<serviceCredentials></span></span>

<span data-ttu-id="5f0f8-103">指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-103">Specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="5f0f8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f0f8-104">Syntax</span></span>  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f0f8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f0f8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5f0f8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f0f8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5f0f8-107">Attributes</span></span>  
  
|<span data-ttu-id="5f0f8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5f0f8-108">Attribute</span></span>|<span data-ttu-id="5f0f8-109">描述</span><span class="sxs-lookup"><span data-stu-id="5f0f8-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="5f0f8-110">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="5f0f8-111">屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="5f0f8-112">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="5f0f8-113">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="5f0f8-114">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="5f0f8-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5f0f8-115">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="5f0f8-116">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="5f0f8-117">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="5f0f8-118">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="5f0f8-119">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="5f0f8-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5f0f8-120">-AddressBook：其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="5f0f8-121">-AuthRoot：協力廠商憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="5f0f8-122">-CertificatAuthority：中繼憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-122">-   CertificatAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="5f0f8-123">-不允許：撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="5f0f8-124">-My：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="5f0f8-125">-Root：信任根憑證授權單位的憑證存放區， (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="5f0f8-126">-TrustedPeople：直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="5f0f8-127">-TrustedPublisher：直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="5f0f8-128">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-128">The default is My.</span></span>|  
|`x509FindType`|<span data-ttu-id="5f0f8-129">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="5f0f8-130">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="5f0f8-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5f0f8-131">-FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="5f0f8-131">-   FindByThumbprint</span></span><br /><span data-ttu-id="5f0f8-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="5f0f8-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="5f0f8-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="5f0f8-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="5f0f8-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="5f0f8-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="5f0f8-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="5f0f8-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="5f0f8-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="5f0f8-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="5f0f8-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="5f0f8-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="5f0f8-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="5f0f8-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="5f0f8-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="5f0f8-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="5f0f8-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="5f0f8-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="5f0f8-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="5f0f8-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="5f0f8-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="5f0f8-142">-   FindByExtension</span></span><br /><span data-ttu-id="5f0f8-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="5f0f8-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="5f0f8-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="5f0f8-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="5f0f8-145">`findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="5f0f8-146">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f0f8-147">子元素</span><span class="sxs-lookup"><span data-stu-id="5f0f8-147">Child Elements</span></span>  

 <span data-ttu-id="5f0f8-148">無</span><span class="sxs-lookup"><span data-stu-id="5f0f8-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f0f8-149">父項目</span><span class="sxs-lookup"><span data-stu-id="5f0f8-149">Parent Elements</span></span>  
  
|<span data-ttu-id="5f0f8-150">項目</span><span class="sxs-lookup"><span data-stu-id="5f0f8-150">Element</span></span>|<span data-ttu-id="5f0f8-151">描述</span><span class="sxs-lookup"><span data-stu-id="5f0f8-151">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="5f0f8-152">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-152">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f0f8-153">備註</span><span class="sxs-lookup"><span data-stu-id="5f0f8-153">Remarks</span></span>  

 <span data-ttu-id="5f0f8-154">使用此項目指定 X.509 憑證，而此憑證將用以驗證使用訊息安全性模式的用戶端服務。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-154">Use this element to specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="5f0f8-155">如果您使用的是會定期更新的憑證，則其指紋將會變更。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-155">If you are using a certificate that will be periodically renewed, then its thumbprint will change.</span></span> <span data-ttu-id="5f0f8-156">在這種情況下，請使用主體名稱當成 `x509FindType`，因為憑證可以使用相同的主體名稱重新發出。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-156">In that case, use the subject name as the `x509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 <span data-ttu-id="5f0f8-157">如需使用元素的詳細資訊，請參閱 [如何：指定用戶端認證值](../../../wcf/how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="5f0f8-157">For more information about using the element, see [How to: Specify Client Credential Values](../../../wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0f8-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f0f8-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [<span data-ttu-id="5f0f8-159">作法：指定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="5f0f8-159">How to: Specify Client Credential Values</span></span>](../../../wcf/how-to-specify-client-credential-values.md)
- [<span data-ttu-id="5f0f8-160">安全性行為</span><span class="sxs-lookup"><span data-stu-id="5f0f8-160">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
