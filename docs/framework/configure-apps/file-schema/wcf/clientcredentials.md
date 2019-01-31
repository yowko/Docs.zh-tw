---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 7ee49d6960864826dc74fbff629f502fcc70b4bf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254804"
---
# <a name="clientcredentials"></a><span data-ttu-id="8bbfa-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8bbfa-101">\<clientCredentials></span></span>
<span data-ttu-id="8bbfa-102">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="8bbfa-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8bbfa-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8bbfa-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="8bbfa-104">\<behaviors></span></span>  
<span data-ttu-id="8bbfa-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8bbfa-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="8bbfa-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8bbfa-106">\<behavior></span></span>  
<span data-ttu-id="8bbfa-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8bbfa-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bbfa-108">語法</span><span class="sxs-lookup"><span data-stu-id="8bbfa-108">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bbfa-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8bbfa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8bbfa-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bbfa-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8bbfa-111">Attributes</span></span>  
  
|<span data-ttu-id="8bbfa-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8bbfa-112">Attribute</span></span>|<span data-ttu-id="8bbfa-113">描述</span><span class="sxs-lookup"><span data-stu-id="8bbfa-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="8bbfa-114">布林值，指定互動式使用者是否可以在執行階段選取用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="8bbfa-115">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="8bbfa-116">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bbfa-117">子元素</span><span class="sxs-lookup"><span data-stu-id="8bbfa-117">Child Elements</span></span>  
  
|<span data-ttu-id="8bbfa-118">項目</span><span class="sxs-lookup"><span data-stu-id="8bbfa-118">Element</span></span>|<span data-ttu-id="8bbfa-119">描述</span><span class="sxs-lookup"><span data-stu-id="8bbfa-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bbfa-120">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="8bbfa-120">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="8bbfa-121">指定用來對服務驗證用戶端的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="8bbfa-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="8bbfa-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="8bbfa-123">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="8bbfa-124">指定用來對服務驗證用戶端的摘要。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="8bbfa-125">此項目的型別為 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="8bbfa-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="8bbfa-126">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="8bbfa-127">指定用來對安全性權杖服務 (STS) 驗證用戶端的自訂權杖型別。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="8bbfa-128">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="8bbfa-129">\<peer></span><span class="sxs-lookup"><span data-stu-id="8bbfa-129">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="8bbfa-130">指定目前的對等認證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-130">Specifies a current peer credential.</span></span> <span data-ttu-id="8bbfa-131">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="8bbfa-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="8bbfa-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="8bbfa-133">指定用來對用戶端驗證服務的憑證，並提供設定憑證選項的結構。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="8bbfa-134">當超出服務至用戶端的範圍時，就必須提供此憑證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="8bbfa-135">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="8bbfa-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="8bbfa-136">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="8bbfa-137">指定 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-137">Specifies a Windows credential.</span></span> <span data-ttu-id="8bbfa-138">預設為目前執行緒的認證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="8bbfa-139">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsClientElement>。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8bbfa-140">父項目</span><span class="sxs-lookup"><span data-stu-id="8bbfa-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8bbfa-141">項目</span><span class="sxs-lookup"><span data-stu-id="8bbfa-141">Element</span></span>|<span data-ttu-id="8bbfa-142">描述</span><span class="sxs-lookup"><span data-stu-id="8bbfa-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bbfa-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8bbfa-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8bbfa-144">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bbfa-145">備註</span><span class="sxs-lookup"><span data-stu-id="8bbfa-145">Remarks</span></span>  
 <span data-ttu-id="8bbfa-146">在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="8bbfa-147">在用戶端必須以服務的憑證保護傳遞給服務的訊息時，這個組態區段也可以用來指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8bbfa-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bbfa-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bbfa-148">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="8bbfa-149">安全性行為</span><span class="sxs-lookup"><span data-stu-id="8bbfa-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8bbfa-150">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="8bbfa-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
