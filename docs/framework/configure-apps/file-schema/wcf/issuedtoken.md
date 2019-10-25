---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846865"
---
# <a name="issuedtoken"></a><span data-ttu-id="7ff2b-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="7ff2b-101">\<issuedToken></span></span>
<span data-ttu-id="7ff2b-102">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="7ff2b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7ff2b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7ff2b-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7ff2b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7ff2b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7ff2b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7ff2b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7ff2b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="7ff2b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7ff2b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="7ff2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="7ff2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="7ff2b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**issuedToken >**</span><span class="sxs-lookup"><span data-stu-id="7ff2b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff2b-110">語法</span><span class="sxs-lookup"><span data-stu-id="7ff2b-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ff2b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7ff2b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7ff2b-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ff2b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7ff2b-113">Attributes</span></span>  
  
|<span data-ttu-id="7ff2b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7ff2b-114">Attribute</span></span>|<span data-ttu-id="7ff2b-115">描述</span><span class="sxs-lookup"><span data-stu-id="7ff2b-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="7ff2b-116">選用性的布林值屬性，指定是否快取權杖。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="7ff2b-117">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="7ff2b-118">選用性字串屬性，這個屬性會指定交握作業要使用的亂數值 (Entropy)。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="7ff2b-119">值包括 `ClientEntropy`、`ServerEntropy` 與 `CombinedEntropy`，預設為 `CombinedEntropy`。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="7ff2b-120">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="7ff2b-121">選用性的整數屬性，這個屬性會指定權杖更新前，可通過的有效時間範圍 (由權杖簽發者提供) 百分比。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="7ff2b-122">值為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-122">Values are from 0 to 100.</span></span> <span data-ttu-id="7ff2b-123">預設為 60，表示嘗試更新前有 60% 的時間通過。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="7ff2b-124">選用性屬性，這個屬性會指定與簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="7ff2b-125">選用性屬性，這個屬性會指定與本機簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="7ff2b-126">選用性的 Timespan 屬性，當權杖簽發者 (STS) 沒有指定時間時，指定快取發行的權杖之期間。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="7ff2b-127">預設值為 "10675199.02：48： 05.4775807"。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ff2b-128">子項目</span><span class="sxs-lookup"><span data-stu-id="7ff2b-128">Child Elements</span></span>  
  
|<span data-ttu-id="7ff2b-129">項目</span><span class="sxs-lookup"><span data-stu-id="7ff2b-129">Element</span></span>|<span data-ttu-id="7ff2b-130">描述</span><span class="sxs-lookup"><span data-stu-id="7ff2b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ff2b-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="7ff2b-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="7ff2b-132">指定權杖的本機簽發者位址，與用來與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="7ff2b-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7ff2b-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="7ff2b-134">指定連絡本機簽發者時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ff2b-135">父項目</span><span class="sxs-lookup"><span data-stu-id="7ff2b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="7ff2b-136">項目</span><span class="sxs-lookup"><span data-stu-id="7ff2b-136">Element</span></span>|<span data-ttu-id="7ff2b-137">描述</span><span class="sxs-lookup"><span data-stu-id="7ff2b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ff2b-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7ff2b-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="7ff2b-139">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ff2b-140">備註</span><span class="sxs-lookup"><span data-stu-id="7ff2b-140">Remarks</span></span>  
 <span data-ttu-id="7ff2b-141">發行的權杖會在某些情況下當做自訂認證型別使用，例如在聯合案例中與安全權杖服務 (STS) 進行驗證時。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="7ff2b-142">根據預設，這個權杖是 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="7ff2b-143">如需詳細資訊，請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)，以及[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="7ff2b-144">這個區段包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="7ff2b-145">如需將用戶端設定為使用本機簽發者的指示，請參閱[如何：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="7ff2b-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff2b-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ff2b-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="7ff2b-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="7ff2b-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7ff2b-148">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="7ff2b-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7ff2b-149">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7ff2b-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7ff2b-150">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="7ff2b-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7ff2b-151">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="7ff2b-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="7ff2b-152">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="7ff2b-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="7ff2b-153">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7ff2b-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
