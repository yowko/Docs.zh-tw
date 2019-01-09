---
title: '&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 072e3f4e961f6bf45e7c8b48c64cda36d385cf2b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149536"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="deb6b-102">&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="deb6b-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="deb6b-103">新增與 STS 通訊時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="deb6b-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="deb6b-104">如果任何端點行為包含[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目，將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="deb6b-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="deb6b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="deb6b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="deb6b-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="deb6b-106">\<behaviors></span></span>  
<span data-ttu-id="deb6b-107">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="deb6b-107">endpointBehaviors section</span></span>  
<span data-ttu-id="deb6b-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="deb6b-108">\<behavior></span></span>  
<span data-ttu-id="deb6b-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="deb6b-109">\<clientCredentials></span></span>  
<span data-ttu-id="deb6b-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="deb6b-110">\<issuedToken></span></span>  
<span data-ttu-id="deb6b-111">\<issuerChannelBehaviors > 項目</span><span class="sxs-lookup"><span data-stu-id="deb6b-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="deb6b-112">\<add></span><span class="sxs-lookup"><span data-stu-id="deb6b-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deb6b-113">語法</span><span class="sxs-lookup"><span data-stu-id="deb6b-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"
     behaviorConfiguraton="string" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="deb6b-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="deb6b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="deb6b-115">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="deb6b-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="deb6b-116">屬性</span><span class="sxs-lookup"><span data-stu-id="deb6b-116">Attributes</span></span>  
  
|<span data-ttu-id="deb6b-117">屬性</span><span class="sxs-lookup"><span data-stu-id="deb6b-117">Attribute</span></span>|<span data-ttu-id="deb6b-118">描述</span><span class="sxs-lookup"><span data-stu-id="deb6b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="deb6b-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="deb6b-119">issuerAddress</span></span>|<span data-ttu-id="deb6b-120">要與其進行通訊之安全性權杖簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="deb6b-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="deb6b-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="deb6b-121">behaviorConfiguration</span></span>|<span data-ttu-id="deb6b-122">相同組態檔中定義之端點行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="deb6b-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="deb6b-123">子元素</span><span class="sxs-lookup"><span data-stu-id="deb6b-123">Child Elements</span></span>  
 <span data-ttu-id="deb6b-124">無。</span><span class="sxs-lookup"><span data-stu-id="deb6b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="deb6b-125">父項目</span><span class="sxs-lookup"><span data-stu-id="deb6b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="deb6b-126">項目</span><span class="sxs-lookup"><span data-stu-id="deb6b-126">Element</span></span>|<span data-ttu-id="deb6b-127">描述</span><span class="sxs-lookup"><span data-stu-id="deb6b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="deb6b-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="deb6b-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="deb6b-129">包含與指定的服務權杖服務進行通訊時要使用 Windows Communication Foundation (WCF) 用戶端端點行為的集合。</span><span class="sxs-lookup"><span data-stu-id="deb6b-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deb6b-130">備註</span><span class="sxs-lookup"><span data-stu-id="deb6b-130">Remarks</span></span>  
 <span data-ttu-id="deb6b-131">`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。</span><span class="sxs-lookup"><span data-stu-id="deb6b-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="deb6b-132">`behaviorConfiguration` 指向應用程式建立 Windows Communication Foundation (WCF) 通道中用來從安全性權杖服務取得核發的權杖端點行為。</span><span class="sxs-lookup"><span data-stu-id="deb6b-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb6b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deb6b-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="deb6b-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="deb6b-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="deb6b-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="deb6b-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="deb6b-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="deb6b-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="deb6b-137">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="deb6b-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="deb6b-138">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="deb6b-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="deb6b-139">如何：建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="deb6b-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="deb6b-140">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="deb6b-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="deb6b-141">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="deb6b-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="deb6b-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="deb6b-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
