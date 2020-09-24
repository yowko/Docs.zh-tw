---
title: <security> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: be2f48f7d9c3be4ea0a5fe95436930b3f23c7551
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170060"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="53da7-102">\<security> 的 \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="53da7-102">\<security> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="53da7-103">定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="53da7-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="53da7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="53da7-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53da7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="53da7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="53da7-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="53da7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53da7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="53da7-107">Attributes</span></span>  
  
|<span data-ttu-id="53da7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="53da7-108">Attribute</span></span>|<span data-ttu-id="53da7-109">描述</span><span class="sxs-lookup"><span data-stu-id="53da7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53da7-110">mode</span><span class="sxs-lookup"><span data-stu-id="53da7-110">mode</span></span>|<span data-ttu-id="53da7-111">指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="53da7-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="53da7-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="53da7-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="53da7-113">-None：這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="53da7-113">-   None: This disables security.</span></span><br /><span data-ttu-id="53da7-114">-Transport：傳輸提供保護和驗證。</span><span class="sxs-lookup"><span data-stu-id="53da7-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="53da7-115">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="53da7-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="53da7-116">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="53da7-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="53da7-117">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="53da7-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="53da7-118">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="53da7-118">The default value is `Transport`.</span></span> <span data-ttu-id="53da7-119">此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="53da7-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53da7-120">子元素</span><span class="sxs-lookup"><span data-stu-id="53da7-120">Child Elements</span></span>  
  
|<span data-ttu-id="53da7-121">項目</span><span class="sxs-lookup"><span data-stu-id="53da7-121">Element</span></span>|<span data-ttu-id="53da7-122">描述</span><span class="sxs-lookup"><span data-stu-id="53da7-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="53da7-123">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="53da7-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="53da7-124">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="53da7-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53da7-125">父項目</span><span class="sxs-lookup"><span data-stu-id="53da7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="53da7-126">項目</span><span class="sxs-lookup"><span data-stu-id="53da7-126">Element</span></span>|<span data-ttu-id="53da7-127">描述</span><span class="sxs-lookup"><span data-stu-id="53da7-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="53da7-128">的繫結項目 [\<msmqIntegrationBinding>](msmqintegrationbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="53da7-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53da7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53da7-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="53da7-130">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="53da7-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="53da7-131">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="53da7-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="53da7-132">繫結</span><span class="sxs-lookup"><span data-stu-id="53da7-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="53da7-133">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="53da7-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="53da7-134">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="53da7-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
