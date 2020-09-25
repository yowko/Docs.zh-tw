---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 63368355027856118546bc70183b41864eddb0e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172875"
---
# \<serviceCredentials>

<span data-ttu-id="d8b42-101">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="d8b42-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="d8b42-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8b42-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8b42-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8b42-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d8b42-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d8b42-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8b42-105">屬性</span><span class="sxs-lookup"><span data-stu-id="d8b42-105">Attributes</span></span>  
  
|<span data-ttu-id="d8b42-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d8b42-106">Attribute</span></span>|<span data-ttu-id="d8b42-107">描述</span><span class="sxs-lookup"><span data-stu-id="d8b42-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d8b42-108">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="d8b42-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8b42-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d8b42-109">Child Elements</span></span>  
  
|<span data-ttu-id="d8b42-110">項目</span><span class="sxs-lookup"><span data-stu-id="d8b42-110">Element</span></span>|<span data-ttu-id="d8b42-111">描述</span><span class="sxs-lookup"><span data-stu-id="d8b42-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="d8b42-112">指定當用戶端憑證可在超出範圍使用時，要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="d8b42-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="d8b42-113">這個項目也會指定用戶端憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="d8b42-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="d8b42-114">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d8b42-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="d8b42-115">指定這個服務的目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="d8b42-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="d8b42-116">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d8b42-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="d8b42-117">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="d8b42-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="d8b42-118">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="d8b42-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="d8b42-119">指定安全對話的目前認證。</span><span class="sxs-lookup"><span data-stu-id="d8b42-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="d8b42-120">此項目的型別為 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d8b42-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="d8b42-121">指定服務用來識別本身的憑證。</span><span class="sxs-lookup"><span data-stu-id="d8b42-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="d8b42-122">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d8b42-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="d8b42-123">指定使用者名稱密碼驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="d8b42-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="d8b42-124">此項目的型別為 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d8b42-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="d8b42-125">指定 Windows 認證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="d8b42-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="d8b42-126">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="d8b42-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8b42-127">父項目</span><span class="sxs-lookup"><span data-stu-id="d8b42-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d8b42-128">項目</span><span class="sxs-lookup"><span data-stu-id="d8b42-128">Element</span></span>|<span data-ttu-id="d8b42-129">描述</span><span class="sxs-lookup"><span data-stu-id="d8b42-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d8b42-130">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="d8b42-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8b42-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8b42-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="d8b42-132">安全性行為</span><span class="sxs-lookup"><span data-stu-id="d8b42-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
