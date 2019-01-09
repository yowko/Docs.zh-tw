---
title: '&lt;ClientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 3f70a4e6e27507c3820e1b67f49664e538ac736f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145741"
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="9d540-102">&lt;ClientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="9d540-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="9d540-103">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="9d540-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="9d540-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9d540-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d540-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="9d540-105">\<behaviors></span></span>  
<span data-ttu-id="9d540-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="9d540-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="9d540-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="9d540-107">\<behavior></span></span>  
<span data-ttu-id="9d540-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="9d540-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d540-109">語法</span><span class="sxs-lookup"><span data-stu-id="9d540-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d540-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9d540-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9d540-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9d540-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d540-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9d540-112">Attributes</span></span>  
  
|<span data-ttu-id="9d540-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9d540-113">Attribute</span></span>|<span data-ttu-id="9d540-114">描述</span><span class="sxs-lookup"><span data-stu-id="9d540-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="9d540-115">布林值，指定互動式使用者是否可以在執行階段選取用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="9d540-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="9d540-116">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="9d540-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="9d540-117">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="9d540-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d540-118">子元素</span><span class="sxs-lookup"><span data-stu-id="9d540-118">Child Elements</span></span>  
  
|<span data-ttu-id="9d540-119">項目</span><span class="sxs-lookup"><span data-stu-id="9d540-119">Element</span></span>|<span data-ttu-id="9d540-120">描述</span><span class="sxs-lookup"><span data-stu-id="9d540-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d540-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="9d540-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="9d540-122">指定用來對服務驗證用戶端的憑證。</span><span class="sxs-lookup"><span data-stu-id="9d540-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="9d540-123">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="9d540-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="9d540-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="9d540-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="9d540-125">指定用來對服務驗證用戶端的摘要。</span><span class="sxs-lookup"><span data-stu-id="9d540-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="9d540-126">此項目的型別為 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>。</span><span class="sxs-lookup"><span data-stu-id="9d540-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="9d540-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="9d540-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="9d540-128">指定用來對安全性權杖服務 (STS) 驗證用戶端的自訂權杖型別。</span><span class="sxs-lookup"><span data-stu-id="9d540-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="9d540-129">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>。</span><span class="sxs-lookup"><span data-stu-id="9d540-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="9d540-130">\<peer></span><span class="sxs-lookup"><span data-stu-id="9d540-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="9d540-131">指定目前的對等認證。</span><span class="sxs-lookup"><span data-stu-id="9d540-131">Specifies a current peer credential.</span></span> <span data-ttu-id="9d540-132">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="9d540-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="9d540-133">\<v ></span><span class="sxs-lookup"><span data-stu-id="9d540-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="9d540-134">指定用來對用戶端驗證服務的憑證，並提供設定憑證選項的結構。</span><span class="sxs-lookup"><span data-stu-id="9d540-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="9d540-135">當超出服務至用戶端的範圍時，就必須提供此憑證。</span><span class="sxs-lookup"><span data-stu-id="9d540-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="9d540-136">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="9d540-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="9d540-137">\<windows ></span><span class="sxs-lookup"><span data-stu-id="9d540-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="9d540-138">指定 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="9d540-138">Specifies a Windows credential.</span></span> <span data-ttu-id="9d540-139">預設為目前執行緒的認證。</span><span class="sxs-lookup"><span data-stu-id="9d540-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="9d540-140">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsClientElement>。</span><span class="sxs-lookup"><span data-stu-id="9d540-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d540-141">父項目</span><span class="sxs-lookup"><span data-stu-id="9d540-141">Parent Elements</span></span>  
  
|<span data-ttu-id="9d540-142">項目</span><span class="sxs-lookup"><span data-stu-id="9d540-142">Element</span></span>|<span data-ttu-id="9d540-143">描述</span><span class="sxs-lookup"><span data-stu-id="9d540-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d540-144">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="9d540-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9d540-145">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="9d540-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d540-146">備註</span><span class="sxs-lookup"><span data-stu-id="9d540-146">Remarks</span></span>  
 <span data-ttu-id="9d540-147">在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="9d540-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="9d540-148">在用戶端必須以服務的憑證保護傳遞給服務的訊息時，這個組態區段也可以用來指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="9d540-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d540-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d540-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="9d540-150">安全性行為</span><span class="sxs-lookup"><span data-stu-id="9d540-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="9d540-151">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="9d540-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
