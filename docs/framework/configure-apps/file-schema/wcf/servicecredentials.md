---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: d9f8fdf272962916cd08aede484e9bbde55b96a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670283"
---
# <a name="servicecredentials"></a><span data-ttu-id="965bd-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="965bd-101">\<serviceCredentials></span></span>
<span data-ttu-id="965bd-102">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="965bd-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="965bd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="965bd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="965bd-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="965bd-104">\<behaviors></span></span>  
<span data-ttu-id="965bd-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="965bd-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="965bd-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="965bd-106">\<behavior></span></span>  
<span data-ttu-id="965bd-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="965bd-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="965bd-108">語法</span><span class="sxs-lookup"><span data-stu-id="965bd-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="965bd-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="965bd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="965bd-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="965bd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="965bd-111">屬性</span><span class="sxs-lookup"><span data-stu-id="965bd-111">Attributes</span></span>  
  
|<span data-ttu-id="965bd-112">屬性</span><span class="sxs-lookup"><span data-stu-id="965bd-112">Attribute</span></span>|<span data-ttu-id="965bd-113">描述</span><span class="sxs-lookup"><span data-stu-id="965bd-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="965bd-114">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="965bd-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="965bd-115">子元素</span><span class="sxs-lookup"><span data-stu-id="965bd-115">Child Elements</span></span>  
  
|<span data-ttu-id="965bd-116">項目</span><span class="sxs-lookup"><span data-stu-id="965bd-116">Element</span></span>|<span data-ttu-id="965bd-117">描述</span><span class="sxs-lookup"><span data-stu-id="965bd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="965bd-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="965bd-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="965bd-119">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="965bd-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="965bd-120">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="965bd-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="965bd-121">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="965bd-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="965bd-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="965bd-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="965bd-123">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="965bd-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="965bd-124">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="965bd-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="965bd-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="965bd-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="965bd-126">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="965bd-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="965bd-127">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="965bd-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="965bd-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="965bd-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="965bd-129">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="965bd-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="965bd-130">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="965bd-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="965bd-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="965bd-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="965bd-132">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="965bd-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="965bd-133">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="965bd-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="965bd-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="965bd-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="965bd-135">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="965bd-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="965bd-136">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="965bd-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="965bd-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="965bd-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="965bd-138">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="965bd-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="965bd-139">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="965bd-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="965bd-140">父項目</span><span class="sxs-lookup"><span data-stu-id="965bd-140">Parent Elements</span></span>  
  
|<span data-ttu-id="965bd-141">項目</span><span class="sxs-lookup"><span data-stu-id="965bd-141">Element</span></span>|<span data-ttu-id="965bd-142">描述</span><span class="sxs-lookup"><span data-stu-id="965bd-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="965bd-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="965bd-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="965bd-144">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="965bd-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="965bd-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="965bd-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="965bd-146">安全性行為</span><span class="sxs-lookup"><span data-stu-id="965bd-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
