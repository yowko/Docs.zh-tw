---
title: <clientCertificate> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: 74209c43dcafb1e27bb1d7943ee7832eaea0ef57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204940"
---
# <a name="clientcertificate-of-clientcredentials-element"></a><span data-ttu-id="41f50-102">\<clientCertificate> 項目的 \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="41f50-102">\<clientCertificate> of \<clientCredentials> Element</span></span>

<span data-ttu-id="41f50-103">定義用於向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="41f50-103">Defines an X.509 certificate used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="41f50-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="41f50-104">Syntax</span></span>  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41f50-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="41f50-105">Attributes and Elements</span></span>  

 <span data-ttu-id="41f50-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="41f50-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41f50-107">屬性</span><span class="sxs-lookup"><span data-stu-id="41f50-107">Attributes</span></span>  
  
|<span data-ttu-id="41f50-108">屬性</span><span class="sxs-lookup"><span data-stu-id="41f50-108">Attribute</span></span>|<span data-ttu-id="41f50-109">描述</span><span class="sxs-lookup"><span data-stu-id="41f50-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="41f50-110">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="41f50-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="41f50-111">這個屬性所包含的型別必須滿足 `X509FindType` 屬性值的需求。</span><span class="sxs-lookup"><span data-stu-id="41f50-111">The type contained in the attribute must satisfy the requirements of the `X509FindType` attribute value.</span></span> <span data-ttu-id="41f50-112">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="41f50-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="41f50-113">指定 X.509 憑證的位置，用戶端會使用該憑證來進行對服務的自我驗證。</span><span class="sxs-lookup"><span data-stu-id="41f50-113">Specifies the location of the X.509 certificate that the client uses to authenticate itself to the service.</span></span> <span data-ttu-id="41f50-114">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="41f50-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41f50-115">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="41f50-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="41f50-116">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="41f50-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="41f50-117">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="41f50-117">The default is LocalMachine.</span></span> <span data-ttu-id="41f50-118">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="41f50-118">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|`storeName`|<span data-ttu-id="41f50-119">指定要搜尋之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="41f50-119">Specifies the name of the X.509 certificate store to search.</span></span> <span data-ttu-id="41f50-120">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="41f50-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41f50-121">-AddressBook：其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="41f50-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="41f50-122">-AuthRoot：協力廠商憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="41f50-122">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="41f50-123">-CertificateAuthority：中繼憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="41f50-123">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="41f50-124">-不允許：撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="41f50-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="41f50-125">-My：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="41f50-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="41f50-126">-Root：受信任的根憑證授權單位的憑證存放區， (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="41f50-126">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="41f50-127">-TrustedPeople：直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="41f50-127">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="41f50-128">-TrustedPublisher：直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="41f50-128">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="41f50-129">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="41f50-129">The default is My.</span></span> <span data-ttu-id="41f50-130">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreName>。</span><span class="sxs-lookup"><span data-stu-id="41f50-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="41f50-131">X509FindType</span><span class="sxs-lookup"><span data-stu-id="41f50-131">X509FindType</span></span>|<span data-ttu-id="41f50-132">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="41f50-132">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="41f50-133">`findValue` 屬性中所包含的型別必須滿足此屬性的需求。</span><span class="sxs-lookup"><span data-stu-id="41f50-133">The type contained in the `findValue` attribute must satisfy the requirements of this attribute.</span></span> <span data-ttu-id="41f50-134">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="41f50-134">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41f50-135">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="41f50-135">-   FindByThumbPrint</span></span><br /><span data-ttu-id="41f50-136">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="41f50-136">-   FindBySubjectName</span></span><br /><span data-ttu-id="41f50-137">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="41f50-137">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="41f50-138">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="41f50-138">-   FindByIssuerName</span></span><br /><span data-ttu-id="41f50-139">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="41f50-139">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="41f50-140">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="41f50-140">-   FindBySerialNumber</span></span><br /><span data-ttu-id="41f50-141">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="41f50-141">-   FindByTimeValid</span></span><br /><span data-ttu-id="41f50-142">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="41f50-142">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="41f50-143">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="41f50-143">-   FindByTemplateName</span></span><br /><span data-ttu-id="41f50-144">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="41f50-144">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="41f50-145">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="41f50-145">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="41f50-146">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="41f50-146">-   FindByExtension</span></span><br /><span data-ttu-id="41f50-147">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="41f50-147">-   FindByKeyUsage</span></span><br /><span data-ttu-id="41f50-148">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="41f50-148">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="41f50-149">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="41f50-149">The default value is FindBySubjectDistinguishedName.</span></span> <span data-ttu-id="41f50-150">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。</span><span class="sxs-lookup"><span data-stu-id="41f50-150">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41f50-151">子元素</span><span class="sxs-lookup"><span data-stu-id="41f50-151">Child Elements</span></span>  

 <span data-ttu-id="41f50-152">無。</span><span class="sxs-lookup"><span data-stu-id="41f50-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41f50-153">父項目</span><span class="sxs-lookup"><span data-stu-id="41f50-153">Parent Elements</span></span>  
  
|<span data-ttu-id="41f50-154">項目</span><span class="sxs-lookup"><span data-stu-id="41f50-154">Element</span></span>|<span data-ttu-id="41f50-155">描述</span><span class="sxs-lookup"><span data-stu-id="41f50-155">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="41f50-156">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="41f50-156">Specifies the credentials used to authenticate the client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41f50-157">備註</span><span class="sxs-lookup"><span data-stu-id="41f50-157">Remarks</span></span>  

 <span data-ttu-id="41f50-158">這個組態項目會指定憑證，此憑證會用來驗證具有這個項目的用戶端。</span><span class="sxs-lookup"><span data-stu-id="41f50-158">This configuration element specifies the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="41f50-159">如需詳細資訊，請參閱 [如何：指定用戶端認證值](../../../wcf/how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="41f50-159">For more information, see [How to: Specify Client Credential Values](../../../wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f50-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41f50-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="41f50-161">安全性行為</span><span class="sxs-lookup"><span data-stu-id="41f50-161">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="41f50-162">作法：指定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="41f50-162">How to: Specify Client Credential Values</span></span>](../../../wcf/how-to-specify-client-credential-values.md)
- [<span data-ttu-id="41f50-163">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="41f50-163">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="41f50-164">使用憑證</span><span class="sxs-lookup"><span data-stu-id="41f50-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="41f50-165">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="41f50-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
