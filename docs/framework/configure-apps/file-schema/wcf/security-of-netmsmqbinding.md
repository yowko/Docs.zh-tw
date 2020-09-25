---
title: <security> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 32b066fdf4d8edbbd36fdff7b14bdec87ddc970d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170073"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="88e7a-102">\<security> 的 \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="88e7a-102">\<security> of \<netMsmqBinding></span></span>

<span data-ttu-id="88e7a-103">定義 MSMQ 繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="88e7a-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="88e7a-104">它指定是否啟用傳輸或 SOAP 安全性，以及如果啟用，正在使用的驗證模式和保護層級。</span><span class="sxs-lookup"><span data-stu-id="88e7a-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="88e7a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="88e7a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88e7a-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="88e7a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="88e7a-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="88e7a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88e7a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="88e7a-108">Attributes</span></span>  
  
|<span data-ttu-id="88e7a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="88e7a-109">Attribute</span></span>|<span data-ttu-id="88e7a-110">描述</span><span class="sxs-lookup"><span data-stu-id="88e7a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88e7a-111">mode</span><span class="sxs-lookup"><span data-stu-id="88e7a-111">mode</span></span>|<span data-ttu-id="88e7a-112">指定負責控制完整性、機密性和驗證的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="88e7a-112">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="88e7a-113">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="88e7a-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="88e7a-114">-None：這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="88e7a-114">-   None: This disables security.</span></span><br /><span data-ttu-id="88e7a-115">-Transport：傳輸提供保護和驗證。</span><span class="sxs-lookup"><span data-stu-id="88e7a-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="88e7a-116">這會套用在兩個佇列管理員之間的訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="88e7a-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="88e7a-117">應用程式和佇列管理員之間沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="88e7a-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="88e7a-118">現有 Msmq 應用程式在功能上相當於這個安全性模式類型。</span><span class="sxs-lookup"><span data-stu-id="88e7a-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="88e7a-119">-Message：指定端對端應用程式安全性。</span><span class="sxs-lookup"><span data-stu-id="88e7a-119">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="88e7a-120">在傳輸層沒有提供安全性。</span><span class="sxs-lookup"><span data-stu-id="88e7a-120">There is no security offered at the transport layer.</span></span> <span data-ttu-id="88e7a-121">這與其他標準繫結程序提供的安全性類似。</span><span class="sxs-lookup"><span data-stu-id="88e7a-121">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="88e7a-122">-Both：提供傳輸和 SOAP 訊息層的安全性。</span><span class="sxs-lookup"><span data-stu-id="88e7a-122">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="88e7a-123">這兩個層級需要相同的認證。</span><span class="sxs-lookup"><span data-stu-id="88e7a-123">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="88e7a-124">預設值為 Transport。</span><span class="sxs-lookup"><span data-stu-id="88e7a-124">The default value is Transport.</span></span> <span data-ttu-id="88e7a-125">此屬性的型別為 <xref:System.ServiceModel.NetMsmqSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="88e7a-125">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88e7a-126">子元素</span><span class="sxs-lookup"><span data-stu-id="88e7a-126">Child Elements</span></span>  
  
|<span data-ttu-id="88e7a-127">項目</span><span class="sxs-lookup"><span data-stu-id="88e7a-127">Element</span></span>|<span data-ttu-id="88e7a-128">描述</span><span class="sxs-lookup"><span data-stu-id="88e7a-128">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="88e7a-129">定義 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="88e7a-129">Defines the SOAP message security settings.</span></span> <span data-ttu-id="88e7a-130">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>。</span><span class="sxs-lookup"><span data-stu-id="88e7a-130">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="88e7a-131">定義 MSMQ 傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="88e7a-131">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="88e7a-132">此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="88e7a-132">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88e7a-133">父項目</span><span class="sxs-lookup"><span data-stu-id="88e7a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="88e7a-134">項目</span><span class="sxs-lookup"><span data-stu-id="88e7a-134">Element</span></span>|<span data-ttu-id="88e7a-135">描述</span><span class="sxs-lookup"><span data-stu-id="88e7a-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88e7a-136">繫結</span><span class="sxs-lookup"><span data-stu-id="88e7a-136">binding</span></span>|<span data-ttu-id="88e7a-137">的繫結項目。 [\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="88e7a-137">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88e7a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88e7a-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="88e7a-139">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="88e7a-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="88e7a-140">繫結</span><span class="sxs-lookup"><span data-stu-id="88e7a-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="88e7a-141">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="88e7a-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="88e7a-142">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="88e7a-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="88e7a-143">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="88e7a-143">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
