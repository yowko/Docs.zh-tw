---
title: "&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7dca60a5bf1b3dd81502f9fd48d2881c3a9b71dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="1c29a-102">&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="1c29a-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="1c29a-103">新增與 STS 通訊時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="1c29a-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c29a-104">如果任何端點行為包含[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目，將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1c29a-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="1c29a-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1c29a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c29a-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1c29a-106">\<behaviors></span></span>  
<span data-ttu-id="1c29a-107">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="1c29a-107">endpointBehaviors section</span></span>  
<span data-ttu-id="1c29a-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1c29a-108">\<behavior></span></span>  
<span data-ttu-id="1c29a-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1c29a-109">\<clientCredentials></span></span>  
<span data-ttu-id="1c29a-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="1c29a-110">\<issuedToken></span></span>  
<span data-ttu-id="1c29a-111">\<h > 項目</span><span class="sxs-lookup"><span data-stu-id="1c29a-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="1c29a-112">\<add></span><span class="sxs-lookup"><span data-stu-id="1c29a-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c29a-113">語法</span><span class="sxs-lookup"><span data-stu-id="1c29a-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c29a-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1c29a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1c29a-115">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1c29a-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c29a-116">屬性</span><span class="sxs-lookup"><span data-stu-id="1c29a-116">Attributes</span></span>  
  
|<span data-ttu-id="1c29a-117">屬性</span><span class="sxs-lookup"><span data-stu-id="1c29a-117">Attribute</span></span>|<span data-ttu-id="1c29a-118">描述</span><span class="sxs-lookup"><span data-stu-id="1c29a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c29a-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="1c29a-119">issuerAddress</span></span>|<span data-ttu-id="1c29a-120">要與其進行通訊之安全性權杖簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="1c29a-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="1c29a-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="1c29a-121">behaviorConfiguration</span></span>|<span data-ttu-id="1c29a-122">相同組態檔中定義之端點行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c29a-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c29a-123">子元素</span><span class="sxs-lookup"><span data-stu-id="1c29a-123">Child Elements</span></span>  
 <span data-ttu-id="1c29a-124">無。</span><span class="sxs-lookup"><span data-stu-id="1c29a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c29a-125">父項目</span><span class="sxs-lookup"><span data-stu-id="1c29a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1c29a-126">項目</span><span class="sxs-lookup"><span data-stu-id="1c29a-126">Element</span></span>|<span data-ttu-id="1c29a-127">說明</span><span class="sxs-lookup"><span data-stu-id="1c29a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c29a-128">\<h ></span><span class="sxs-lookup"><span data-stu-id="1c29a-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="1c29a-129">包含要在與指定安全性權杖服務通訊時使用的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端端點行為集合。</span><span class="sxs-lookup"><span data-stu-id="1c29a-129">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c29a-130">備註</span><span class="sxs-lookup"><span data-stu-id="1c29a-130">Remarks</span></span>  
 <span data-ttu-id="1c29a-131">`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。</span><span class="sxs-lookup"><span data-stu-id="1c29a-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="1c29a-132">`behaviorConfiguration` 會指向端點行為，而應用程式會在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 建立的通道中使用該行為取得 Security Token Service 發出的權杖。</span><span class="sxs-lookup"><span data-stu-id="1c29a-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c29a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c29a-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="1c29a-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="1c29a-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="1c29a-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="1c29a-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1c29a-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="1c29a-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1c29a-137">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="1c29a-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1c29a-138">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="1c29a-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="1c29a-139">如何： 建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="1c29a-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="1c29a-140">如何： 設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="1c29a-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="1c29a-141">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="1c29a-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1c29a-142">\<h ></span><span class="sxs-lookup"><span data-stu-id="1c29a-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
