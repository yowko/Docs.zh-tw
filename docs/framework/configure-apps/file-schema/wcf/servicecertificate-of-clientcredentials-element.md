---
title: <serviceCertificate> <clientCredentials>項目
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4fe196ef8737c7abde939e36c2bb7afd5a0d86b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145336"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="9b0b3-102">\<serviceCertificate > 的\<clientCredentials > 項目</span><span class="sxs-lookup"><span data-stu-id="9b0b3-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="9b0b3-103">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="9b0b3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9b0b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9b0b3-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="9b0b3-105">\<behaviors></span></span>  
<span data-ttu-id="9b0b3-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="9b0b3-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="9b0b3-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9b0b3-107">\<behavior></span></span>  
<span data-ttu-id="9b0b3-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="9b0b3-108">\<clientCredentials></span></span>  
<span data-ttu-id="9b0b3-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="9b0b3-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0b3-110">語法</span><span class="sxs-lookup"><span data-stu-id="9b0b3-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b0b3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9b0b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9b0b3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b0b3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9b0b3-113">Attributes</span></span>  
 <span data-ttu-id="9b0b3-114">無。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b0b3-115">子元素</span><span class="sxs-lookup"><span data-stu-id="9b0b3-115">Child Elements</span></span>  
  
|<span data-ttu-id="9b0b3-116">項目</span><span class="sxs-lookup"><span data-stu-id="9b0b3-116">Element</span></span>|<span data-ttu-id="9b0b3-117">描述</span><span class="sxs-lookup"><span data-stu-id="9b0b3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b0b3-118">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="9b0b3-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="9b0b3-119">指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="9b0b3-120">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="9b0b3-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="9b0b3-121">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="9b0b3-122">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="9b0b3-123">\<驗證 ></span><span class="sxs-lookup"><span data-stu-id="9b0b3-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="9b0b3-124">為用戶端使用的服務憑證指定驗證行為。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b0b3-125">父項目</span><span class="sxs-lookup"><span data-stu-id="9b0b3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9b0b3-126">項目</span><span class="sxs-lookup"><span data-stu-id="9b0b3-126">Element</span></span>|<span data-ttu-id="9b0b3-127">描述</span><span class="sxs-lookup"><span data-stu-id="9b0b3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b0b3-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="9b0b3-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="9b0b3-129">指定用戶端用來對服務驗證本身的認證。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b0b3-130">備註</span><span class="sxs-lookup"><span data-stu-id="9b0b3-130">Remarks</span></span>  
 <span data-ttu-id="9b0b3-131">這個組態項目會指定用戶端用來驗證憑證的設定，而這份憑證是由使用 SSL 驗證的服務所提供。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="9b0b3-132">它另外包含的任何憑證，可讓已明確設定於用戶端上的服務在使用訊息安全性時用於加密傳給服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="9b0b3-133">屬性`serviceCertificate`項目完全相同的屬性[ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)。</span><span class="sxs-lookup"><span data-stu-id="9b0b3-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0b3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b0b3-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="9b0b3-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="9b0b3-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9b0b3-136">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="9b0b3-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="9b0b3-137">使用憑證</span><span class="sxs-lookup"><span data-stu-id="9b0b3-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9b0b3-138">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="9b0b3-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
