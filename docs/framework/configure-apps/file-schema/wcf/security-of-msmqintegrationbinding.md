---
title: <security> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 2268bf48a2b86c3b3b25db006e6f8f55ea33af73
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738689"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="59630-102">\<security> 的 \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="59630-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="59630-103">定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="59630-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="59630-104">語法</span><span class="sxs-lookup"><span data-stu-id="59630-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59630-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="59630-105">Attributes and Elements</span></span>  
 <span data-ttu-id="59630-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="59630-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59630-107">屬性</span><span class="sxs-lookup"><span data-stu-id="59630-107">Attributes</span></span>  
  
|<span data-ttu-id="59630-108">屬性</span><span class="sxs-lookup"><span data-stu-id="59630-108">Attribute</span></span>|<span data-ttu-id="59630-109">描述</span><span class="sxs-lookup"><span data-stu-id="59630-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59630-110">mode</span><span class="sxs-lookup"><span data-stu-id="59630-110">mode</span></span>|<span data-ttu-id="59630-111">指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="59630-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="59630-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="59630-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="59630-113">-None：這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="59630-113">-   None: This disables security.</span></span><br /><span data-ttu-id="59630-114">-Transport：保護和驗證是由傳輸所提供。</span><span class="sxs-lookup"><span data-stu-id="59630-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="59630-115">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="59630-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="59630-116">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="59630-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="59630-117">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="59630-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="59630-118">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="59630-118">The default value is `Transport`.</span></span> <span data-ttu-id="59630-119">此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="59630-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59630-120">子元素</span><span class="sxs-lookup"><span data-stu-id="59630-120">Child Elements</span></span>  
  
|<span data-ttu-id="59630-121">元素</span><span class="sxs-lookup"><span data-stu-id="59630-121">Element</span></span>|<span data-ttu-id="59630-122">描述</span><span class="sxs-lookup"><span data-stu-id="59630-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="59630-123">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="59630-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="59630-124">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="59630-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59630-125">父項目</span><span class="sxs-lookup"><span data-stu-id="59630-125">Parent Elements</span></span>  
  
|<span data-ttu-id="59630-126">元素</span><span class="sxs-lookup"><span data-stu-id="59630-126">Element</span></span>|<span data-ttu-id="59630-127">描述</span><span class="sxs-lookup"><span data-stu-id="59630-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="59630-128">的繫結項目 [\<msmqIntegrationBinding>](msmqintegrationbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="59630-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59630-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59630-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="59630-130">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="59630-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="59630-131">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="59630-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="59630-132">繫結</span><span class="sxs-lookup"><span data-stu-id="59630-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59630-133">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="59630-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="59630-134">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="59630-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
