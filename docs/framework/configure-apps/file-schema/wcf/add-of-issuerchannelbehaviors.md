---
title: <add> 的 <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920117"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="11fc5-102">\<新增 issuerChannelBehaviors > \<的 ></span><span class="sxs-lookup"><span data-stu-id="11fc5-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="11fc5-103">新增與 STS 通訊時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="11fc5-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="11fc5-104">如果任何端點行為包含[ \<clientCredentials >](clientcredentials.md)元素, 則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="11fc5-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="11fc5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="11fc5-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="11fc5-106">\<行為 > </span><span class="sxs-lookup"><span data-stu-id="11fc5-106">\<behaviors></span></span>\
<span data-ttu-id="11fc5-107">endpointBehaviors 區段\<行為 > </span><span class="sxs-lookup"><span data-stu-id="11fc5-107">endpointBehaviors section \<behavior></span></span>\
<span data-ttu-id="11fc5-108">\<clientCredentials > </span><span class="sxs-lookup"><span data-stu-id="11fc5-108">\<clientCredentials></span></span>\
<span data-ttu-id="11fc5-109">\<issuedToken > </span><span class="sxs-lookup"><span data-stu-id="11fc5-109">\<issuedToken></span></span>\
<span data-ttu-id="11fc5-110">\<issuerChannelBehaviors > 元素 </span><span class="sxs-lookup"><span data-stu-id="11fc5-110">\<issuerChannelBehaviors> Element</span></span>\
<span data-ttu-id="11fc5-111">\<add></span><span class="sxs-lookup"><span data-stu-id="11fc5-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="11fc5-112">語法</span><span class="sxs-lookup"><span data-stu-id="11fc5-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11fc5-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="11fc5-113">Attributes and Elements</span></span>

<span data-ttu-id="11fc5-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="11fc5-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="11fc5-115">屬性</span><span class="sxs-lookup"><span data-stu-id="11fc5-115">Attributes</span></span>

|<span data-ttu-id="11fc5-116">屬性</span><span class="sxs-lookup"><span data-stu-id="11fc5-116">Attribute</span></span>|<span data-ttu-id="11fc5-117">描述</span><span class="sxs-lookup"><span data-stu-id="11fc5-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="11fc5-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="11fc5-118">issuerAddress</span></span>|<span data-ttu-id="11fc5-119">要與其進行通訊之安全性權杖簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="11fc5-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="11fc5-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="11fc5-120">behaviorConfiguration</span></span>|<span data-ttu-id="11fc5-121">相同組態檔中定義之端點行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="11fc5-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="11fc5-122">子元素</span><span class="sxs-lookup"><span data-stu-id="11fc5-122">Child Elements</span></span>

<span data-ttu-id="11fc5-123">無。</span><span class="sxs-lookup"><span data-stu-id="11fc5-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11fc5-124">父項目</span><span class="sxs-lookup"><span data-stu-id="11fc5-124">Parent Elements</span></span>

|<span data-ttu-id="11fc5-125">項目</span><span class="sxs-lookup"><span data-stu-id="11fc5-125">Element</span></span>|<span data-ttu-id="11fc5-126">說明</span><span class="sxs-lookup"><span data-stu-id="11fc5-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11fc5-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="11fc5-127">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="11fc5-128">包含與指定的服務權杖服務通訊時, 所要使用的 Windows Communication Foundation (WCF) 用戶端端點行為集合。</span><span class="sxs-lookup"><span data-stu-id="11fc5-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11fc5-129">備註</span><span class="sxs-lookup"><span data-stu-id="11fc5-129">Remarks</span></span>

<span data-ttu-id="11fc5-130">`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。</span><span class="sxs-lookup"><span data-stu-id="11fc5-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="11fc5-131">`behaviorConfiguration`指向端點行為, 應用程式會在 Windows Communication Foundation (WCF) 建立的通道中使用該行為, 從安全性權杖服務取得發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="11fc5-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="11fc5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11fc5-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="11fc5-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="11fc5-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="11fc5-134">安全性行為</span><span class="sxs-lookup"><span data-stu-id="11fc5-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="11fc5-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="11fc5-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="11fc5-136">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="11fc5-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="11fc5-137">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="11fc5-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="11fc5-138">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="11fc5-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="11fc5-139">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="11fc5-139">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="11fc5-140">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="11fc5-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="11fc5-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="11fc5-141">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
