---
title: <certificate> 項目的 <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 94241d022e8a97253100a67e2a779593861c093c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366513"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="cd1eb-102">\<憑證 > 的\<clientCertificate > 項目</span><span class="sxs-lookup"><span data-stu-id="cd1eb-102">\<certificate> of \<clientCertificate> Element</span></span>
<span data-ttu-id="cd1eb-103">指定用來簽署與加密訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
 <span data-ttu-id="cd1eb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cd1eb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cd1eb-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="cd1eb-105">\<behaviors></span></span>  
<span data-ttu-id="cd1eb-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cd1eb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cd1eb-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="cd1eb-107">\<behavior></span></span>  
<span data-ttu-id="cd1eb-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cd1eb-108">\<serviceCredentials></span></span>  
<span data-ttu-id="cd1eb-109">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="cd1eb-109">\<clientCertificate></span></span>  
<span data-ttu-id="cd1eb-110">\<certificate></span><span class="sxs-lookup"><span data-stu-id="cd1eb-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd1eb-111">語法</span><span class="sxs-lookup"><span data-stu-id="cd1eb-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd1eb-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cd1eb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cd1eb-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="cd1eb-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd1eb-114">屬性</span><span class="sxs-lookup"><span data-stu-id="cd1eb-114">Attributes</span></span>  
  
|<span data-ttu-id="cd1eb-115">屬性</span><span class="sxs-lookup"><span data-stu-id="cd1eb-115">Attribute</span></span>|<span data-ttu-id="cd1eb-116">描述</span><span class="sxs-lookup"><span data-stu-id="cd1eb-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="cd1eb-117">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="cd1eb-118">屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-118">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="cd1eb-119">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="cd1eb-120">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-120">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="cd1eb-121">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="cd1eb-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cd1eb-122">-LocalMachine: 指派憑證存放區到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="cd1eb-123">-CurrentUser: 指派憑證存放區目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="cd1eb-124">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="cd1eb-125">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="cd1eb-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="cd1eb-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cd1eb-127">-AddressBook:其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="cd1eb-128">-   AuthRoot:第三方憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="cd1eb-129">-CertificationAuthority:中繼憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-129">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="cd1eb-130">-不允許：已撤銷之憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="cd1eb-131">-我：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="cd1eb-132">根目錄：受信任的根憑證授權單位 (Ca) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="cd1eb-133">-TrustedPeople:直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-133">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="cd1eb-134">-TrustedPublisher:直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-134">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="cd1eb-135">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="cd1eb-136">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="cd1eb-137">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="cd1eb-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cd1eb-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="cd1eb-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="cd1eb-139">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="cd1eb-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="cd1eb-140">-   FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="cd1eb-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="cd1eb-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="cd1eb-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="cd1eb-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="cd1eb-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="cd1eb-143">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="cd1eb-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="cd1eb-144">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="cd1eb-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="cd1eb-145">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="cd1eb-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="cd1eb-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="cd1eb-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="cd1eb-147">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="cd1eb-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="cd1eb-148">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="cd1eb-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="cd1eb-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="cd1eb-149">-   FindByExtension</span></span><br /><span data-ttu-id="cd1eb-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="cd1eb-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="cd1eb-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="cd1eb-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="cd1eb-152">
  `findValue\` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="cd1eb-153">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd1eb-154">子元素</span><span class="sxs-lookup"><span data-stu-id="cd1eb-154">Child Elements</span></span>  
 <span data-ttu-id="cd1eb-155">無。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd1eb-156">父項目</span><span class="sxs-lookup"><span data-stu-id="cd1eb-156">Parent Elements</span></span>  
  
|<span data-ttu-id="cd1eb-157">項目</span><span class="sxs-lookup"><span data-stu-id="cd1eb-157">Element</span></span>|<span data-ttu-id="cd1eb-158">描述</span><span class="sxs-lookup"><span data-stu-id="cd1eb-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd1eb-159">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="cd1eb-159">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="cd1eb-160">備註</span><span class="sxs-lookup"><span data-stu-id="cd1eb-160">Remarks</span></span>  
 <span data-ttu-id="cd1eb-161">當服務必須具有用戶端的憑證，進而與用戶端安全地進行通訊時，則會使用 `<certificate>` 項目。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-161">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="cd1eb-162">這種情況發生在使用雙工通訊模式時。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-162">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="cd1eb-163">在較為典型的要求/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-163">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="cd1eb-164">然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-164">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="cd1eb-165">所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-165">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="cd1eb-166">如需有關雙工服務的詳細資訊，請參閱[How to:建立雙工合約](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-166">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd1eb-167">範例</span><span class="sxs-lookup"><span data-stu-id="cd1eb-167">Example</span></span>  
 <span data-ttu-id="cd1eb-168">下列程式碼說明如何在 `<authentication>` 項目中尋找適當的 X.509 憑證和自訂驗證類型。</span><span class="sxs-lookup"><span data-stu-id="cd1eb-168">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="cd1eb-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd1eb-169">See also</span></span>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="cd1eb-170">安全性行為</span><span class="sxs-lookup"><span data-stu-id="cd1eb-170">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="cd1eb-171">如何：建立使用自訂憑證驗證程式服務</span><span class="sxs-lookup"><span data-stu-id="cd1eb-171">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="cd1eb-172">使用憑證</span><span class="sxs-lookup"><span data-stu-id="cd1eb-172">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
