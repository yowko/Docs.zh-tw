---
title: <add> 的 <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398324"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="1b5a3-102">\<新增 issuerChannelBehaviors > \<的 ></span><span class="sxs-lookup"><span data-stu-id="1b5a3-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="1b5a3-103">新增與 STS 通訊時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="1b5a3-104">如果任何端點行為包含[ \<clientCredentials >](clientcredentials.md)元素，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="1b5a3-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1b5a3-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1b5a3-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1b5a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="1b5a3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="1b5a3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="1b5a3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="1b5a3-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerChannelBehaviors >** ](issuerchannelbehaviors-element.md)</span><span class="sxs-lookup"><span data-stu-id="1b5a3-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)</span></span>\
<span data-ttu-id="1b5a3-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="1b5a3-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="1b5a3-114">語法</span><span class="sxs-lookup"><span data-stu-id="1b5a3-114">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b5a3-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1b5a3-115">Attributes and Elements</span></span>

<span data-ttu-id="1b5a3-116">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1b5a3-116">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="1b5a3-117">屬性</span><span class="sxs-lookup"><span data-stu-id="1b5a3-117">Attributes</span></span>

|<span data-ttu-id="1b5a3-118">屬性</span><span class="sxs-lookup"><span data-stu-id="1b5a3-118">Attribute</span></span>|<span data-ttu-id="1b5a3-119">說明</span><span class="sxs-lookup"><span data-stu-id="1b5a3-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="1b5a3-120">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="1b5a3-120">issuerAddress</span></span>|<span data-ttu-id="1b5a3-121">要與其進行通訊之安全性權杖簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-121">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="1b5a3-122">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="1b5a3-122">behaviorConfiguration</span></span>|<span data-ttu-id="1b5a3-123">相同組態檔中定義之端點行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-123">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1b5a3-124">子元素</span><span class="sxs-lookup"><span data-stu-id="1b5a3-124">Child Elements</span></span>

<span data-ttu-id="1b5a3-125">無。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b5a3-126">父項目</span><span class="sxs-lookup"><span data-stu-id="1b5a3-126">Parent Elements</span></span>

|<span data-ttu-id="1b5a3-127">項目</span><span class="sxs-lookup"><span data-stu-id="1b5a3-127">Element</span></span>|<span data-ttu-id="1b5a3-128">描述</span><span class="sxs-lookup"><span data-stu-id="1b5a3-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b5a3-129">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="1b5a3-129">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="1b5a3-130">包含與指定的服務權杖服務通訊時，所要使用的 Windows Communication Foundation （WCF）用戶端端點行為集合。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-130">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1b5a3-131">備註</span><span class="sxs-lookup"><span data-stu-id="1b5a3-131">Remarks</span></span>

<span data-ttu-id="1b5a3-132">`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-132">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="1b5a3-133">`behaviorConfiguration`指向端點行為，應用程式會在 Windows Communication Foundation （WCF）建立的通道中使用該行為，從安全性權杖服務取得發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="1b5a3-133">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b5a3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b5a3-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="1b5a3-135">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="1b5a3-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1b5a3-136">安全性行為</span><span class="sxs-lookup"><span data-stu-id="1b5a3-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="1b5a3-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="1b5a3-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1b5a3-138">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="1b5a3-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1b5a3-139">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="1b5a3-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="1b5a3-140">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="1b5a3-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="1b5a3-141">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="1b5a3-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="1b5a3-142">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="1b5a3-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1b5a3-143">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="1b5a3-143">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
