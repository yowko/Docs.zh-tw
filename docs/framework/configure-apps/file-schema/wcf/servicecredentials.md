---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b5d257b3082717ba94b9a4517ed5ccd4bd325c06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936302"
---
# <a name="servicecredentials"></a><span data-ttu-id="f800c-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f800c-101">\<serviceCredentials></span></span>
<span data-ttu-id="f800c-102">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="f800c-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="f800c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f800c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f800c-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="f800c-104">\<behaviors></span></span>  
<span data-ttu-id="f800c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f800c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="f800c-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="f800c-106">\<behavior></span></span>  
<span data-ttu-id="f800c-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f800c-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f800c-108">語法</span><span class="sxs-lookup"><span data-stu-id="f800c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f800c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f800c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f800c-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f800c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f800c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f800c-111">Attributes</span></span>  
  
|<span data-ttu-id="f800c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f800c-112">Attribute</span></span>|<span data-ttu-id="f800c-113">說明</span><span class="sxs-lookup"><span data-stu-id="f800c-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="f800c-114">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="f800c-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f800c-115">子元素</span><span class="sxs-lookup"><span data-stu-id="f800c-115">Child Elements</span></span>  
  
|<span data-ttu-id="f800c-116">項目</span><span class="sxs-lookup"><span data-stu-id="f800c-116">Element</span></span>|<span data-ttu-id="f800c-117">描述</span><span class="sxs-lookup"><span data-stu-id="f800c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f800c-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="f800c-118">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="f800c-119">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="f800c-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="f800c-120">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="f800c-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="f800c-121">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="f800c-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="f800c-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="f800c-122">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="f800c-123">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="f800c-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="f800c-124">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="f800c-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="f800c-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="f800c-125">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="f800c-126">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="f800c-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="f800c-127">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="f800c-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="f800c-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="f800c-128">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="f800c-129">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="f800c-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="f800c-130">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="f800c-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="f800c-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="f800c-131">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="f800c-132">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="f800c-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="f800c-133">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="f800c-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="f800c-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="f800c-134">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="f800c-135">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="f800c-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="f800c-136">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="f800c-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="f800c-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="f800c-137">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="f800c-138">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="f800c-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="f800c-139">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="f800c-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f800c-140">父項目</span><span class="sxs-lookup"><span data-stu-id="f800c-140">Parent Elements</span></span>  
  
|<span data-ttu-id="f800c-141">項目</span><span class="sxs-lookup"><span data-stu-id="f800c-141">Element</span></span>|<span data-ttu-id="f800c-142">說明</span><span class="sxs-lookup"><span data-stu-id="f800c-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f800c-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f800c-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f800c-144">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="f800c-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f800c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f800c-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="f800c-146">安全性行為</span><span class="sxs-lookup"><span data-stu-id="f800c-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
