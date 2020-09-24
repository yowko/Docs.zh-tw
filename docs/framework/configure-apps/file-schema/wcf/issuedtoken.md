---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9f3feb11fbe45cbb4b952c70feaa99f9c481dd2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157365"
---
# \<issuedToken>

<span data-ttu-id="46cd3-101">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="46cd3-101">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="46cd3-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="46cd3-102">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46cd3-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46cd3-103">Attributes and Elements</span></span>  

 <span data-ttu-id="46cd3-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="46cd3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46cd3-105">屬性</span><span class="sxs-lookup"><span data-stu-id="46cd3-105">Attributes</span></span>  
  
|<span data-ttu-id="46cd3-106">屬性</span><span class="sxs-lookup"><span data-stu-id="46cd3-106">Attribute</span></span>|<span data-ttu-id="46cd3-107">描述</span><span class="sxs-lookup"><span data-stu-id="46cd3-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="46cd3-108">選用性的布林值屬性，指定是否快取權杖。</span><span class="sxs-lookup"><span data-stu-id="46cd3-108">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="46cd3-109">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="46cd3-109">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="46cd3-110">選用性字串屬性，這個屬性會指定交握作業要使用的亂數值 (Entropy)。</span><span class="sxs-lookup"><span data-stu-id="46cd3-110">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="46cd3-111">值包括 `ClientEntropy`、`ServerEntropy` 與 `CombinedEntropy`，預設為 `CombinedEntropy`。</span><span class="sxs-lookup"><span data-stu-id="46cd3-111">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="46cd3-112">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。</span><span class="sxs-lookup"><span data-stu-id="46cd3-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="46cd3-113">選用性的整數屬性，這個屬性會指定權杖更新前，可通過的有效時間範圍 (由權杖簽發者提供) 百分比。</span><span class="sxs-lookup"><span data-stu-id="46cd3-113">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="46cd3-114">值為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="46cd3-114">Values are from 0 to 100.</span></span> <span data-ttu-id="46cd3-115">預設為 60，表示嘗試更新前有 60% 的時間通過。</span><span class="sxs-lookup"><span data-stu-id="46cd3-115">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="46cd3-116">選用性屬性，這個屬性會指定與簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="46cd3-116">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="46cd3-117">選用性屬性，這個屬性會指定與本機簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="46cd3-117">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="46cd3-118">選用性的 Timespan 屬性，當權杖簽發者 (STS) 沒有指定時間時，指定快取發行的權杖之期間。</span><span class="sxs-lookup"><span data-stu-id="46cd3-118">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="46cd3-119">預設值為 "10675199.02：48： 05.4775807"。</span><span class="sxs-lookup"><span data-stu-id="46cd3-119">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46cd3-120">子元素</span><span class="sxs-lookup"><span data-stu-id="46cd3-120">Child Elements</span></span>  
  
|<span data-ttu-id="46cd3-121">項目</span><span class="sxs-lookup"><span data-stu-id="46cd3-121">Element</span></span>|<span data-ttu-id="46cd3-122">描述</span><span class="sxs-lookup"><span data-stu-id="46cd3-122">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="46cd3-123">指定權杖的本機簽發者位址，與用來與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="46cd3-123">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="46cd3-124">指定連絡本機簽發者時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="46cd3-124">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46cd3-125">父項目</span><span class="sxs-lookup"><span data-stu-id="46cd3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="46cd3-126">項目</span><span class="sxs-lookup"><span data-stu-id="46cd3-126">Element</span></span>|<span data-ttu-id="46cd3-127">描述</span><span class="sxs-lookup"><span data-stu-id="46cd3-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="46cd3-128">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="46cd3-128">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46cd3-129">備註</span><span class="sxs-lookup"><span data-stu-id="46cd3-129">Remarks</span></span>  

 <span data-ttu-id="46cd3-130">發行的權杖會在某些情況下當做自訂認證型別使用，例如在聯合案例中與安全權杖服務 (STS) 進行驗證時。</span><span class="sxs-lookup"><span data-stu-id="46cd3-130">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="46cd3-131">根據預設，這個權杖是 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="46cd3-131">By default, the token is a SAML token.</span></span> <span data-ttu-id="46cd3-132">如需詳細資訊，請參閱 [同盟和已發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)，以及 [同盟和已發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="46cd3-132">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="46cd3-133">這個區段包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="46cd3-133">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="46cd3-134">如需將用戶端設定為使用本機簽發者的指示，請參閱 [如何：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="46cd3-134">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cd3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46cd3-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="46cd3-136">安全性行為</span><span class="sxs-lookup"><span data-stu-id="46cd3-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="46cd3-137">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="46cd3-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="46cd3-138">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="46cd3-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="46cd3-139">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="46cd3-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="46cd3-140">作法：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="46cd3-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="46cd3-141">作法：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="46cd3-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="46cd3-142">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="46cd3-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
