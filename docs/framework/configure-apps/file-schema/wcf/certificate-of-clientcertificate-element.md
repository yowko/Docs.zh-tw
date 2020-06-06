---
title: <certificate> 項目的 <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400537"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="c5ae1-102">\<certificate> 項目的 \<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="c5ae1-102">\<certificate> of \<clientCertificate> Element</span></span>
<span data-ttu-id="c5ae1-103">指定用來簽署與加密訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="c5ae1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5ae1-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5ae1-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5ae1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c5ae1-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="c5ae1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5ae1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c5ae1-107">Attributes</span></span>  
  
|<span data-ttu-id="c5ae1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c5ae1-108">Attribute</span></span>|<span data-ttu-id="c5ae1-109">描述</span><span class="sxs-lookup"><span data-stu-id="c5ae1-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="c5ae1-110">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="c5ae1-111">屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="c5ae1-112">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="c5ae1-113">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="c5ae1-114">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="c5ae1-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c5ae1-115">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="c5ae1-116">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="c5ae1-117">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="c5ae1-118">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="c5ae1-119">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="c5ae1-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c5ae1-120">-通訊錄：其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="c5ae1-121">-AuthRoot：協力廠商憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="c5ae1-122">-Microsoft-windows-certificationauthority：中繼憑證授權單位單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-122">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="c5ae1-123">-不允許：已撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="c5ae1-124">-My：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="c5ae1-125">-Root：信任的根憑證授權單位（Ca）的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="c5ae1-126">-TrustedPeople：直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="c5ae1-127">-TrustedPublisher：直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="c5ae1-128">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="c5ae1-129">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="c5ae1-130">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="c5ae1-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c5ae1-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="c5ae1-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="c5ae1-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="c5ae1-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="c5ae1-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c5ae1-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="c5ae1-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="c5ae1-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="c5ae1-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c5ae1-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="c5ae1-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="c5ae1-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="c5ae1-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="c5ae1-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="c5ae1-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="c5ae1-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="c5ae1-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="c5ae1-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="c5ae1-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="c5ae1-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="c5ae1-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="c5ae1-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="c5ae1-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="c5ae1-142">-   FindByExtension</span></span><br /><span data-ttu-id="c5ae1-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="c5ae1-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="c5ae1-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="c5ae1-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="c5ae1-145">`findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="c5ae1-146">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5ae1-147">子元素</span><span class="sxs-lookup"><span data-stu-id="c5ae1-147">Child Elements</span></span>  
 <span data-ttu-id="c5ae1-148">無。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5ae1-149">父項目</span><span class="sxs-lookup"><span data-stu-id="c5ae1-149">Parent Elements</span></span>  
  
|<span data-ttu-id="c5ae1-150">元素</span><span class="sxs-lookup"><span data-stu-id="c5ae1-150">Element</span></span>|<span data-ttu-id="c5ae1-151">描述</span><span class="sxs-lookup"><span data-stu-id="c5ae1-151">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="c5ae1-152">備註</span><span class="sxs-lookup"><span data-stu-id="c5ae1-152">Remarks</span></span>  
 <span data-ttu-id="c5ae1-153">當服務必須具有用戶端的憑證，進而與用戶端安全地進行通訊時，則會使用 `<certificate>` 項目。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-153">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="c5ae1-154">這種情況發生在使用雙工通訊模式時。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-154">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="c5ae1-155">在較為典型的要求/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-155">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="c5ae1-156">然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-156">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="c5ae1-157">所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-157">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="c5ae1-158">如需雙工服務的詳細資訊，請參閱[如何：建立雙工合約](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-158">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5ae1-159">範例</span><span class="sxs-lookup"><span data-stu-id="c5ae1-159">Example</span></span>  
 <span data-ttu-id="c5ae1-160">下列程式碼說明如何在 `<authentication>` 項目中尋找適當的 X.509 憑證和自訂驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c5ae1-160">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5ae1-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5ae1-161">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="c5ae1-162">安全性行為</span><span class="sxs-lookup"><span data-stu-id="c5ae1-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c5ae1-163">HOW TO：建立使用自訂憑證驗證程式的服務</span><span class="sxs-lookup"><span data-stu-id="c5ae1-163">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="c5ae1-164">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="c5ae1-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
