---
title: '&lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bef277ebd2bd80d51380ae9786b290e7d05a0f0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="69a14-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="69a14-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="69a14-103">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="69a14-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="69a14-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="69a14-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69a14-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="69a14-105">\<behaviors></span></span>  
<span data-ttu-id="69a14-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="69a14-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="69a14-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="69a14-107">\<behavior></span></span>  
<span data-ttu-id="69a14-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="69a14-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a14-109">語法</span><span class="sxs-lookup"><span data-stu-id="69a14-109">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">  
   <clientCertificate>  
   </clientCertificate>  
   <issuedTokenAuthentication>  
   </issuedTokenAuthentication>  
   <peer>  
   </peer>  
   <secureConversationAuthentication>  
   </secureConversationAuthentication>  
   <serviceCertificate>  
   </serviceCertificate>  
   <userNameAuthentication>  
   </userNameAuthentication>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</serviceCredentials>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69a14-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="69a14-110">Attributes and Elements</span></span>  
 <span data-ttu-id="69a14-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="69a14-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69a14-112">屬性</span><span class="sxs-lookup"><span data-stu-id="69a14-112">Attributes</span></span>  
  
|<span data-ttu-id="69a14-113">屬性</span><span class="sxs-lookup"><span data-stu-id="69a14-113">Attribute</span></span>|<span data-ttu-id="69a14-114">描述</span><span class="sxs-lookup"><span data-stu-id="69a14-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="69a14-115">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="69a14-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69a14-116">子元素</span><span class="sxs-lookup"><span data-stu-id="69a14-116">Child Elements</span></span>  
  
|<span data-ttu-id="69a14-117">項目</span><span class="sxs-lookup"><span data-stu-id="69a14-117">Element</span></span>|<span data-ttu-id="69a14-118">說明</span><span class="sxs-lookup"><span data-stu-id="69a14-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69a14-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="69a14-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="69a14-120">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="69a14-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="69a14-121">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="69a14-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="69a14-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="69a14-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="69a14-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="69a14-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="69a14-124">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="69a14-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="69a14-125">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="69a14-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="69a14-126">\<對等 ></span><span class="sxs-lookup"><span data-stu-id="69a14-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="69a14-127">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="69a14-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="69a14-128">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="69a14-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="69a14-129">\<s ></span><span class="sxs-lookup"><span data-stu-id="69a14-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="69a14-130">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="69a14-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="69a14-131">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="69a14-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="69a14-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="69a14-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="69a14-133">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="69a14-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="69a14-134">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="69a14-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="69a14-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="69a14-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="69a14-136">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="69a14-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="69a14-137">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="69a14-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="69a14-138">\<windows 驗證 ></span><span class="sxs-lookup"><span data-stu-id="69a14-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="69a14-139">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="69a14-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="69a14-140">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="69a14-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69a14-141">父項目</span><span class="sxs-lookup"><span data-stu-id="69a14-141">Parent Elements</span></span>  
  
|<span data-ttu-id="69a14-142">項目</span><span class="sxs-lookup"><span data-stu-id="69a14-142">Element</span></span>|<span data-ttu-id="69a14-143">說明</span><span class="sxs-lookup"><span data-stu-id="69a14-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69a14-144">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="69a14-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="69a14-145">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="69a14-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69a14-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69a14-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="69a14-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="69a14-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
