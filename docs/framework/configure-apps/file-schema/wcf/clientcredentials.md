---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 6094006df24ee824c419a783ab29d7604757577c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201456"
---
# \<clientCredentials>

<span data-ttu-id="3ba73-101">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="3ba73-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ba73-102">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ba73-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3ba73-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3ba73-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3ba73-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ba73-105">屬性</span><span class="sxs-lookup"><span data-stu-id="3ba73-105">Attributes</span></span>  
  
|<span data-ttu-id="3ba73-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3ba73-106">Attribute</span></span>|<span data-ttu-id="3ba73-107">描述</span><span class="sxs-lookup"><span data-stu-id="3ba73-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="3ba73-108">布林值，指定互動式使用者是否可以在執行階段選取用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="3ba73-109">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ba73-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="3ba73-110">字串，指定這個組態項目的型別。</span><span class="sxs-lookup"><span data-stu-id="3ba73-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ba73-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3ba73-111">Child Elements</span></span>  
  
|<span data-ttu-id="3ba73-112">項目</span><span class="sxs-lookup"><span data-stu-id="3ba73-112">Element</span></span>|<span data-ttu-id="3ba73-113">描述</span><span class="sxs-lookup"><span data-stu-id="3ba73-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="3ba73-114">指定用來對服務驗證用戶端的憑證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="3ba73-115">此項目的型別為 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="3ba73-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="3ba73-116">指定用來對服務驗證用戶端的摘要。</span><span class="sxs-lookup"><span data-stu-id="3ba73-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="3ba73-117">此項目的型別為 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>。</span><span class="sxs-lookup"><span data-stu-id="3ba73-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="3ba73-118">指定用來對安全性權杖服務 (STS) 驗證用戶端的自訂權杖型別。</span><span class="sxs-lookup"><span data-stu-id="3ba73-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="3ba73-119">此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>。</span><span class="sxs-lookup"><span data-stu-id="3ba73-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="3ba73-120">指定目前的對等認證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-120">Specifies a current peer credential.</span></span> <span data-ttu-id="3ba73-121">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="3ba73-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="3ba73-122">指定用來對用戶端驗證服務的憑證，並提供設定憑證選項的結構。</span><span class="sxs-lookup"><span data-stu-id="3ba73-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="3ba73-123">當超出服務至用戶端的範圍時，就必須提供此憑證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="3ba73-124">此項目的型別為 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="3ba73-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="3ba73-125">指定 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-125">Specifies a Windows credential.</span></span> <span data-ttu-id="3ba73-126">預設為目前執行緒的認證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="3ba73-127">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsClientElement>。</span><span class="sxs-lookup"><span data-stu-id="3ba73-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ba73-128">父項目</span><span class="sxs-lookup"><span data-stu-id="3ba73-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3ba73-129">項目</span><span class="sxs-lookup"><span data-stu-id="3ba73-129">Element</span></span>|<span data-ttu-id="3ba73-130">描述</span><span class="sxs-lookup"><span data-stu-id="3ba73-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3ba73-131">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="3ba73-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ba73-132">備註</span><span class="sxs-lookup"><span data-stu-id="3ba73-132">Remarks</span></span>  

 <span data-ttu-id="3ba73-133">在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="3ba73-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="3ba73-134">在用戶端必須以服務的憑證保護傳遞給服務的訊息時，這個組態區段也可以用來指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="3ba73-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba73-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ba73-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="3ba73-136">安全性行為</span><span class="sxs-lookup"><span data-stu-id="3ba73-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3ba73-137">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="3ba73-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
