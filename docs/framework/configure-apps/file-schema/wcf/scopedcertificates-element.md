---
title: <scopedCertificates> 項目
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: ed53a42575a8d57c365f7a329a1a9c1df075d6d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935227"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="fb2ae-102">\<scopedCertificates > 元素</span><span class="sxs-lookup"><span data-stu-id="fb2ae-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="fb2ae-103">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="fb2ae-104">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="fb2ae-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fb2ae-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fb2ae-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="fb2ae-106">\<behaviors></span></span>  
<span data-ttu-id="fb2ae-107">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="fb2ae-107">endpointBehaviors section</span></span>  
<span data-ttu-id="fb2ae-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="fb2ae-108">\<behavior></span></span>  
<span data-ttu-id="fb2ae-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="fb2ae-109">\<clientCredentials></span></span>  
<span data-ttu-id="fb2ae-110">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="fb2ae-110">\<serviceCertificate></span></span>  
<span data-ttu-id="fb2ae-111">\<scopedCertificates > 元素</span><span class="sxs-lookup"><span data-stu-id="fb2ae-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="fb2ae-112">\<新增 scopedCertificates > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="fb2ae-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2ae-113">語法</span><span class="sxs-lookup"><span data-stu-id="fb2ae-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb2ae-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fb2ae-114">Attributes and Elements</span></span>  
 <span data-ttu-id="fb2ae-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb2ae-116">屬性</span><span class="sxs-lookup"><span data-stu-id="fb2ae-116">Attributes</span></span>  
 <span data-ttu-id="fb2ae-117">無。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb2ae-118">子元素</span><span class="sxs-lookup"><span data-stu-id="fb2ae-118">Child Elements</span></span>  
  
|<span data-ttu-id="fb2ae-119">項目</span><span class="sxs-lookup"><span data-stu-id="fb2ae-119">Element</span></span>|<span data-ttu-id="fb2ae-120">說明</span><span class="sxs-lookup"><span data-stu-id="fb2ae-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb2ae-121">\<add></span><span class="sxs-lookup"><span data-stu-id="fb2ae-121">\<add></span></span>](add-of-scopedcertificates-element.md)|<span data-ttu-id="fb2ae-122">將 X.509 憑證加入至範圍憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb2ae-123">父項目</span><span class="sxs-lookup"><span data-stu-id="fb2ae-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fb2ae-124">項目</span><span class="sxs-lookup"><span data-stu-id="fb2ae-124">Element</span></span>|<span data-ttu-id="fb2ae-125">說明</span><span class="sxs-lookup"><span data-stu-id="fb2ae-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb2ae-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="fb2ae-126">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="fb2ae-127">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb2ae-128">備註</span><span class="sxs-lookup"><span data-stu-id="fb2ae-128">Remarks</span></span>  
 <span data-ttu-id="fb2ae-129">這個集合可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="fb2ae-130">在用戶端可以與多重服務 (終端服務以及中繼安全性權杖服務) 進行通訊的已核發權杖情況中，這個屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="fb2ae-131">對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="fb2ae-132">如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="fb2ae-133">如需詳細資訊, 請參閱[如何:建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb2ae-134">範例</span><span class="sxs-lookup"><span data-stu-id="fb2ae-134">Example</span></span>  
 <span data-ttu-id="fb2ae-135">下列範例會指定網域名稱與端點通訊時要使用用戶端的服務憑證 `http://www.contoso.com` 透過 HTTP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="fb2ae-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb2ae-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb2ae-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="fb2ae-137">使用憑證</span><span class="sxs-lookup"><span data-stu-id="fb2ae-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="fb2ae-138">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="fb2ae-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="fb2ae-139">\<add></span><span class="sxs-lookup"><span data-stu-id="fb2ae-139">\<add></span></span>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="fb2ae-140">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="fb2ae-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="fb2ae-141">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="fb2ae-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
