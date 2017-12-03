---
title: "&lt;serviceCredentials&gt; 的 &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc2dfd94ffbf8ce08dee9c14421f389861e99e77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="81956-102">&lt;serviceCredentials&gt; 的 &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="81956-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="81956-103">定義雙工通訊模式中，用來簽署與加密服務至用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="81956-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="81956-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="81956-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="81956-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="81956-105">\<behaviors></span></span>  
<span data-ttu-id="81956-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="81956-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="81956-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="81956-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="81956-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="81956-108">\<behavior></span></span>  
<span data-ttu-id="81956-109">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="81956-109">\<serviceCredentials></span></span>  
<span data-ttu-id="81956-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="81956-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81956-111">語法</span><span class="sxs-lookup"><span data-stu-id="81956-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81956-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="81956-112">Attributes and Elements</span></span>  
 <span data-ttu-id="81956-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="81956-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81956-114">屬性</span><span class="sxs-lookup"><span data-stu-id="81956-114">Attributes</span></span>  
 <span data-ttu-id="81956-115">無。</span><span class="sxs-lookup"><span data-stu-id="81956-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="81956-116">子項目</span><span class="sxs-lookup"><span data-stu-id="81956-116">Child Elements</span></span>  
  
|<span data-ttu-id="81956-117">項目</span><span class="sxs-lookup"><span data-stu-id="81956-117">Element</span></span>|<span data-ttu-id="81956-118">說明</span><span class="sxs-lookup"><span data-stu-id="81956-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81956-119">\<驗證 ></span><span class="sxs-lookup"><span data-stu-id="81956-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="81956-120">指定用戶端憑證的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="81956-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="81956-121">\<憑證 ></span><span class="sxs-lookup"><span data-stu-id="81956-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="81956-122">指定要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="81956-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81956-123">父項目</span><span class="sxs-lookup"><span data-stu-id="81956-123">Parent Elements</span></span>  
  
|<span data-ttu-id="81956-124">項目</span><span class="sxs-lookup"><span data-stu-id="81956-124">Element</span></span>|<span data-ttu-id="81956-125">說明</span><span class="sxs-lookup"><span data-stu-id="81956-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81956-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="81956-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="81956-127">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="81956-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81956-128">備註</span><span class="sxs-lookup"><span data-stu-id="81956-128">Remarks</span></span>  
 <span data-ttu-id="81956-129">當服務必須具有用戶端的憑證才能與用戶端安全地進行通訊時，則會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="81956-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="81956-130">這種情況發生在使用雙工通訊模式時。</span><span class="sxs-lookup"><span data-stu-id="81956-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="81956-131">在較為典型的要求/回應模式中，用戶端會在要求中納入其憑證，服務便使用此憑證加密與簽署其對於用戶端的回應。</span><span class="sxs-lookup"><span data-stu-id="81956-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="81956-132">然而，在雙工通訊模式中，服務沒有來自用戶端的要求，因此需要用戶端的憑證，進而保護傳送到用戶端的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="81956-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="81956-133">所以，您必須在超出範圍的交涉中取得用戶端的憑證，並使用此項目指定憑證。</span><span class="sxs-lookup"><span data-stu-id="81956-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="81956-134">如需雙工服務的詳細資訊，請參閱[How to： 建立雙工合約](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="81956-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="81956-135">設定在這個項目中的憑證，只能在繫結是以 `MutualCertificateDuplex` 訊息安全性驗證模式所設定的情況下，才可用來加密傳送給用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="81956-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81956-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81956-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="81956-137">如何： 建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="81956-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="81956-138">安全性行為</span><span class="sxs-lookup"><span data-stu-id="81956-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="81956-139">使用憑證</span><span class="sxs-lookup"><span data-stu-id="81956-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
