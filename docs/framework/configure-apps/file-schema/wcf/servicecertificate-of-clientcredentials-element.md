---
title: "&lt;clientCredentials&gt; 的 &lt;serviceCertificate&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3fbb3ef0fddd287fa3feb30732b26c651ac0067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="b1a09-102">&lt;clientCredentials&gt; 的 &lt;serviceCertificate&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="b1a09-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="b1a09-103">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="b1a09-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="b1a09-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b1a09-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1a09-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b1a09-105">\<behaviors></span></span>  
<span data-ttu-id="b1a09-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b1a09-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="b1a09-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="b1a09-107">\<behavior></span></span>  
<span data-ttu-id="b1a09-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="b1a09-108">\<clientCredentials></span></span>  
<span data-ttu-id="b1a09-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="b1a09-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a09-110">語法</span><span class="sxs-lookup"><span data-stu-id="b1a09-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1a09-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1a09-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b1a09-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b1a09-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1a09-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b1a09-113">Attributes</span></span>  
 <span data-ttu-id="b1a09-114">無。</span><span class="sxs-lookup"><span data-stu-id="b1a09-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1a09-115">子項目</span><span class="sxs-lookup"><span data-stu-id="b1a09-115">Child Elements</span></span>  
  
|<span data-ttu-id="b1a09-116">項目</span><span class="sxs-lookup"><span data-stu-id="b1a09-116">Element</span></span>|<span data-ttu-id="b1a09-117">說明</span><span class="sxs-lookup"><span data-stu-id="b1a09-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1a09-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="b1a09-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="b1a09-119">指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="b1a09-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="b1a09-120">\<但是在 scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="b1a09-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="b1a09-121">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="b1a09-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="b1a09-122">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="b1a09-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="b1a09-123">\<驗證 ></span><span class="sxs-lookup"><span data-stu-id="b1a09-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="b1a09-124">為用戶端使用的服務憑證指定驗證行為。</span><span class="sxs-lookup"><span data-stu-id="b1a09-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1a09-125">父項目</span><span class="sxs-lookup"><span data-stu-id="b1a09-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b1a09-126">項目</span><span class="sxs-lookup"><span data-stu-id="b1a09-126">Element</span></span>|<span data-ttu-id="b1a09-127">說明</span><span class="sxs-lookup"><span data-stu-id="b1a09-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1a09-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="b1a09-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="b1a09-129">指定用戶端用來對服務驗證本身的認證。</span><span class="sxs-lookup"><span data-stu-id="b1a09-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a09-130">備註</span><span class="sxs-lookup"><span data-stu-id="b1a09-130">Remarks</span></span>  
 <span data-ttu-id="b1a09-131">這個組態項目會指定用戶端用來驗證憑證的設定，而這份憑證是由使用 SSL 驗證的服務所提供。</span><span class="sxs-lookup"><span data-stu-id="b1a09-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="b1a09-132">它另外包含的任何憑證，可讓已明確設定於用戶端上的服務在使用訊息安全性時用於加密傳給服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="b1a09-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="b1a09-133">屬性的`serviceCertificate`項目是屬性的相同[ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)。</span><span class="sxs-lookup"><span data-stu-id="b1a09-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a09-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1a09-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="b1a09-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="b1a09-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b1a09-136">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="b1a09-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="b1a09-137">使用憑證</span><span class="sxs-lookup"><span data-stu-id="b1a09-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="b1a09-138">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="b1a09-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
