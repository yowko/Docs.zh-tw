---
title: <issuerChannelBehaviors> 項目
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893153"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="dad5e-102">\<issuerChannelBehaviors > 元素</span><span class="sxs-lookup"><span data-stu-id="dad5e-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="dad5e-103">包含 Windows Communication Foundation （WCF）用戶端端點行為（定義于設定中）的集合，以便在與指定的服務權杖服務通訊時使用。</span><span class="sxs-lookup"><span data-stu-id="dad5e-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="dad5e-104">定義的行為不能包含任何[ \<clientCredentials >](clientcredentials.md)元素。</span><span class="sxs-lookup"><span data-stu-id="dad5e-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="dad5e-105">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dad5e-105">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="dad5e-106">&nbsp;&nbsp;[\<System.servicemodel >](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dad5e-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="dad5e-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<行為 >](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dad5e-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="dad5e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors >](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dad5e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="dad5e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<行為 >](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dad5e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="dad5e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials >](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="dad5e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="dad5e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken >](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="dad5e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="dad5e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dad5e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="dad5e-113">語法</span><span class="sxs-lookup"><span data-stu-id="dad5e-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dad5e-114">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="dad5e-114">Attributes and elements</span></span>

<span data-ttu-id="dad5e-115">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dad5e-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dad5e-116">屬性</span><span class="sxs-lookup"><span data-stu-id="dad5e-116">Attributes</span></span>

<span data-ttu-id="dad5e-117">無。</span><span class="sxs-lookup"><span data-stu-id="dad5e-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dad5e-118">子元素</span><span class="sxs-lookup"><span data-stu-id="dad5e-118">Child elements</span></span>

|<span data-ttu-id="dad5e-119">元素</span><span class="sxs-lookup"><span data-stu-id="dad5e-119">Element</span></span>|<span data-ttu-id="dad5e-120">描述</span><span class="sxs-lookup"><span data-stu-id="dad5e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dad5e-121">\<add></span><span class="sxs-lookup"><span data-stu-id="dad5e-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="dad5e-122">將行為新增至集合中。</span><span class="sxs-lookup"><span data-stu-id="dad5e-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dad5e-123">父元素</span><span class="sxs-lookup"><span data-stu-id="dad5e-123">Parent elements</span></span>

|<span data-ttu-id="dad5e-124">元素</span><span class="sxs-lookup"><span data-stu-id="dad5e-124">Element</span></span>|<span data-ttu-id="dad5e-125">描述</span><span class="sxs-lookup"><span data-stu-id="dad5e-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dad5e-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="dad5e-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="dad5e-127">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="dad5e-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dad5e-128">備註</span><span class="sxs-lookup"><span data-stu-id="dad5e-128">Remarks</span></span>

<span data-ttu-id="dad5e-129">當在必須使用任何行為 (包含 `<clientCredentials>` 項目之行為以外的任何行為) 與服務進行通訊時，請使用此項目。</span><span class="sxs-lookup"><span data-stu-id="dad5e-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="dad5e-130">例如，如果必須包含[ \<dataContractSerializer >](datacontractserializer-element.md)行為元素，則為。</span><span class="sxs-lookup"><span data-stu-id="dad5e-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="dad5e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dad5e-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="dad5e-132">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="dad5e-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="dad5e-133">安全性行為</span><span class="sxs-lookup"><span data-stu-id="dad5e-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="dad5e-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="dad5e-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dad5e-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="dad5e-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dad5e-136">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="dad5e-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="dad5e-137">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="dad5e-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="dad5e-138">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="dad5e-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="dad5e-139">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="dad5e-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
