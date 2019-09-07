---
title: <certificate> 項目的 <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400537"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="b4ed8-102">\<clientCertificate > 元素\<的憑證 ></span><span class="sxs-lookup"><span data-stu-id="b4ed8-102">\<certificate> of \<clientCertificate> Element</span></span>
<span data-ttu-id="b4ed8-103">指定用來簽署與加密訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
<span data-ttu-id="b4ed8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4ed8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b4ed8-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b4ed8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b4ed8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b4ed8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b4ed8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b4ed8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="b4ed8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b4ed8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="b4ed8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b4ed8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="b4ed8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCertificate >** ](clientcertificate-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b4ed8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)</span></span>\
<span data-ttu-id="b4ed8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<憑證 >**</span><span class="sxs-lookup"><span data-stu-id="b4ed8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ed8-112">語法</span><span class="sxs-lookup"><span data-stu-id="b4ed8-112">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4ed8-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b4ed8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b4ed8-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="b4ed8-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4ed8-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b4ed8-115">Attributes</span></span>  
  
|<span data-ttu-id="b4ed8-116">屬性</span><span class="sxs-lookup"><span data-stu-id="b4ed8-116">Attribute</span></span>|<span data-ttu-id="b4ed8-117">描述</span><span class="sxs-lookup"><span data-stu-id="b4ed8-117">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="b4ed8-118">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-118">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="b4ed8-119">屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-119">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="b4ed8-120">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-120">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="b4ed8-121">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-121">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="b4ed8-122">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="b4ed8-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b4ed8-123">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-123">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="b4ed8-124">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-124">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="b4ed8-125">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-125">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="b4ed8-126">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-126">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="b4ed8-127">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="b4ed8-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b4ed8-128">通訊錄其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-128">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="b4ed8-129">AuthRoot協力廠商憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-129">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="b4ed8-130">Microsoft-windows-certificationauthority中繼憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-130">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="b4ed8-131">禁止已撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-131">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="b4ed8-132">'個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-132">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="b4ed8-133">路徑信任的根憑證授權單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-133">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="b4ed8-134">TrustedPeople直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-134">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="b4ed8-135">TrustedPublisher直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-135">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="b4ed8-136">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-136">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="b4ed8-137">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-137">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="b4ed8-138">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="b4ed8-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b4ed8-139">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="b4ed8-139">-   FindByThumbPrint</span></span><br /><span data-ttu-id="b4ed8-140">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="b4ed8-140">-   FindBySubjectName</span></span><br /><span data-ttu-id="b4ed8-141">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="b4ed8-141">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="b4ed8-142">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="b4ed8-142">-   FindByIssuerName</span></span><br /><span data-ttu-id="b4ed8-143">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="b4ed8-143">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="b4ed8-144">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="b4ed8-144">-   FindBySerialNumber</span></span><br /><span data-ttu-id="b4ed8-145">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="b4ed8-145">-   FindByTimeValid</span></span><br /><span data-ttu-id="b4ed8-146">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="b4ed8-146">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="b4ed8-147">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="b4ed8-147">-   FindByTemplateName</span></span><br /><span data-ttu-id="b4ed8-148">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="b4ed8-148">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="b4ed8-149">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="b4ed8-149">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="b4ed8-150">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="b4ed8-150">-   FindByExtension</span></span><br /><span data-ttu-id="b4ed8-151">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="b4ed8-151">-   FindByKeyUsage</span></span><br /><span data-ttu-id="b4ed8-152">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="b4ed8-152">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="b4ed8-153">`findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-153">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="b4ed8-154">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-154">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4ed8-155">子元素</span><span class="sxs-lookup"><span data-stu-id="b4ed8-155">Child Elements</span></span>  
 <span data-ttu-id="b4ed8-156">無。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4ed8-157">父項目</span><span class="sxs-lookup"><span data-stu-id="b4ed8-157">Parent Elements</span></span>  
  
|<span data-ttu-id="b4ed8-158">項目</span><span class="sxs-lookup"><span data-stu-id="b4ed8-158">Element</span></span>|<span data-ttu-id="b4ed8-159">描述</span><span class="sxs-lookup"><span data-stu-id="b4ed8-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4ed8-160">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="b4ed8-160">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="b4ed8-161">備註</span><span class="sxs-lookup"><span data-stu-id="b4ed8-161">Remarks</span></span>  
 <span data-ttu-id="b4ed8-162">當服務必須具有用戶端的憑證，進而與用戶端安全地進行通訊時，則會使用 `<certificate>` 項目。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-162">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="b4ed8-163">這種情況發生在使用雙工通訊模式時。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-163">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="b4ed8-164">在較為典型的要求/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-164">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="b4ed8-165">然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-165">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="b4ed8-166">所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-166">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="b4ed8-167">如需雙工服務的詳細資訊[，請參閱如何：建立雙工合約](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-167">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4ed8-168">範例</span><span class="sxs-lookup"><span data-stu-id="b4ed8-168">Example</span></span>  
 <span data-ttu-id="b4ed8-169">下列程式碼說明如何在 `<authentication>` 項目中尋找適當的 X.509 憑證和自訂驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b4ed8-169">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4ed8-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ed8-170">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="b4ed8-171">安全性行為</span><span class="sxs-lookup"><span data-stu-id="b4ed8-171">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b4ed8-172">如何：建立採用自訂憑證驗證程式的服務</span><span class="sxs-lookup"><span data-stu-id="b4ed8-172">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="b4ed8-173">使用憑證</span><span class="sxs-lookup"><span data-stu-id="b4ed8-173">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
