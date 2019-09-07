---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399662"
---
# <a name="servicecredentials"></a><span data-ttu-id="90d07-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="90d07-101">\<serviceCredentials></span></span>
<span data-ttu-id="90d07-102">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="90d07-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
<span data-ttu-id="90d07-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="90d07-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="90d07-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="90d07-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="90d07-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="90d07-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="90d07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="90d07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="90d07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="90d07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="90d07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCredentials >**</span><span class="sxs-lookup"><span data-stu-id="90d07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d07-109">語法</span><span class="sxs-lookup"><span data-stu-id="90d07-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90d07-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90d07-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90d07-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="90d07-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90d07-112">屬性</span><span class="sxs-lookup"><span data-stu-id="90d07-112">Attributes</span></span>  
  
|<span data-ttu-id="90d07-113">屬性</span><span class="sxs-lookup"><span data-stu-id="90d07-113">Attribute</span></span>|<span data-ttu-id="90d07-114">說明</span><span class="sxs-lookup"><span data-stu-id="90d07-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="90d07-115">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="90d07-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90d07-116">子元素</span><span class="sxs-lookup"><span data-stu-id="90d07-116">Child Elements</span></span>  
  
|<span data-ttu-id="90d07-117">項目</span><span class="sxs-lookup"><span data-stu-id="90d07-117">Element</span></span>|<span data-ttu-id="90d07-118">描述</span><span class="sxs-lookup"><span data-stu-id="90d07-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90d07-119">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="90d07-119">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="90d07-120">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="90d07-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="90d07-121">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="90d07-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="90d07-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="90d07-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="90d07-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="90d07-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="90d07-124">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="90d07-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="90d07-125">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="90d07-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="90d07-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="90d07-126">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="90d07-127">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="90d07-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="90d07-128">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="90d07-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="90d07-129">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="90d07-129">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="90d07-130">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="90d07-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="90d07-131">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="90d07-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="90d07-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="90d07-132">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="90d07-133">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="90d07-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="90d07-134">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="90d07-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="90d07-135">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="90d07-135">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="90d07-136">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="90d07-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="90d07-137">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="90d07-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="90d07-138">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="90d07-138">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="90d07-139">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="90d07-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="90d07-140">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="90d07-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90d07-141">父項目</span><span class="sxs-lookup"><span data-stu-id="90d07-141">Parent Elements</span></span>  
  
|<span data-ttu-id="90d07-142">項目</span><span class="sxs-lookup"><span data-stu-id="90d07-142">Element</span></span>|<span data-ttu-id="90d07-143">描述</span><span class="sxs-lookup"><span data-stu-id="90d07-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90d07-144">\<behavior></span><span class="sxs-lookup"><span data-stu-id="90d07-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="90d07-145">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="90d07-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90d07-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90d07-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="90d07-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="90d07-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
