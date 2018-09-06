---
title: '&lt;msmqIntegrationBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6419c2157281d00cf79de16d4f494fc52bcee598
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43876728"
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="2a190-102">&lt;msmqIntegrationBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="2a190-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="2a190-103">定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2a190-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="2a190-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a190-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a190-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2a190-105">\<bindings></span></span>  
<span data-ttu-id="2a190-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="2a190-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="2a190-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2a190-107">\<binding></span></span>  
<span data-ttu-id="2a190-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="2a190-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a190-109">語法</span><span class="sxs-lookup"><span data-stu-id="2a190-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>  
   <binding>   
       <security mode="None/Transport">  
         <transport msmqAuthenticationMode="None/Windows/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                        clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
            defaultProtectionLevel="None/Sign/EncryptAndSign" />  
       </security>  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a190-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a190-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a190-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2a190-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a190-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2a190-112">Attributes</span></span>  
  
|<span data-ttu-id="2a190-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2a190-113">Attribute</span></span>|<span data-ttu-id="2a190-114">描述</span><span class="sxs-lookup"><span data-stu-id="2a190-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a190-115">模式</span><span class="sxs-lookup"><span data-stu-id="2a190-115">mode</span></span>|<span data-ttu-id="2a190-116">指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="2a190-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="2a190-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="2a190-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2a190-118">-None： 這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2a190-118">-   None: This disables security.</span></span><br /><span data-ttu-id="2a190-119">-傳輸： 保護和驗證是由傳輸提供。</span><span class="sxs-lookup"><span data-stu-id="2a190-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="2a190-120">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="2a190-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="2a190-121">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="2a190-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="2a190-122">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="2a190-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="2a190-123">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="2a190-123">The default value is `Transport`.</span></span> <span data-ttu-id="2a190-124">此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="2a190-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a190-125">子元素</span><span class="sxs-lookup"><span data-stu-id="2a190-125">Child Elements</span></span>  
  
|<span data-ttu-id="2a190-126">項目</span><span class="sxs-lookup"><span data-stu-id="2a190-126">Element</span></span>|<span data-ttu-id="2a190-127">描述</span><span class="sxs-lookup"><span data-stu-id="2a190-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a190-128">\<transport></span><span class="sxs-lookup"><span data-stu-id="2a190-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="2a190-129">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2a190-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="2a190-130">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="2a190-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a190-131">父項目</span><span class="sxs-lookup"><span data-stu-id="2a190-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2a190-132">項目</span><span class="sxs-lookup"><span data-stu-id="2a190-132">Element</span></span>|<span data-ttu-id="2a190-133">描述</span><span class="sxs-lookup"><span data-stu-id="2a190-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a190-134">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2a190-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2a190-135">繫結項目[ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="2a190-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a190-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a190-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="2a190-137">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="2a190-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="2a190-138">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2a190-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2a190-139">繫結</span><span class="sxs-lookup"><span data-stu-id="2a190-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2a190-140">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2a190-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2a190-141">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="2a190-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2a190-142">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2a190-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="2a190-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="2a190-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
