---
title: '&lt;ServiceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b9e32509a5e182301455eaf0e602a03c51fbc23a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150769"
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="cae78-102">&lt;ServiceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="cae78-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="cae78-103">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="cae78-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="cae78-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cae78-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cae78-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cae78-105">\<behaviors></span></span>  
<span data-ttu-id="cae78-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cae78-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cae78-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cae78-107">\<behavior></span></span>  
<span data-ttu-id="cae78-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cae78-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae78-109">語法</span><span class="sxs-lookup"><span data-stu-id="cae78-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cae78-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cae78-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cae78-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cae78-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cae78-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cae78-112">Attributes</span></span>  
  
|<span data-ttu-id="cae78-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cae78-113">Attribute</span></span>|<span data-ttu-id="cae78-114">描述</span><span class="sxs-lookup"><span data-stu-id="cae78-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="cae78-115">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="cae78-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cae78-116">子元素</span><span class="sxs-lookup"><span data-stu-id="cae78-116">Child Elements</span></span>  
  
|<span data-ttu-id="cae78-117">項目</span><span class="sxs-lookup"><span data-stu-id="cae78-117">Element</span></span>|<span data-ttu-id="cae78-118">描述</span><span class="sxs-lookup"><span data-stu-id="cae78-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cae78-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="cae78-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="cae78-120">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="cae78-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="cae78-121">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="cae78-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="cae78-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="cae78-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="cae78-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="cae78-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="cae78-124">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="cae78-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="cae78-125">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="cae78-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="cae78-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="cae78-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="cae78-127">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="cae78-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="cae78-128">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="cae78-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="cae78-129">\<s ></span><span class="sxs-lookup"><span data-stu-id="cae78-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="cae78-130">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="cae78-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="cae78-131">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="cae78-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="cae78-132">\<v ></span><span class="sxs-lookup"><span data-stu-id="cae78-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="cae78-133">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="cae78-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="cae78-134">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="cae78-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="cae78-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="cae78-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="cae78-136">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="cae78-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="cae78-137">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="cae78-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="cae78-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="cae78-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="cae78-139">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="cae78-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="cae78-140">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="cae78-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cae78-141">父項目</span><span class="sxs-lookup"><span data-stu-id="cae78-141">Parent Elements</span></span>  
  
|<span data-ttu-id="cae78-142">項目</span><span class="sxs-lookup"><span data-stu-id="cae78-142">Element</span></span>|<span data-ttu-id="cae78-143">描述</span><span class="sxs-lookup"><span data-stu-id="cae78-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cae78-144">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cae78-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cae78-145">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="cae78-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cae78-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cae78-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="cae78-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="cae78-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
