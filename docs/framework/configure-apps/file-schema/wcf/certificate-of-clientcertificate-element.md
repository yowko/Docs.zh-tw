---
title: <certificate> 項目的 <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 35ea3814e208921abaf44e6ef431c4e1b44cde60
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151137"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="3d51c-102">\<certificate> 項目的 \<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="3d51c-102">\<certificate> of \<clientCertificate> Element</span></span>

<span data-ttu-id="3d51c-103">指定用來簽署與加密訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="3d51c-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="3d51c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d51c-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d51c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3d51c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3d51c-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="3d51c-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d51c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3d51c-107">Attributes</span></span>  
  
|<span data-ttu-id="3d51c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3d51c-108">Attribute</span></span>|<span data-ttu-id="3d51c-109">描述</span><span class="sxs-lookup"><span data-stu-id="3d51c-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="3d51c-110">字串，其中包含要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="3d51c-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="3d51c-111">屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="3d51c-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="3d51c-112">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="3d51c-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="3d51c-113">指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區來驗證伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="3d51c-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="3d51c-114">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="3d51c-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3d51c-115">-LocalMachine：指派給本機電腦的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d51c-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="3d51c-116">-CurrentUser：指派給目前使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d51c-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="3d51c-117">預設為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="3d51c-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="3d51c-118">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d51c-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="3d51c-119">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="3d51c-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3d51c-120">-AddressBook：其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d51c-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="3d51c-121">-AuthRoot：協力廠商憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="3d51c-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="3d51c-122">-CertificationAuthority：中繼憑證授權單位單位的憑證存放區 (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="3d51c-122">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="3d51c-123">-不允許：撤銷憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d51c-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="3d51c-124">-My：個人憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d51c-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="3d51c-125">-Root：信任根憑證授權單位的憑證存放區， (CAs) 。</span><span class="sxs-lookup"><span data-stu-id="3d51c-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="3d51c-126">-TrustedPeople：直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d51c-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="3d51c-127">-TrustedPublisher：直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d51c-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="3d51c-128">預設為 My。</span><span class="sxs-lookup"><span data-stu-id="3d51c-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="3d51c-129">定義要執行之 X.509 搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="3d51c-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="3d51c-130">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="3d51c-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3d51c-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="3d51c-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="3d51c-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="3d51c-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="3d51c-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3d51c-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="3d51c-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="3d51c-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="3d51c-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3d51c-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="3d51c-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="3d51c-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="3d51c-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="3d51c-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="3d51c-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="3d51c-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="3d51c-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="3d51c-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="3d51c-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="3d51c-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="3d51c-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3d51c-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="3d51c-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="3d51c-142">-   FindByExtension</span></span><br /><span data-ttu-id="3d51c-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="3d51c-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="3d51c-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="3d51c-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="3d51c-145">`findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="3d51c-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="3d51c-146">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="3d51c-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d51c-147">子元素</span><span class="sxs-lookup"><span data-stu-id="3d51c-147">Child Elements</span></span>  

 <span data-ttu-id="3d51c-148">無。</span><span class="sxs-lookup"><span data-stu-id="3d51c-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d51c-149">父項目</span><span class="sxs-lookup"><span data-stu-id="3d51c-149">Parent Elements</span></span>  
  
|<span data-ttu-id="3d51c-150">項目</span><span class="sxs-lookup"><span data-stu-id="3d51c-150">Element</span></span>|<span data-ttu-id="3d51c-151">描述</span><span class="sxs-lookup"><span data-stu-id="3d51c-151">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="3d51c-152">備註</span><span class="sxs-lookup"><span data-stu-id="3d51c-152">Remarks</span></span>  

 <span data-ttu-id="3d51c-153">當服務必須具有用戶端的憑證，進而與用戶端安全地進行通訊時，則會使用 `<certificate>` 項目。</span><span class="sxs-lookup"><span data-stu-id="3d51c-153">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="3d51c-154">這種情況發生在使用雙工通訊模式時。</span><span class="sxs-lookup"><span data-stu-id="3d51c-154">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="3d51c-155">在較為典型的要求/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。</span><span class="sxs-lookup"><span data-stu-id="3d51c-155">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="3d51c-156">然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="3d51c-156">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="3d51c-157">所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。</span><span class="sxs-lookup"><span data-stu-id="3d51c-157">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="3d51c-158">如需雙工服務的詳細資訊，請參閱 [如何：建立雙工合約](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="3d51c-158">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d51c-159">範例</span><span class="sxs-lookup"><span data-stu-id="3d51c-159">Example</span></span>  

 <span data-ttu-id="3d51c-160">下列程式碼說明如何在 `<authentication>` 項目中尋找適當的 X.509 憑證和自訂驗證類型。</span><span class="sxs-lookup"><span data-stu-id="3d51c-160">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d51c-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d51c-161">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="3d51c-162">安全性行為</span><span class="sxs-lookup"><span data-stu-id="3d51c-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3d51c-163">作法：建立使用自訂憑證驗證程式的服務</span><span class="sxs-lookup"><span data-stu-id="3d51c-163">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="3d51c-164">使用憑證</span><span class="sxs-lookup"><span data-stu-id="3d51c-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
