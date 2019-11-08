---
title: <security> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 2268bf48a2b86c3b3b25db006e6f8f55ea33af73
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738689"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="ab019-102">\<msmqIntegrationBinding 的 \<安全性 > ></span><span class="sxs-lookup"><span data-stu-id="ab019-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="ab019-103">定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ab019-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
<span data-ttu-id="ab019-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab019-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ab019-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ab019-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ab019-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="ab019-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ab019-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<msmqIntegrationBinding >** ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ab019-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="ab019-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="ab019-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ab019-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="ab019-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab019-110">語法</span><span class="sxs-lookup"><span data-stu-id="ab019-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab019-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab019-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ab019-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ab019-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab019-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ab019-113">Attributes</span></span>  
  
|<span data-ttu-id="ab019-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ab019-114">Attribute</span></span>|<span data-ttu-id="ab019-115">描述</span><span class="sxs-lookup"><span data-stu-id="ab019-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab019-116">模式</span><span class="sxs-lookup"><span data-stu-id="ab019-116">mode</span></span>|<span data-ttu-id="ab019-117">指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="ab019-117">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="ab019-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ab019-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ab019-119">-None：這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="ab019-119">-   None: This disables security.</span></span><br /><span data-ttu-id="ab019-120">-Transport：保護和驗證是由傳輸所提供。</span><span class="sxs-lookup"><span data-stu-id="ab019-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="ab019-121">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="ab019-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="ab019-122">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="ab019-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="ab019-123">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="ab019-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="ab019-124">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="ab019-124">The default value is `Transport`.</span></span> <span data-ttu-id="ab019-125">此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="ab019-125">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab019-126">子項目</span><span class="sxs-lookup"><span data-stu-id="ab019-126">Child Elements</span></span>  
  
|<span data-ttu-id="ab019-127">項目</span><span class="sxs-lookup"><span data-stu-id="ab019-127">Element</span></span>|<span data-ttu-id="ab019-128">描述</span><span class="sxs-lookup"><span data-stu-id="ab019-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab019-129">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="ab019-129">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="ab019-130">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ab019-130">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="ab019-131">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="ab019-131">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab019-132">父項目</span><span class="sxs-lookup"><span data-stu-id="ab019-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ab019-133">項目</span><span class="sxs-lookup"><span data-stu-id="ab019-133">Element</span></span>|<span data-ttu-id="ab019-134">描述</span><span class="sxs-lookup"><span data-stu-id="ab019-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab019-135">\<binding ></span><span class="sxs-lookup"><span data-stu-id="ab019-135">\<binding></span></span>](bindings.md)|<span data-ttu-id="ab019-136">[\<msmqIntegrationBinding >](msmqintegrationbinding.md)的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="ab019-136">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab019-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab019-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="ab019-138">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="ab019-138">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="ab019-139">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ab019-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ab019-140">繫結</span><span class="sxs-lookup"><span data-stu-id="ab019-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ab019-141">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="ab019-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ab019-142">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="ab019-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ab019-143">\<binding ></span><span class="sxs-lookup"><span data-stu-id="ab019-143">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="ab019-144">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="ab019-144">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
