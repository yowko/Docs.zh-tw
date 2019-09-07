---
title: <issuerChannelBehaviors> 項目
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 2c0e0d8d041565edd25c4b2c2802bfd2a589b4f7
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397906"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="6cce2-102">\<issuerChannelBehaviors > 元素</span><span class="sxs-lookup"><span data-stu-id="6cce2-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="6cce2-103">包含 Windows Communication Foundation （WCF）用戶端端點行為（定義于設定中）的集合，以便在與指定的服務權杖服務通訊時使用。</span><span class="sxs-lookup"><span data-stu-id="6cce2-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="6cce2-104">定義的行為不能包含任何[ \<clientCredentials >](clientcredentials.md)元素。</span><span class="sxs-lookup"><span data-stu-id="6cce2-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="6cce2-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6cce2-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6cce2-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6cce2-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6cce2-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6cce2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6cce2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6cce2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="6cce2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6cce2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="6cce2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="6cce2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="6cce2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="6cce2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="6cce2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerChannelBehaviors >**</span><span class="sxs-lookup"><span data-stu-id="6cce2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerChannelBehaviors>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6cce2-113">語法</span><span class="sxs-lookup"><span data-stu-id="6cce2-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6cce2-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6cce2-114">Attributes and Elements</span></span>

<span data-ttu-id="6cce2-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6cce2-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6cce2-116">屬性</span><span class="sxs-lookup"><span data-stu-id="6cce2-116">Attributes</span></span>

<span data-ttu-id="6cce2-117">無。</span><span class="sxs-lookup"><span data-stu-id="6cce2-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6cce2-118">子元素</span><span class="sxs-lookup"><span data-stu-id="6cce2-118">Child Elements</span></span>

|<span data-ttu-id="6cce2-119">項目</span><span class="sxs-lookup"><span data-stu-id="6cce2-119">Element</span></span>|<span data-ttu-id="6cce2-120">描述</span><span class="sxs-lookup"><span data-stu-id="6cce2-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cce2-121">\<add></span><span class="sxs-lookup"><span data-stu-id="6cce2-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="6cce2-122">將行為新增至集合中。</span><span class="sxs-lookup"><span data-stu-id="6cce2-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6cce2-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6cce2-123">Parent Elements</span></span>

|<span data-ttu-id="6cce2-124">項目</span><span class="sxs-lookup"><span data-stu-id="6cce2-124">Element</span></span>|<span data-ttu-id="6cce2-125">描述</span><span class="sxs-lookup"><span data-stu-id="6cce2-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cce2-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="6cce2-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="6cce2-127">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="6cce2-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6cce2-128">備註</span><span class="sxs-lookup"><span data-stu-id="6cce2-128">Remarks</span></span>

<span data-ttu-id="6cce2-129">當在必須使用任何行為 (包含 `<clientCredentials>` 項目之行為以外的任何行為) 與服務進行通訊時，請使用此項目。</span><span class="sxs-lookup"><span data-stu-id="6cce2-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="6cce2-130">例如，如果必須包含[ \<dataContractSerializer >](datacontractserializer-element.md)行為元素，則為。</span><span class="sxs-lookup"><span data-stu-id="6cce2-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cce2-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cce2-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="6cce2-132">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="6cce2-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6cce2-133">安全性行為</span><span class="sxs-lookup"><span data-stu-id="6cce2-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6cce2-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="6cce2-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6cce2-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6cce2-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6cce2-136">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="6cce2-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="6cce2-137">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="6cce2-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="6cce2-138">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="6cce2-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="6cce2-139">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="6cce2-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
