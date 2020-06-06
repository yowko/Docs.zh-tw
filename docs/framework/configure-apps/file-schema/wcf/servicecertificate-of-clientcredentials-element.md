---
title: <serviceCertificate> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399676"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="8d72c-102">\<serviceCertificate> 項目的 \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8d72c-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="8d72c-103">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="8d72c-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="8d72c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d72c-104">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d72c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8d72c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8d72c-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8d72c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d72c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8d72c-107">Attributes</span></span>  
 <span data-ttu-id="8d72c-108">無。</span><span class="sxs-lookup"><span data-stu-id="8d72c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d72c-109">子元素</span><span class="sxs-lookup"><span data-stu-id="8d72c-109">Child Elements</span></span>  
  
|<span data-ttu-id="8d72c-110">元素</span><span class="sxs-lookup"><span data-stu-id="8d72c-110">Element</span></span>|<span data-ttu-id="8d72c-111">描述</span><span class="sxs-lookup"><span data-stu-id="8d72c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="8d72c-112">指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="8d72c-112">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="8d72c-113">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="8d72c-113">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="8d72c-114">這個集合通常用來指定聯合案例中安全性權杖服務的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8d72c-114">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="8d72c-115">為用戶端使用的服務憑證指定驗證行為。</span><span class="sxs-lookup"><span data-stu-id="8d72c-115">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d72c-116">父項目</span><span class="sxs-lookup"><span data-stu-id="8d72c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8d72c-117">元素</span><span class="sxs-lookup"><span data-stu-id="8d72c-117">Element</span></span>|<span data-ttu-id="8d72c-118">描述</span><span class="sxs-lookup"><span data-stu-id="8d72c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="8d72c-119">指定用戶端用來對服務驗證本身的認證。</span><span class="sxs-lookup"><span data-stu-id="8d72c-119">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d72c-120">備註</span><span class="sxs-lookup"><span data-stu-id="8d72c-120">Remarks</span></span>  
 <span data-ttu-id="8d72c-121">這個組態項目會指定用戶端用來驗證憑證的設定，而這份憑證是由使用 SSL 驗證的服務所提供。</span><span class="sxs-lookup"><span data-stu-id="8d72c-121">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="8d72c-122">它另外包含的任何憑證，可讓已明確設定於用戶端上的服務在使用訊息安全性時用於加密傳給服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="8d72c-122">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="8d72c-123">元素的屬性與的 `serviceCertificate` 屬性完全相同 [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="8d72c-123">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d72c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d72c-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="8d72c-125">安全性行為</span><span class="sxs-lookup"><span data-stu-id="8d72c-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8d72c-126">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="8d72c-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8d72c-127">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="8d72c-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8d72c-128">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="8d72c-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
