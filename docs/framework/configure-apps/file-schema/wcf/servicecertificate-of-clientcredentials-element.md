---
title: <serviceCertificate> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399676"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="da367-102">\<clientCredentials > 元素\<的 serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="da367-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="da367-103">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="da367-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
<span data-ttu-id="da367-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="da367-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="da367-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="da367-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="da367-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="da367-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="da367-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="da367-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="da367-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="da367-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="da367-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="da367-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="da367-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="da367-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da367-111">語法</span><span class="sxs-lookup"><span data-stu-id="da367-111">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da367-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="da367-112">Attributes and Elements</span></span>  
 <span data-ttu-id="da367-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="da367-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da367-114">屬性</span><span class="sxs-lookup"><span data-stu-id="da367-114">Attributes</span></span>  
 <span data-ttu-id="da367-115">無。</span><span class="sxs-lookup"><span data-stu-id="da367-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da367-116">子元素</span><span class="sxs-lookup"><span data-stu-id="da367-116">Child Elements</span></span>  
  
|<span data-ttu-id="da367-117">項目</span><span class="sxs-lookup"><span data-stu-id="da367-117">Element</span></span>|<span data-ttu-id="da367-118">說明</span><span class="sxs-lookup"><span data-stu-id="da367-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da367-119">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="da367-119">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="da367-120">指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="da367-120">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="da367-121">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="da367-121">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="da367-122">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="da367-122">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="da367-123">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="da367-123">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="da367-124">\<authentication></span><span class="sxs-lookup"><span data-stu-id="da367-124">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="da367-125">為用戶端使用的服務憑證指定驗證行為。</span><span class="sxs-lookup"><span data-stu-id="da367-125">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da367-126">父項目</span><span class="sxs-lookup"><span data-stu-id="da367-126">Parent Elements</span></span>  
  
|<span data-ttu-id="da367-127">項目</span><span class="sxs-lookup"><span data-stu-id="da367-127">Element</span></span>|<span data-ttu-id="da367-128">說明</span><span class="sxs-lookup"><span data-stu-id="da367-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da367-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="da367-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="da367-130">指定用戶端用來對服務驗證本身的認證。</span><span class="sxs-lookup"><span data-stu-id="da367-130">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da367-131">備註</span><span class="sxs-lookup"><span data-stu-id="da367-131">Remarks</span></span>  
 <span data-ttu-id="da367-132">這個組態項目會指定用戶端用來驗證憑證的設定，而這份憑證是由使用 SSL 驗證的服務所提供。</span><span class="sxs-lookup"><span data-stu-id="da367-132">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="da367-133">它另外包含的任何憑證，可讓已明確設定於用戶端上的服務在使用訊息安全性時用於加密傳給服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="da367-133">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="da367-134">`serviceCertificate`元素的屬性與[ \<clientCertificate >](clientcertificate-of-clientcredentials-element.md)的屬性相同。</span><span class="sxs-lookup"><span data-stu-id="da367-134">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da367-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da367-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="da367-136">安全性行為</span><span class="sxs-lookup"><span data-stu-id="da367-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="da367-137">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="da367-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="da367-138">使用憑證</span><span class="sxs-lookup"><span data-stu-id="da367-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="da367-139">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="da367-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
