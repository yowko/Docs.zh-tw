---
title: <add> 的 <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398324"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="7552a-102">\<add> 的 \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="7552a-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="7552a-103">新增與 STS 通訊時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="7552a-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="7552a-104">如果任何端點行為包含 [\<clientCredentials>](clientcredentials.md) 元素，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7552a-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="7552a-105">語法</span><span class="sxs-lookup"><span data-stu-id="7552a-105">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7552a-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7552a-106">Attributes and Elements</span></span>

<span data-ttu-id="7552a-107">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="7552a-107">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="7552a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7552a-108">Attributes</span></span>

|<span data-ttu-id="7552a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7552a-109">Attribute</span></span>|<span data-ttu-id="7552a-110">描述</span><span class="sxs-lookup"><span data-stu-id="7552a-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7552a-111">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="7552a-111">issuerAddress</span></span>|<span data-ttu-id="7552a-112">要與其進行通訊之安全性權杖簽發者的 URI。</span><span class="sxs-lookup"><span data-stu-id="7552a-112">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="7552a-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="7552a-113">behaviorConfiguration</span></span>|<span data-ttu-id="7552a-114">相同組態檔中定義之端點行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="7552a-114">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7552a-115">子元素</span><span class="sxs-lookup"><span data-stu-id="7552a-115">Child Elements</span></span>

<span data-ttu-id="7552a-116">無。</span><span class="sxs-lookup"><span data-stu-id="7552a-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7552a-117">父項目</span><span class="sxs-lookup"><span data-stu-id="7552a-117">Parent Elements</span></span>

|<span data-ttu-id="7552a-118">元素</span><span class="sxs-lookup"><span data-stu-id="7552a-118">Element</span></span>|<span data-ttu-id="7552a-119">描述</span><span class="sxs-lookup"><span data-stu-id="7552a-119">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="7552a-120">包含與指定的服務權杖服務通訊時，所要使用的 Windows Communication Foundation （WCF）用戶端端點行為集合。</span><span class="sxs-lookup"><span data-stu-id="7552a-120">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7552a-121">備註</span><span class="sxs-lookup"><span data-stu-id="7552a-121">Remarks</span></span>

<span data-ttu-id="7552a-122">`issuerAddress` 包含用戶端想要進行通訊之 Security Token Service 的 URI。</span><span class="sxs-lookup"><span data-stu-id="7552a-122">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="7552a-123">`behaviorConfiguration`指向端點行為，應用程式會在 Windows Communication Foundation （WCF）建立的通道中使用該行為，從安全性權杖服務取得發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="7552a-123">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="7552a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7552a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="7552a-125">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7552a-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7552a-126">安全性行為</span><span class="sxs-lookup"><span data-stu-id="7552a-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7552a-127">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7552a-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7552a-128">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="7552a-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7552a-129">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="7552a-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7552a-130">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="7552a-130">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="7552a-131">HOW TO：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="7552a-131">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="7552a-132">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7552a-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
