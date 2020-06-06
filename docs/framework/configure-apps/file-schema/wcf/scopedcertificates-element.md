---
title: <scopedCertificates> 項目
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399960"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="8eed4-102">\<scopedCertificates> 項目</span><span class="sxs-lookup"><span data-stu-id="8eed4-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="8eed4-103">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="8eed4-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="8eed4-104">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8eed4-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="8eed4-105">語法</span><span class="sxs-lookup"><span data-stu-id="8eed4-105">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8eed4-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8eed4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8eed4-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8eed4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eed4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8eed4-108">Attributes</span></span>  
 <span data-ttu-id="8eed4-109">無。</span><span class="sxs-lookup"><span data-stu-id="8eed4-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8eed4-110">子元素</span><span class="sxs-lookup"><span data-stu-id="8eed4-110">Child Elements</span></span>  
  
|<span data-ttu-id="8eed4-111">元素</span><span class="sxs-lookup"><span data-stu-id="8eed4-111">Element</span></span>|<span data-ttu-id="8eed4-112">描述</span><span class="sxs-lookup"><span data-stu-id="8eed4-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="8eed4-113">將 X.509 憑證加入至範圍憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="8eed4-113">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8eed4-114">父項目</span><span class="sxs-lookup"><span data-stu-id="8eed4-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8eed4-115">元素</span><span class="sxs-lookup"><span data-stu-id="8eed4-115">Element</span></span>|<span data-ttu-id="8eed4-116">描述</span><span class="sxs-lookup"><span data-stu-id="8eed4-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="8eed4-117">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="8eed4-117">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eed4-118">備註</span><span class="sxs-lookup"><span data-stu-id="8eed4-118">Remarks</span></span>  
 <span data-ttu-id="8eed4-119">這個集合可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8eed4-119">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="8eed4-120">在用戶端可以與多重服務 (終端服務以及中繼安全性權杖服務) 進行通訊的已核發權杖情況中，這個屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="8eed4-120">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="8eed4-121">對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="8eed4-121">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="8eed4-122">如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。</span><span class="sxs-lookup"><span data-stu-id="8eed4-122">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="8eed4-123">如需詳細資訊，請參閱[如何：建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)的「限定範圍的憑證」一節。</span><span class="sxs-lookup"><span data-stu-id="8eed4-123">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eed4-124">範例</span><span class="sxs-lookup"><span data-stu-id="8eed4-124">Example</span></span>  
 <span data-ttu-id="8eed4-125">下列範例會為用戶端指定服務憑證，以便在與其功能變數名稱是透過 HTTP 通訊協定的端點進行通訊時使用 `http://www.contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="8eed4-125">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8eed4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eed4-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="8eed4-127">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="8eed4-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8eed4-128">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="8eed4-128">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="8eed4-129">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="8eed4-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8eed4-130">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="8eed4-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
