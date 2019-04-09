---
title: <scopedCertificates> 項目
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 73e78a6ca27ed45e1eadc7121987b75f79bc6aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145196"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="376aa-102">\<scopedCertificates > 項目</span><span class="sxs-lookup"><span data-stu-id="376aa-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="376aa-103">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="376aa-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="376aa-104">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="376aa-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="376aa-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="376aa-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="376aa-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="376aa-106">\<behaviors></span></span>  
<span data-ttu-id="376aa-107">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="376aa-107">endpointBehaviors section</span></span>  
<span data-ttu-id="376aa-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="376aa-108">\<behavior></span></span>  
<span data-ttu-id="376aa-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="376aa-109">\<clientCredentials></span></span>  
<span data-ttu-id="376aa-110">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="376aa-110">\<serviceCertificate></span></span>  
<span data-ttu-id="376aa-111">\<scopedCertificates > 項目</span><span class="sxs-lookup"><span data-stu-id="376aa-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="376aa-112">\<add> element for \<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="376aa-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="376aa-113">語法</span><span class="sxs-lookup"><span data-stu-id="376aa-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="376aa-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="376aa-114">Attributes and Elements</span></span>  
 <span data-ttu-id="376aa-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="376aa-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="376aa-116">屬性</span><span class="sxs-lookup"><span data-stu-id="376aa-116">Attributes</span></span>  
 <span data-ttu-id="376aa-117">無。</span><span class="sxs-lookup"><span data-stu-id="376aa-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="376aa-118">子元素</span><span class="sxs-lookup"><span data-stu-id="376aa-118">Child Elements</span></span>  
  
|<span data-ttu-id="376aa-119">項目</span><span class="sxs-lookup"><span data-stu-id="376aa-119">Element</span></span>|<span data-ttu-id="376aa-120">描述</span><span class="sxs-lookup"><span data-stu-id="376aa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="376aa-121">\<add></span><span class="sxs-lookup"><span data-stu-id="376aa-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="376aa-122">將 X.509 憑證加入至範圍憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="376aa-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="376aa-123">父項目</span><span class="sxs-lookup"><span data-stu-id="376aa-123">Parent Elements</span></span>  
  
|<span data-ttu-id="376aa-124">項目</span><span class="sxs-lookup"><span data-stu-id="376aa-124">Element</span></span>|<span data-ttu-id="376aa-125">描述</span><span class="sxs-lookup"><span data-stu-id="376aa-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="376aa-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="376aa-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="376aa-127">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="376aa-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="376aa-128">備註</span><span class="sxs-lookup"><span data-stu-id="376aa-128">Remarks</span></span>  
 <span data-ttu-id="376aa-129">這個集合可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="376aa-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="376aa-130">在用戶端可以與多重服務 (終端服務以及中繼安全性權杖服務) 進行通訊的已核發權杖情況中，這個屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="376aa-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="376aa-131">對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="376aa-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="376aa-132">如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。</span><span class="sxs-lookup"><span data-stu-id="376aa-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="376aa-133">如需詳細資訊，請參閱的 < 範圍憑證 > 一節[How to:建立聯合用戶端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)。</span><span class="sxs-lookup"><span data-stu-id="376aa-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="376aa-134">範例</span><span class="sxs-lookup"><span data-stu-id="376aa-134">Example</span></span>  
 <span data-ttu-id="376aa-135">下列範例會指定網域名稱與端點通訊時要使用用戶端的服務憑證 `http://www.contoso.com` 透過 HTTP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="376aa-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="376aa-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="376aa-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="376aa-137">使用憑證</span><span class="sxs-lookup"><span data-stu-id="376aa-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="376aa-138">HOW TO：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="376aa-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="376aa-139">\<add></span><span class="sxs-lookup"><span data-stu-id="376aa-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)
- [<span data-ttu-id="376aa-140">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="376aa-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="376aa-141">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="376aa-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
