---
title: <issuerChannelBehaviors> 項目
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: e0e41b4f6d66cd4455c43dda7c77798553f2b58f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929932"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="ad42f-102">\<issuerChannelBehaviors > 元素</span><span class="sxs-lookup"><span data-stu-id="ad42f-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="ad42f-103">包含 Windows Communication Foundation (WCF) 用戶端端點行為 (定義于設定中) 的集合, 以便在與指定的服務權杖服務通訊時使用。</span><span class="sxs-lookup"><span data-stu-id="ad42f-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="ad42f-104">定義的行為不能包含任何[ \<clientCredentials >](clientcredentials.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ad42f-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="ad42f-105">語法</span><span class="sxs-lookup"><span data-stu-id="ad42f-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad42f-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad42f-106">Attributes and Elements</span></span>

<span data-ttu-id="ad42f-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ad42f-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad42f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ad42f-108">Attributes</span></span>

<span data-ttu-id="ad42f-109">無。</span><span class="sxs-lookup"><span data-stu-id="ad42f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad42f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ad42f-110">Child Elements</span></span>

|<span data-ttu-id="ad42f-111">項目</span><span class="sxs-lookup"><span data-stu-id="ad42f-111">Element</span></span>|<span data-ttu-id="ad42f-112">說明</span><span class="sxs-lookup"><span data-stu-id="ad42f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad42f-113">\<add></span><span class="sxs-lookup"><span data-stu-id="ad42f-113">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="ad42f-114">將行為新增至集合中。</span><span class="sxs-lookup"><span data-stu-id="ad42f-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ad42f-115">父項目</span><span class="sxs-lookup"><span data-stu-id="ad42f-115">Parent Elements</span></span>

|<span data-ttu-id="ad42f-116">項目</span><span class="sxs-lookup"><span data-stu-id="ad42f-116">Element</span></span>|<span data-ttu-id="ad42f-117">描述</span><span class="sxs-lookup"><span data-stu-id="ad42f-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad42f-118">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="ad42f-118">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="ad42f-119">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="ad42f-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ad42f-120">備註</span><span class="sxs-lookup"><span data-stu-id="ad42f-120">Remarks</span></span>

<span data-ttu-id="ad42f-121">當在必須使用任何行為 (包含 `<clientCredentials>` 項目之行為以外的任何行為) 與服務進行通訊時，請使用此項目。</span><span class="sxs-lookup"><span data-stu-id="ad42f-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="ad42f-122">例如, 如果必須包含[ \<dataContractSerializer >](datacontractserializer-element.md)行為元素, 則為。</span><span class="sxs-lookup"><span data-stu-id="ad42f-122">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad42f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad42f-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="ad42f-124">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="ad42f-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ad42f-125">安全性行為</span><span class="sxs-lookup"><span data-stu-id="ad42f-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ad42f-126">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ad42f-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ad42f-127">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ad42f-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ad42f-128">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="ad42f-128">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ad42f-129">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="ad42f-129">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="ad42f-130">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="ad42f-130">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="ad42f-131">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ad42f-131">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
