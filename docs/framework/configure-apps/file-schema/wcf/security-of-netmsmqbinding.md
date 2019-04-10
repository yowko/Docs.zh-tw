---
title: <security> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: acb4d04663d841a9b494153caa180855959c145e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206508"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="e31de-102">\<安全性 > 的\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="e31de-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="e31de-103">定義 MSMQ 繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e31de-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="e31de-104">它指定是否啟用傳輸或 SOAP 安全性，以及如果啟用，正在使用的驗證模式和保護層級。</span><span class="sxs-lookup"><span data-stu-id="e31de-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="e31de-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e31de-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e31de-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e31de-106">\<bindings></span></span>  
<span data-ttu-id="e31de-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="e31de-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="e31de-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="e31de-108">\<binding></span></span>  
<span data-ttu-id="e31de-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="e31de-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31de-110">語法</span><span class="sxs-lookup"><span data-stu-id="e31de-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e31de-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e31de-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e31de-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e31de-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e31de-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e31de-113">Attributes</span></span>  
  
|<span data-ttu-id="e31de-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e31de-114">Attribute</span></span>|<span data-ttu-id="e31de-115">描述</span><span class="sxs-lookup"><span data-stu-id="e31de-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e31de-116">模式</span><span class="sxs-lookup"><span data-stu-id="e31de-116">mode</span></span>|<span data-ttu-id="e31de-117">指定負責控制完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="e31de-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="e31de-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="e31de-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e31de-119">-None:這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="e31de-119">-   None: This disables security.</span></span><br /><span data-ttu-id="e31de-120">-傳輸：保護和驗證是由傳輸提供。</span><span class="sxs-lookup"><span data-stu-id="e31de-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="e31de-121">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="e31de-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="e31de-122">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="e31de-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="e31de-123">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="e31de-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="e31de-124">訊息：指定端應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="e31de-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="e31de-125">在傳輸層沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="e31de-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="e31de-126">這與其他標準繫結程序提供的安全性類似。</span><span class="sxs-lookup"><span data-stu-id="e31de-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="e31de-127">-兩者：提供傳輸和 SOAP 訊息層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="e31de-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="e31de-128">這兩個層級需要相同的認證。</span><span class="sxs-lookup"><span data-stu-id="e31de-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="e31de-129">預設值為 Transport。</span><span class="sxs-lookup"><span data-stu-id="e31de-129">The default value is Transport.</span></span> <span data-ttu-id="e31de-130">此屬性的型別為 <xref:System.ServiceModel.NetMsmqSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="e31de-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e31de-131">子元素</span><span class="sxs-lookup"><span data-stu-id="e31de-131">Child Elements</span></span>  
  
|<span data-ttu-id="e31de-132">項目</span><span class="sxs-lookup"><span data-stu-id="e31de-132">Element</span></span>|<span data-ttu-id="e31de-133">描述</span><span class="sxs-lookup"><span data-stu-id="e31de-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e31de-134">\<message></span><span class="sxs-lookup"><span data-stu-id="e31de-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="e31de-135">定義 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e31de-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="e31de-136">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>。</span><span class="sxs-lookup"><span data-stu-id="e31de-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="e31de-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="e31de-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="e31de-138">定義 MSMQ 傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e31de-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="e31de-139">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="e31de-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e31de-140">父項目</span><span class="sxs-lookup"><span data-stu-id="e31de-140">Parent Elements</span></span>  
  
|<span data-ttu-id="e31de-141">項目</span><span class="sxs-lookup"><span data-stu-id="e31de-141">Element</span></span>|<span data-ttu-id="e31de-142">描述</span><span class="sxs-lookup"><span data-stu-id="e31de-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e31de-143">繫結</span><span class="sxs-lookup"><span data-stu-id="e31de-143">binding</span></span>|<span data-ttu-id="e31de-144">繫結項目[ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e31de-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e31de-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e31de-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="e31de-146">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="e31de-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e31de-147">繫結</span><span class="sxs-lookup"><span data-stu-id="e31de-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e31de-148">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e31de-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e31de-149">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e31de-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e31de-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="e31de-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="e31de-151">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="e31de-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
