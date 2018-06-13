---
title: '&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752451"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="ad177-102">&lt;issuerChannelBehaviors&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="ad177-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="ad177-103">新增與 STS 通訊時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="ad177-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad177-104">如果任何端點行為包含[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目，將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ad177-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="ad177-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad177-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad177-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ad177-106">\<behaviors></span></span>  
<span data-ttu-id="ad177-107">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="ad177-107">endpointBehaviors section</span></span>  
<span data-ttu-id="ad177-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ad177-108">\<behavior></span></span>  
<span data-ttu-id="ad177-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ad177-109">\<clientCredentials></span></span>  
<span data-ttu-id="ad177-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="ad177-110">\<issuedToken></span></span>  
<span data-ttu-id="ad177-111">\<h > 項目</span><span class="sxs-lookup"><span data-stu-id="ad177-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="ad177-112">\<add></span><span class="sxs-lookup"><span data-stu-id="ad177-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad177-113">語法</span><span class="sxs-lookup"><span data-stu-id="ad177-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad177-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad177-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ad177-115">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="ad177-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad177-116">屬性</span><span class="sxs-lookup"><span data-stu-id="ad177-116">Attributes</span></span>  
  
|<span data-ttu-id="ad177-117">屬性</span><span class="sxs-lookup"><span data-stu-id="ad177-117">Attribute</span></span>|<span data-ttu-id="ad177-118">描述</span><span class="sxs-lookup"><span data-stu-id="ad177-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad177-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="ad177-119">issuerAddress</span></span>|<span data-ttu-id="ad177-120">要與其進行通訊之安全性權杖簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="ad177-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="ad177-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ad177-121">behaviorConfiguration</span></span>|<span data-ttu-id="ad177-122">相同組態檔中定義之端點行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad177-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad177-123">子項目</span><span class="sxs-lookup"><span data-stu-id="ad177-123">Child Elements</span></span>  
 <span data-ttu-id="ad177-124">無。</span><span class="sxs-lookup"><span data-stu-id="ad177-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad177-125">父項目</span><span class="sxs-lookup"><span data-stu-id="ad177-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ad177-126">項目</span><span class="sxs-lookup"><span data-stu-id="ad177-126">Element</span></span>|<span data-ttu-id="ad177-127">描述</span><span class="sxs-lookup"><span data-stu-id="ad177-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad177-128">\<h ></span><span class="sxs-lookup"><span data-stu-id="ad177-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="ad177-129">包含與指定的服務權杖服務通訊時所要使用的 Windows Communication Foundation (WCF) 用戶端端點行為集合。</span><span class="sxs-lookup"><span data-stu-id="ad177-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad177-130">備註</span><span class="sxs-lookup"><span data-stu-id="ad177-130">Remarks</span></span>  
 <span data-ttu-id="ad177-131">`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。</span><span class="sxs-lookup"><span data-stu-id="ad177-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="ad177-132">`behaviorConfiguration` 指向應用程式建立 Windows Communication Foundation (WCF) 的通道中用來從安全性權杖服務取得核發的權杖端點行為。</span><span class="sxs-lookup"><span data-stu-id="ad177-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad177-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad177-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="ad177-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="ad177-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="ad177-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="ad177-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="ad177-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ad177-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="ad177-137">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ad177-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ad177-138">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="ad177-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="ad177-139">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="ad177-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="ad177-140">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="ad177-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="ad177-141">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ad177-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="ad177-142">\<h ></span><span class="sxs-lookup"><span data-stu-id="ad177-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
