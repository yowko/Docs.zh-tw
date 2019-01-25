---
title: '&lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 978439dfeb0c5275e2ec43f9c891b6927e7a7869
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610431"
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="4e198-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="4e198-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="4e198-103">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="4e198-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="4e198-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e198-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e198-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="4e198-105">\<behaviors></span></span>  
<span data-ttu-id="4e198-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4e198-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4e198-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4e198-107">\<behavior></span></span>  
<span data-ttu-id="4e198-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="4e198-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e198-109">語法</span><span class="sxs-lookup"><span data-stu-id="4e198-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e198-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e198-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4e198-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4e198-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e198-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4e198-112">Attributes</span></span>  
  
|<span data-ttu-id="4e198-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4e198-113">Attribute</span></span>|<span data-ttu-id="4e198-114">描述</span><span class="sxs-lookup"><span data-stu-id="4e198-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="4e198-115">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="4e198-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e198-116">子元素</span><span class="sxs-lookup"><span data-stu-id="4e198-116">Child Elements</span></span>  
  
|<span data-ttu-id="4e198-117">項目</span><span class="sxs-lookup"><span data-stu-id="4e198-117">Element</span></span>|<span data-ttu-id="4e198-118">描述</span><span class="sxs-lookup"><span data-stu-id="4e198-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e198-119">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="4e198-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="4e198-120">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="4e198-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="4e198-121">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="4e198-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="4e198-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="4e198-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="4e198-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="4e198-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="4e198-124">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="4e198-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="4e198-125">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="4e198-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="4e198-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="4e198-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="4e198-127">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="4e198-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="4e198-128">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="4e198-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="4e198-129">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="4e198-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="4e198-130">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="4e198-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="4e198-131">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="4e198-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="4e198-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4e198-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="4e198-133">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="4e198-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="4e198-134">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="4e198-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="4e198-135">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="4e198-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="4e198-136">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="4e198-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="4e198-137">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="4e198-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="4e198-138">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="4e198-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="4e198-139">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="4e198-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="4e198-140">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="4e198-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e198-141">父項目</span><span class="sxs-lookup"><span data-stu-id="4e198-141">Parent Elements</span></span>  
  
|<span data-ttu-id="4e198-142">項目</span><span class="sxs-lookup"><span data-stu-id="4e198-142">Element</span></span>|<span data-ttu-id="4e198-143">描述</span><span class="sxs-lookup"><span data-stu-id="4e198-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e198-144">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4e198-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4e198-145">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="4e198-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e198-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e198-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="4e198-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="4e198-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
