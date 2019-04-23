---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: d9f8fdf272962916cd08aede484e9bbde55b96a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227076"
---
# <a name="servicecredentials"></a><span data-ttu-id="a8043-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a8043-101">\<serviceCredentials></span></span>
<span data-ttu-id="a8043-102">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="a8043-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="a8043-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a8043-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8043-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="a8043-104">\<behaviors></span></span>  
<span data-ttu-id="a8043-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a8043-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a8043-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a8043-106">\<behavior></span></span>  
<span data-ttu-id="a8043-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a8043-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8043-108">語法</span><span class="sxs-lookup"><span data-stu-id="a8043-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8043-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8043-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a8043-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a8043-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8043-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a8043-111">Attributes</span></span>  
  
|<span data-ttu-id="a8043-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a8043-112">Attribute</span></span>|<span data-ttu-id="a8043-113">描述</span><span class="sxs-lookup"><span data-stu-id="a8043-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a8043-114">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="a8043-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8043-115">子元素</span><span class="sxs-lookup"><span data-stu-id="a8043-115">Child Elements</span></span>  
  
|<span data-ttu-id="a8043-116">項目</span><span class="sxs-lookup"><span data-stu-id="a8043-116">Element</span></span>|<span data-ttu-id="a8043-117">描述</span><span class="sxs-lookup"><span data-stu-id="a8043-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8043-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="a8043-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="a8043-119">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="a8043-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="a8043-120">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="a8043-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="a8043-121">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="a8043-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="a8043-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="a8043-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="a8043-123">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="a8043-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="a8043-124">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="a8043-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="a8043-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="a8043-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="a8043-126">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="a8043-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="a8043-127">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="a8043-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="a8043-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="a8043-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="a8043-129">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="a8043-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="a8043-130">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="a8043-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="a8043-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a8043-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="a8043-132">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="a8043-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="a8043-133">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="a8043-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="a8043-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="a8043-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="a8043-135">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="a8043-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="a8043-136">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="a8043-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="a8043-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="a8043-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="a8043-138">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="a8043-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="a8043-139">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="a8043-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8043-140">父項目</span><span class="sxs-lookup"><span data-stu-id="a8043-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a8043-141">項目</span><span class="sxs-lookup"><span data-stu-id="a8043-141">Element</span></span>|<span data-ttu-id="a8043-142">描述</span><span class="sxs-lookup"><span data-stu-id="a8043-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8043-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a8043-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a8043-144">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="a8043-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8043-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8043-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="a8043-146">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a8043-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
