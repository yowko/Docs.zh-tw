---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: b5ab3c3ad070499d686ea74b9fd459e89f380cfa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397968"
---
# <a name="issuedtoken"></a><span data-ttu-id="88ed1-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="88ed1-101">\<issuedToken></span></span>
<span data-ttu-id="88ed1-102">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="88ed1-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="88ed1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="88ed1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="88ed1-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="88ed1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="88ed1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="88ed1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="88ed1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="88ed1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="88ed1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="88ed1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="88ed1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="88ed1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="88ed1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedToken >**</span><span class="sxs-lookup"><span data-stu-id="88ed1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ed1-110">語法</span><span class="sxs-lookup"><span data-stu-id="88ed1-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88ed1-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="88ed1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="88ed1-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="88ed1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88ed1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="88ed1-113">Attributes</span></span>  
  
|<span data-ttu-id="88ed1-114">屬性</span><span class="sxs-lookup"><span data-stu-id="88ed1-114">Attribute</span></span>|<span data-ttu-id="88ed1-115">描述</span><span class="sxs-lookup"><span data-stu-id="88ed1-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="88ed1-116">選用性的布林值屬性，指定是否快取權杖。</span><span class="sxs-lookup"><span data-stu-id="88ed1-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="88ed1-117">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="88ed1-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="88ed1-118">選用性字串屬性，這個屬性會指定交握作業要使用的亂數值 (Entropy)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="88ed1-119">值包括 `ClientEntropy`、`ServerEntropy` 與 `CombinedEntropy`，預設為 `CombinedEntropy`。</span><span class="sxs-lookup"><span data-stu-id="88ed1-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="88ed1-120">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。</span><span class="sxs-lookup"><span data-stu-id="88ed1-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="88ed1-121">選用性的整數屬性，這個屬性會指定權杖更新前，可通過的有效時間範圍 (由權杖簽發者提供) 百分比。</span><span class="sxs-lookup"><span data-stu-id="88ed1-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="88ed1-122">值為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="88ed1-122">Values are from 0 to 100.</span></span> <span data-ttu-id="88ed1-123">預設為 60，表示嘗試更新前有 60% 的時間通過。</span><span class="sxs-lookup"><span data-stu-id="88ed1-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="88ed1-124">選用性屬性，這個屬性會指定與簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="88ed1-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="88ed1-125">選用性屬性，這個屬性會指定與本機簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="88ed1-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="88ed1-126">選用性的 Timespan 屬性，當權杖簽發者 (STS) 沒有指定時間時，指定快取發行的權杖之期間。</span><span class="sxs-lookup"><span data-stu-id="88ed1-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="88ed1-127">預設值為 "10675199.02：48： 05.4775807"。</span><span class="sxs-lookup"><span data-stu-id="88ed1-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88ed1-128">子元素</span><span class="sxs-lookup"><span data-stu-id="88ed1-128">Child Elements</span></span>  
  
|<span data-ttu-id="88ed1-129">項目</span><span class="sxs-lookup"><span data-stu-id="88ed1-129">Element</span></span>|<span data-ttu-id="88ed1-130">描述</span><span class="sxs-lookup"><span data-stu-id="88ed1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88ed1-131">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="88ed1-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="88ed1-132">指定權杖的本機簽發者位址，與用來與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="88ed1-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="88ed1-133">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="88ed1-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="88ed1-134">指定連絡本機簽發者時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="88ed1-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88ed1-135">父項目</span><span class="sxs-lookup"><span data-stu-id="88ed1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="88ed1-136">項目</span><span class="sxs-lookup"><span data-stu-id="88ed1-136">Element</span></span>|<span data-ttu-id="88ed1-137">描述</span><span class="sxs-lookup"><span data-stu-id="88ed1-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88ed1-138">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="88ed1-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="88ed1-139">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="88ed1-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88ed1-140">備註</span><span class="sxs-lookup"><span data-stu-id="88ed1-140">Remarks</span></span>  
 <span data-ttu-id="88ed1-141">發行的權杖會在某些情況下當做自訂認證型別使用，例如在聯合案例中與安全權杖服務 (STS) 進行驗證時。</span><span class="sxs-lookup"><span data-stu-id="88ed1-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="88ed1-142">根據預設，這個權杖是 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="88ed1-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="88ed1-143">如需詳細資訊，請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="88ed1-144">和[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-144">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="88ed1-145">這個區段包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="88ed1-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="88ed1-146">如需設定用戶端使用本機簽發者的指示，請[參閱如何：設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ed1-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88ed1-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="88ed1-148">安全性行為</span><span class="sxs-lookup"><span data-stu-id="88ed1-148">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="88ed1-149">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="88ed1-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="88ed1-150">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="88ed1-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="88ed1-151">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="88ed1-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="88ed1-152">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="88ed1-152">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="88ed1-153">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="88ed1-153">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="88ed1-154">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="88ed1-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
