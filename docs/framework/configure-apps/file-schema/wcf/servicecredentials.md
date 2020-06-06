---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399662"
---
# \<serviceCredentials>
<span data-ttu-id="d7424-101">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="d7424-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="d7424-102">語法</span><span class="sxs-lookup"><span data-stu-id="d7424-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7424-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7424-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d7424-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d7424-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7424-105">屬性</span><span class="sxs-lookup"><span data-stu-id="d7424-105">Attributes</span></span>  
  
|<span data-ttu-id="d7424-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d7424-106">Attribute</span></span>|<span data-ttu-id="d7424-107">描述</span><span class="sxs-lookup"><span data-stu-id="d7424-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d7424-108">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="d7424-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7424-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d7424-109">Child Elements</span></span>  
  
|<span data-ttu-id="d7424-110">元素</span><span class="sxs-lookup"><span data-stu-id="d7424-110">Element</span></span>|<span data-ttu-id="d7424-111">描述</span><span class="sxs-lookup"><span data-stu-id="d7424-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="d7424-112">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="d7424-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="d7424-113">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="d7424-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="d7424-114">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d7424-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="d7424-115">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="d7424-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="d7424-116">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d7424-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="d7424-117">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="d7424-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="d7424-118">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="d7424-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="d7424-119">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="d7424-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="d7424-120">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d7424-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="d7424-121">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="d7424-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="d7424-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d7424-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="d7424-123">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="d7424-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="d7424-124">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d7424-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="d7424-125">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="d7424-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="d7424-126">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d7424-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7424-127">父項目</span><span class="sxs-lookup"><span data-stu-id="d7424-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d7424-128">元素</span><span class="sxs-lookup"><span data-stu-id="d7424-128">Element</span></span>|<span data-ttu-id="d7424-129">描述</span><span class="sxs-lookup"><span data-stu-id="d7424-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d7424-130">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="d7424-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7424-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7424-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="d7424-132">安全性行為</span><span class="sxs-lookup"><span data-stu-id="d7424-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
