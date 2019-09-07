---
title: <security> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: c780b157d0d566e24c6826c253401a51fbfab69d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399832"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="2985c-102">\<netMsmqBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="2985c-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="2985c-103">定義 MSMQ 繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2985c-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="2985c-104">它指定是否啟用傳輸或 SOAP 安全性，以及如果啟用，正在使用的驗證模式和保護層級。</span><span class="sxs-lookup"><span data-stu-id="2985c-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
<span data-ttu-id="2985c-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2985c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2985c-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2985c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2985c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2985c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2985c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2985c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="2985c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="2985c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2985c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="2985c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2985c-111">語法</span><span class="sxs-lookup"><span data-stu-id="2985c-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2985c-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2985c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2985c-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2985c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2985c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2985c-114">Attributes</span></span>  
  
|<span data-ttu-id="2985c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="2985c-115">Attribute</span></span>|<span data-ttu-id="2985c-116">描述</span><span class="sxs-lookup"><span data-stu-id="2985c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2985c-117">模式</span><span class="sxs-lookup"><span data-stu-id="2985c-117">mode</span></span>|<span data-ttu-id="2985c-118">指定負責控制完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="2985c-118">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="2985c-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="2985c-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2985c-120">無這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2985c-120">-   None: This disables security.</span></span><br /><span data-ttu-id="2985c-121">運送傳輸會提供保護和驗證。</span><span class="sxs-lookup"><span data-stu-id="2985c-121">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="2985c-122">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="2985c-122">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="2985c-123">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="2985c-123">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="2985c-124">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="2985c-124">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="2985c-125">提示指定端對端應用程式安全性。</span><span class="sxs-lookup"><span data-stu-id="2985c-125">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="2985c-126">在傳輸層沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="2985c-126">There is no security offered at the transport layer.</span></span> <span data-ttu-id="2985c-127">這與其他標準繫結程序提供的安全性類似。</span><span class="sxs-lookup"><span data-stu-id="2985c-127">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="2985c-128">既提供傳輸和 SOAP 訊息層的安全性。</span><span class="sxs-lookup"><span data-stu-id="2985c-128">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="2985c-129">這兩個層級需要相同的認證。</span><span class="sxs-lookup"><span data-stu-id="2985c-129">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="2985c-130">預設值為 Transport。</span><span class="sxs-lookup"><span data-stu-id="2985c-130">The default value is Transport.</span></span> <span data-ttu-id="2985c-131">此屬性的型別為 <xref:System.ServiceModel.NetMsmqSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="2985c-131">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2985c-132">子元素</span><span class="sxs-lookup"><span data-stu-id="2985c-132">Child Elements</span></span>  
  
|<span data-ttu-id="2985c-133">項目</span><span class="sxs-lookup"><span data-stu-id="2985c-133">Element</span></span>|<span data-ttu-id="2985c-134">描述</span><span class="sxs-lookup"><span data-stu-id="2985c-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2985c-135">\<message></span><span class="sxs-lookup"><span data-stu-id="2985c-135">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="2985c-136">定義 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2985c-136">Defines the SOAP message security settings.</span></span> <span data-ttu-id="2985c-137">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>。</span><span class="sxs-lookup"><span data-stu-id="2985c-137">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="2985c-138">\<transport></span><span class="sxs-lookup"><span data-stu-id="2985c-138">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="2985c-139">定義 MSMQ 傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2985c-139">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="2985c-140">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="2985c-140">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2985c-141">父項目</span><span class="sxs-lookup"><span data-stu-id="2985c-141">Parent Elements</span></span>  
  
|<span data-ttu-id="2985c-142">項目</span><span class="sxs-lookup"><span data-stu-id="2985c-142">Element</span></span>|<span data-ttu-id="2985c-143">說明</span><span class="sxs-lookup"><span data-stu-id="2985c-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2985c-144">繫結</span><span class="sxs-lookup"><span data-stu-id="2985c-144">binding</span></span>|<span data-ttu-id="2985c-145">NetMsmqBinding 的 binding 元素 > [ \<](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2985c-145">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2985c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2985c-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="2985c-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2985c-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2985c-148">繫結</span><span class="sxs-lookup"><span data-stu-id="2985c-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2985c-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2985c-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2985c-150">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="2985c-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2985c-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="2985c-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="2985c-152">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="2985c-152">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
