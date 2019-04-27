---
title: <add> 的 <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673611"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="8e370-102">\<新增 > 的\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8e370-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="8e370-103">新增與 STS 通訊時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="8e370-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="8e370-104">如果任何端點行為包含[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目，將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8e370-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="8e370-105">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="8e370-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="8e370-106">\<behaviors>\\</span><span class="sxs-lookup"><span data-stu-id="8e370-106">\<behaviors>\\</span></span>
<span data-ttu-id="8e370-107">endpointBehaviors 區段\<行為 > \\</span><span class="sxs-lookup"><span data-stu-id="8e370-107">endpointBehaviors section \<behavior>\\</span></span>
<span data-ttu-id="8e370-108">\<clientCredentials>\\</span><span class="sxs-lookup"><span data-stu-id="8e370-108">\<clientCredentials>\\</span></span>
<span data-ttu-id="8e370-109">\<issuedToken>\\</span><span class="sxs-lookup"><span data-stu-id="8e370-109">\<issuedToken>\\</span></span>
<span data-ttu-id="8e370-110">\<issuerChannelBehaviors > Element\\</span><span class="sxs-lookup"><span data-stu-id="8e370-110">\<issuerChannelBehaviors> Element\\</span></span>
<span data-ttu-id="8e370-111">\<add></span><span class="sxs-lookup"><span data-stu-id="8e370-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="8e370-112">語法</span><span class="sxs-lookup"><span data-stu-id="8e370-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e370-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8e370-113">Attributes and Elements</span></span>

<span data-ttu-id="8e370-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="8e370-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="8e370-115">屬性</span><span class="sxs-lookup"><span data-stu-id="8e370-115">Attributes</span></span>

|<span data-ttu-id="8e370-116">屬性</span><span class="sxs-lookup"><span data-stu-id="8e370-116">Attribute</span></span>|<span data-ttu-id="8e370-117">描述</span><span class="sxs-lookup"><span data-stu-id="8e370-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="8e370-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="8e370-118">issuerAddress</span></span>|<span data-ttu-id="8e370-119">要與其進行通訊之安全性權杖簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="8e370-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="8e370-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="8e370-120">behaviorConfiguration</span></span>|<span data-ttu-id="8e370-121">相同組態檔中定義之端點行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e370-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8e370-122">子元素</span><span class="sxs-lookup"><span data-stu-id="8e370-122">Child Elements</span></span>

<span data-ttu-id="8e370-123">無。</span><span class="sxs-lookup"><span data-stu-id="8e370-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e370-124">父項目</span><span class="sxs-lookup"><span data-stu-id="8e370-124">Parent Elements</span></span>

|<span data-ttu-id="8e370-125">項目</span><span class="sxs-lookup"><span data-stu-id="8e370-125">Element</span></span>|<span data-ttu-id="8e370-126">描述</span><span class="sxs-lookup"><span data-stu-id="8e370-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e370-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="8e370-127">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="8e370-128">包含與指定的服務權杖服務進行通訊時要使用 Windows Communication Foundation (WCF) 用戶端端點行為的集合。</span><span class="sxs-lookup"><span data-stu-id="8e370-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e370-129">備註</span><span class="sxs-lookup"><span data-stu-id="8e370-129">Remarks</span></span>

<span data-ttu-id="8e370-130">`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。</span><span class="sxs-lookup"><span data-stu-id="8e370-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="8e370-131">`behaviorConfiguration` 指向應用程式建立 Windows Communication Foundation (WCF) 通道中用來從安全性權杖服務取得核發的權杖端點行為。</span><span class="sxs-lookup"><span data-stu-id="8e370-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e370-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e370-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="8e370-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="8e370-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8e370-134">安全性行為</span><span class="sxs-lookup"><span data-stu-id="8e370-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8e370-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="8e370-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8e370-136">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8e370-136">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8e370-137">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="8e370-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="8e370-138">如何：建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="8e370-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="8e370-139">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="8e370-139">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="8e370-140">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="8e370-140">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8e370-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="8e370-141">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
