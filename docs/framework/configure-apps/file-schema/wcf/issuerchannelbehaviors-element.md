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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893153"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="103b7-102">\<issuerChannelBehaviors> 項目</span><span class="sxs-lookup"><span data-stu-id="103b7-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="103b7-103">包含 Windows Communication Foundation （WCF）用戶端端點行為（定義于設定中）的集合，以便在與指定的服務權杖服務通訊時使用。</span><span class="sxs-lookup"><span data-stu-id="103b7-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="103b7-104">定義的行為不能包含任何 [\<clientCredentials>](clientcredentials.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="103b7-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a><span data-ttu-id="103b7-105">語法</span><span class="sxs-lookup"><span data-stu-id="103b7-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="103b7-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="103b7-106">Attributes and elements</span></span>

<span data-ttu-id="103b7-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="103b7-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="103b7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="103b7-108">Attributes</span></span>

<span data-ttu-id="103b7-109">無。</span><span class="sxs-lookup"><span data-stu-id="103b7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="103b7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="103b7-110">Child elements</span></span>

|<span data-ttu-id="103b7-111">元素</span><span class="sxs-lookup"><span data-stu-id="103b7-111">Element</span></span>|<span data-ttu-id="103b7-112">描述</span><span class="sxs-lookup"><span data-stu-id="103b7-112">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="103b7-113">將行為新增至集合中。</span><span class="sxs-lookup"><span data-stu-id="103b7-113">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="103b7-114">父元素</span><span class="sxs-lookup"><span data-stu-id="103b7-114">Parent elements</span></span>

|<span data-ttu-id="103b7-115">元素</span><span class="sxs-lookup"><span data-stu-id="103b7-115">Element</span></span>|<span data-ttu-id="103b7-116">描述</span><span class="sxs-lookup"><span data-stu-id="103b7-116">Description</span></span>|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="103b7-117">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="103b7-117">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="103b7-118">備註</span><span class="sxs-lookup"><span data-stu-id="103b7-118">Remarks</span></span>

<span data-ttu-id="103b7-119">當在必須使用任何行為 (包含 `<clientCredentials>` 項目之行為以外的任何行為) 與服務進行通訊時，請使用此項目。</span><span class="sxs-lookup"><span data-stu-id="103b7-119">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="103b7-120">例如，如果 [\<dataContractSerializer>](datacontractserializer-element.md) 必須包含行為元素，則為。</span><span class="sxs-lookup"><span data-stu-id="103b7-120">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="103b7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="103b7-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="103b7-122">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="103b7-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="103b7-123">安全性行為</span><span class="sxs-lookup"><span data-stu-id="103b7-123">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="103b7-124">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="103b7-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="103b7-125">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="103b7-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="103b7-126">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="103b7-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="103b7-127">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="103b7-127">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="103b7-128">HOW TO：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="103b7-128">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="103b7-129">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="103b7-129">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
