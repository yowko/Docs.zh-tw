---
title: '&lt;msmqIntegrationBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 574c0d7cba88f724143e642da13cace8c329dea6
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50039685"
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="549a5-102">&lt;msmqIntegrationBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="549a5-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="549a5-103">定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="549a5-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="549a5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="549a5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="549a5-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="549a5-105">\<bindings></span></span>  
<span data-ttu-id="549a5-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="549a5-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="549a5-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="549a5-107">\<binding></span></span>  
<span data-ttu-id="549a5-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="549a5-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="549a5-109">語法</span><span class="sxs-lookup"><span data-stu-id="549a5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="549a5-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="549a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="549a5-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="549a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="549a5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="549a5-112">Attributes</span></span>  
  
|<span data-ttu-id="549a5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="549a5-113">Attribute</span></span>|<span data-ttu-id="549a5-114">描述</span><span class="sxs-lookup"><span data-stu-id="549a5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="549a5-115">模式</span><span class="sxs-lookup"><span data-stu-id="549a5-115">mode</span></span>|<span data-ttu-id="549a5-116">指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="549a5-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="549a5-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="549a5-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="549a5-118">-None： 這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="549a5-118">-   None: This disables security.</span></span><br /><span data-ttu-id="549a5-119">-傳輸： 保護和驗證是由傳輸提供。</span><span class="sxs-lookup"><span data-stu-id="549a5-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="549a5-120">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="549a5-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="549a5-121">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="549a5-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="549a5-122">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="549a5-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="549a5-123">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="549a5-123">The default value is `Transport`.</span></span> <span data-ttu-id="549a5-124">此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="549a5-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="549a5-125">子元素</span><span class="sxs-lookup"><span data-stu-id="549a5-125">Child Elements</span></span>  
  
|<span data-ttu-id="549a5-126">項目</span><span class="sxs-lookup"><span data-stu-id="549a5-126">Element</span></span>|<span data-ttu-id="549a5-127">描述</span><span class="sxs-lookup"><span data-stu-id="549a5-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="549a5-128">\<transport></span><span class="sxs-lookup"><span data-stu-id="549a5-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="549a5-129">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="549a5-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="549a5-130">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="549a5-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="549a5-131">父項目</span><span class="sxs-lookup"><span data-stu-id="549a5-131">Parent Elements</span></span>  
  
|<span data-ttu-id="549a5-132">項目</span><span class="sxs-lookup"><span data-stu-id="549a5-132">Element</span></span>|<span data-ttu-id="549a5-133">描述</span><span class="sxs-lookup"><span data-stu-id="549a5-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="549a5-134">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="549a5-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="549a5-135">繫結項目[ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="549a5-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="549a5-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="549a5-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="549a5-137">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="549a5-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="549a5-138">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="549a5-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="549a5-139">繫結</span><span class="sxs-lookup"><span data-stu-id="549a5-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="549a5-140">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="549a5-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="549a5-141">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="549a5-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="549a5-142">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="549a5-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="549a5-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="549a5-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
