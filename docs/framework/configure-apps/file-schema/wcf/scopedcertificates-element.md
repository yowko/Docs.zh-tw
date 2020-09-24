---
title: <scopedCertificates> 項目
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 4bee627fe186ed8dd85c118a37f59f575eb4650e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162253"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="8b00e-102">\<scopedCertificates> 項目</span><span class="sxs-lookup"><span data-stu-id="8b00e-102">\<scopedCertificates> Element</span></span>

<span data-ttu-id="8b00e-103">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="8b00e-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="8b00e-104">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8b00e-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="8b00e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b00e-105">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b00e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8b00e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8b00e-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8b00e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b00e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8b00e-108">Attributes</span></span>  

 <span data-ttu-id="8b00e-109">無。</span><span class="sxs-lookup"><span data-stu-id="8b00e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8b00e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="8b00e-110">Child Elements</span></span>  
  
|<span data-ttu-id="8b00e-111">項目</span><span class="sxs-lookup"><span data-stu-id="8b00e-111">Element</span></span>|<span data-ttu-id="8b00e-112">描述</span><span class="sxs-lookup"><span data-stu-id="8b00e-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="8b00e-113">將 X.509 憑證加入至範圍憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="8b00e-113">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b00e-114">父項目</span><span class="sxs-lookup"><span data-stu-id="8b00e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8b00e-115">項目</span><span class="sxs-lookup"><span data-stu-id="8b00e-115">Element</span></span>|<span data-ttu-id="8b00e-116">描述</span><span class="sxs-lookup"><span data-stu-id="8b00e-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="8b00e-117">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="8b00e-117">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b00e-118">備註</span><span class="sxs-lookup"><span data-stu-id="8b00e-118">Remarks</span></span>  

 <span data-ttu-id="8b00e-119">這個集合可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8b00e-119">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="8b00e-120">在用戶端可以與多重服務 (終端服務以及中繼安全性權杖服務) 進行通訊的已核發權杖情況中，這個屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="8b00e-120">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="8b00e-121">對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="8b00e-121">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="8b00e-122">如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。</span><span class="sxs-lookup"><span data-stu-id="8b00e-122">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="8b00e-123">如需詳細資訊，請參閱 [如何：建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)的「範圍憑證」一節。</span><span class="sxs-lookup"><span data-stu-id="8b00e-123">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b00e-124">範例</span><span class="sxs-lookup"><span data-stu-id="8b00e-124">Example</span></span>  

 <span data-ttu-id="8b00e-125">下列範例會指定用戶端在透過 HTTP 通訊協定上的功能變數名稱進行通訊時，所要使用的服務憑證 `http://www.contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="8b00e-125">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b00e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b00e-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="8b00e-127">使用憑證</span><span class="sxs-lookup"><span data-stu-id="8b00e-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8b00e-128">作法：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="8b00e-128">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="8b00e-129">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8b00e-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8b00e-130">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8b00e-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
