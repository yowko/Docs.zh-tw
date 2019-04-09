---
title: <security> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125784"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="c8e8f-102">\<安全性 > 的\<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="c8e8f-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="c8e8f-103">定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="c8e8f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c8e8f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c8e8f-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c8e8f-105">\<bindings></span></span>  
<span data-ttu-id="c8e8f-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="c8e8f-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="c8e8f-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="c8e8f-107">\<binding></span></span>  
<span data-ttu-id="c8e8f-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="c8e8f-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e8f-109">語法</span><span class="sxs-lookup"><span data-stu-id="c8e8f-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8e8f-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c8e8f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c8e8f-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8e8f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c8e8f-112">Attributes</span></span>  
  
|<span data-ttu-id="c8e8f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c8e8f-113">Attribute</span></span>|<span data-ttu-id="c8e8f-114">描述</span><span class="sxs-lookup"><span data-stu-id="c8e8f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8e8f-115">模式</span><span class="sxs-lookup"><span data-stu-id="c8e8f-115">mode</span></span>|<span data-ttu-id="c8e8f-116">指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="c8e8f-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="c8e8f-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c8e8f-118">-None:這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-118">-   None: This disables security.</span></span><br /><span data-ttu-id="c8e8f-119">-傳輸：保護和驗證是由傳輸提供。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="c8e8f-120">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="c8e8f-121">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="c8e8f-122">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="c8e8f-123">預設值為 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-123">The default value is `Transport`.</span></span> <span data-ttu-id="c8e8f-124">此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8e8f-125">子元素</span><span class="sxs-lookup"><span data-stu-id="c8e8f-125">Child Elements</span></span>  
  
|<span data-ttu-id="c8e8f-126">項目</span><span class="sxs-lookup"><span data-stu-id="c8e8f-126">Element</span></span>|<span data-ttu-id="c8e8f-127">描述</span><span class="sxs-lookup"><span data-stu-id="c8e8f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8e8f-128">\<transport></span><span class="sxs-lookup"><span data-stu-id="c8e8f-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="c8e8f-129">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="c8e8f-130">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8e8f-131">父項目</span><span class="sxs-lookup"><span data-stu-id="c8e8f-131">Parent Elements</span></span>  
  
|<span data-ttu-id="c8e8f-132">項目</span><span class="sxs-lookup"><span data-stu-id="c8e8f-132">Element</span></span>|<span data-ttu-id="c8e8f-133">描述</span><span class="sxs-lookup"><span data-stu-id="c8e8f-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8e8f-134">\<binding></span><span class="sxs-lookup"><span data-stu-id="c8e8f-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c8e8f-135">繫結項目[ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c8e8f-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8e8f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8e8f-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="c8e8f-137">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="c8e8f-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="c8e8f-138">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="c8e8f-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c8e8f-139">繫結</span><span class="sxs-lookup"><span data-stu-id="c8e8f-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c8e8f-140">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="c8e8f-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c8e8f-141">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="c8e8f-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c8e8f-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="c8e8f-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="c8e8f-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="c8e8f-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
