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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8e2fa4fe72b7b4c2f421aefa566f89492c06457
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="1a861-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="1a861-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="1a861-103">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="1a861-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="1a861-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a861-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a861-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1a861-105">\<behaviors></span></span>  
<span data-ttu-id="1a861-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1a861-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1a861-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1a861-107">\<behavior></span></span>  
<span data-ttu-id="1a861-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1a861-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a861-109">語法</span><span class="sxs-lookup"><span data-stu-id="1a861-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a861-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1a861-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1a861-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1a861-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a861-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1a861-112">Attributes</span></span>  
  
|<span data-ttu-id="1a861-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1a861-113">Attribute</span></span>|<span data-ttu-id="1a861-114">描述</span><span class="sxs-lookup"><span data-stu-id="1a861-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="1a861-115">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="1a861-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a861-116">子元素</span><span class="sxs-lookup"><span data-stu-id="1a861-116">Child Elements</span></span>  
  
|<span data-ttu-id="1a861-117">項目</span><span class="sxs-lookup"><span data-stu-id="1a861-117">Element</span></span>|<span data-ttu-id="1a861-118">說明</span><span class="sxs-lookup"><span data-stu-id="1a861-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a861-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="1a861-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="1a861-120">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="1a861-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="1a861-121">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="1a861-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="1a861-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="1a861-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="1a861-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1a861-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="1a861-124">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="1a861-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="1a861-125">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="1a861-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="1a861-126">\<對等 ></span><span class="sxs-lookup"><span data-stu-id="1a861-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="1a861-127">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="1a861-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="1a861-128">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="1a861-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="1a861-129">\<s ></span><span class="sxs-lookup"><span data-stu-id="1a861-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="1a861-130">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="1a861-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="1a861-131">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="1a861-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="1a861-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="1a861-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="1a861-133">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="1a861-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="1a861-134">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="1a861-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="1a861-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1a861-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="1a861-136">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="1a861-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="1a861-137">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="1a861-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="1a861-138">\<windows 驗證 ></span><span class="sxs-lookup"><span data-stu-id="1a861-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="1a861-139">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="1a861-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="1a861-140">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="1a861-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a861-141">父項目</span><span class="sxs-lookup"><span data-stu-id="1a861-141">Parent Elements</span></span>  
  
|<span data-ttu-id="1a861-142">項目</span><span class="sxs-lookup"><span data-stu-id="1a861-142">Element</span></span>|<span data-ttu-id="1a861-143">說明</span><span class="sxs-lookup"><span data-stu-id="1a861-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a861-144">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1a861-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1a861-145">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="1a861-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a861-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a861-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="1a861-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="1a861-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
