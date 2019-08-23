---
title: <security> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 5b74c95ef2933fcf7e8d49aed89d95acbd288b80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936701"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="9d7f7-102">\<msmqIntegrationBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="9d7f7-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="9d7f7-103">定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="9d7f7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9d7f7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d7f7-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9d7f7-105">\<bindings></span></span>  
<span data-ttu-id="9d7f7-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="9d7f7-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="9d7f7-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="9d7f7-107">\<binding></span></span>  
<span data-ttu-id="9d7f7-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="9d7f7-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7f7-109">語法</span><span class="sxs-lookup"><span data-stu-id="9d7f7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d7f7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9d7f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9d7f7-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d7f7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9d7f7-112">Attributes</span></span>  
  
|<span data-ttu-id="9d7f7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9d7f7-113">Attribute</span></span>|<span data-ttu-id="9d7f7-114">說明</span><span class="sxs-lookup"><span data-stu-id="9d7f7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d7f7-115">模式</span><span class="sxs-lookup"><span data-stu-id="9d7f7-115">mode</span></span>|<span data-ttu-id="9d7f7-116">指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="9d7f7-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="9d7f7-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9d7f7-118">無這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-118">-   None: This disables security.</span></span><br /><span data-ttu-id="9d7f7-119">運送傳輸會提供保護和驗證。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="9d7f7-120">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="9d7f7-121">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="9d7f7-122">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="9d7f7-123">預設值為 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-123">The default value is `Transport`.</span></span> <span data-ttu-id="9d7f7-124">此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d7f7-125">子元素</span><span class="sxs-lookup"><span data-stu-id="9d7f7-125">Child Elements</span></span>  
  
|<span data-ttu-id="9d7f7-126">項目</span><span class="sxs-lookup"><span data-stu-id="9d7f7-126">Element</span></span>|<span data-ttu-id="9d7f7-127">說明</span><span class="sxs-lookup"><span data-stu-id="9d7f7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d7f7-128">\<transport></span><span class="sxs-lookup"><span data-stu-id="9d7f7-128">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="9d7f7-129">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="9d7f7-130">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="9d7f7-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d7f7-131">父項目</span><span class="sxs-lookup"><span data-stu-id="9d7f7-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9d7f7-132">項目</span><span class="sxs-lookup"><span data-stu-id="9d7f7-132">Element</span></span>|<span data-ttu-id="9d7f7-133">描述</span><span class="sxs-lookup"><span data-stu-id="9d7f7-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d7f7-134">\<binding></span><span class="sxs-lookup"><span data-stu-id="9d7f7-134">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="9d7f7-135">MsmqIntegrationBinding > 的 binding 元素。 [ \< ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="9d7f7-135">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d7f7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d7f7-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="9d7f7-137">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="9d7f7-137">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="9d7f7-138">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="9d7f7-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9d7f7-139">繫結</span><span class="sxs-lookup"><span data-stu-id="9d7f7-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9d7f7-140">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="9d7f7-140">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9d7f7-141">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="9d7f7-141">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9d7f7-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="9d7f7-142">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="9d7f7-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="9d7f7-143">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
