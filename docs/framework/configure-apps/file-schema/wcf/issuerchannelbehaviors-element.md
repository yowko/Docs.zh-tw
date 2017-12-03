---
title: "&lt;issuerChannelBehaviors&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b73d090aa47e18792d313b3d086e7a667e74bb08
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="7d300-102">&lt;issuerChannelBehaviors&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="7d300-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="7d300-103">包含 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端端點行為 (於組態中定義) 的集合，與指定的服務權杖服務通訊時，會使用此行為。</span><span class="sxs-lookup"><span data-stu-id="7d300-103">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="7d300-104">已定義的行為不能包含任何[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目。</span><span class="sxs-lookup"><span data-stu-id="7d300-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="7d300-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7d300-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d300-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7d300-106">\<behaviors></span></span>  
<span data-ttu-id="7d300-107">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="7d300-107">endpointBehaviors section</span></span>  
<span data-ttu-id="7d300-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7d300-108">\<behavior></span></span>  
<span data-ttu-id="7d300-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7d300-109">\<clientCredentials></span></span>  
<span data-ttu-id="7d300-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="7d300-110">\<issuedToken></span></span>  
<span data-ttu-id="7d300-111">\<h ></span><span class="sxs-lookup"><span data-stu-id="7d300-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d300-112">語法</span><span class="sxs-lookup"><span data-stu-id="7d300-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d300-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7d300-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7d300-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7d300-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d300-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7d300-115">Attributes</span></span>  
 <span data-ttu-id="7d300-116">無。</span><span class="sxs-lookup"><span data-stu-id="7d300-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d300-117">子項目</span><span class="sxs-lookup"><span data-stu-id="7d300-117">Child Elements</span></span>  
  
|<span data-ttu-id="7d300-118">項目</span><span class="sxs-lookup"><span data-stu-id="7d300-118">Element</span></span>|<span data-ttu-id="7d300-119">描述</span><span class="sxs-lookup"><span data-stu-id="7d300-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d300-120">\<add></span><span class="sxs-lookup"><span data-stu-id="7d300-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="7d300-121">將行為新增至集合中。</span><span class="sxs-lookup"><span data-stu-id="7d300-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d300-122">父項目</span><span class="sxs-lookup"><span data-stu-id="7d300-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7d300-123">項目</span><span class="sxs-lookup"><span data-stu-id="7d300-123">Element</span></span>|<span data-ttu-id="7d300-124">說明</span><span class="sxs-lookup"><span data-stu-id="7d300-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d300-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="7d300-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="7d300-126">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="7d300-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d300-127">備註</span><span class="sxs-lookup"><span data-stu-id="7d300-127">Remarks</span></span>  
 <span data-ttu-id="7d300-128">當在必須使用任何行為 (包含 `<clientCredentials>` 項目之行為以外的任何行為) 與服務進行通訊時，請使用此項目。</span><span class="sxs-lookup"><span data-stu-id="7d300-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="7d300-129">例如，如果[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)行為項目必須包含。</span><span class="sxs-lookup"><span data-stu-id="7d300-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d300-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d300-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="7d300-131">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7d300-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7d300-132">安全性行為</span><span class="sxs-lookup"><span data-stu-id="7d300-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7d300-133">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7d300-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7d300-134">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="7d300-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7d300-135">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="7d300-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="7d300-136">如何： 建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="7d300-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="7d300-137">如何： 設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="7d300-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="7d300-138">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7d300-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
