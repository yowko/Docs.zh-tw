---
title: <clientCertificate> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: aceb30b6354bac5c327a5f4367344e5c9608b689
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286893"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="bf01e-102">\<clientCertificate> of \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bf01e-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="bf01e-103">定義雙工通訊模式中，用來簽署與加密服務至用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="bf01e-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="bf01e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf01e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf01e-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="bf01e-105">\<behaviors></span></span>  
<span data-ttu-id="bf01e-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bf01e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bf01e-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bf01e-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="bf01e-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bf01e-108">\<behavior></span></span>  
<span data-ttu-id="bf01e-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bf01e-109">\<serviceCredentials></span></span>  
<span data-ttu-id="bf01e-110">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="bf01e-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf01e-111">語法</span><span class="sxs-lookup"><span data-stu-id="bf01e-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf01e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bf01e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bf01e-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="bf01e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf01e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="bf01e-114">Attributes</span></span>  
 <span data-ttu-id="bf01e-115">無。</span><span class="sxs-lookup"><span data-stu-id="bf01e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf01e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="bf01e-116">Child Elements</span></span>  
  
|<span data-ttu-id="bf01e-117">項目</span><span class="sxs-lookup"><span data-stu-id="bf01e-117">Element</span></span>|<span data-ttu-id="bf01e-118">描述</span><span class="sxs-lookup"><span data-stu-id="bf01e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf01e-119">\<authentication></span><span class="sxs-lookup"><span data-stu-id="bf01e-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="bf01e-120">指定用戶端憑證的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="bf01e-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="bf01e-121">\<certificate></span><span class="sxs-lookup"><span data-stu-id="bf01e-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="bf01e-122">指定要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="bf01e-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf01e-123">父項目</span><span class="sxs-lookup"><span data-stu-id="bf01e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf01e-124">項目</span><span class="sxs-lookup"><span data-stu-id="bf01e-124">Element</span></span>|<span data-ttu-id="bf01e-125">描述</span><span class="sxs-lookup"><span data-stu-id="bf01e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf01e-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bf01e-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="bf01e-127">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="bf01e-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf01e-128">備註</span><span class="sxs-lookup"><span data-stu-id="bf01e-128">Remarks</span></span>  
 <span data-ttu-id="bf01e-129">當服務必須具有用戶端的憑證才能與用戶端安全地進行通訊時，則會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="bf01e-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="bf01e-130">這種情況發生在使用雙工通訊模式時。</span><span class="sxs-lookup"><span data-stu-id="bf01e-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="bf01e-131">在較為典型的要求/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。</span><span class="sxs-lookup"><span data-stu-id="bf01e-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="bf01e-132">然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="bf01e-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="bf01e-133">所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。</span><span class="sxs-lookup"><span data-stu-id="bf01e-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="bf01e-134">如需有關雙工服務的詳細資訊，請參閱[How to:建立雙工合約](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="bf01e-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="bf01e-135">設定在這個項目中的憑證，只能在繫結是以 `MutualCertificateDuplex` 訊息安全性驗證模式所設定的情況下，才可用來加密傳送給用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf01e-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf01e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf01e-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="bf01e-137">如何：建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="bf01e-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="bf01e-138">安全性行為</span><span class="sxs-lookup"><span data-stu-id="bf01e-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="bf01e-139">使用憑證</span><span class="sxs-lookup"><span data-stu-id="bf01e-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
