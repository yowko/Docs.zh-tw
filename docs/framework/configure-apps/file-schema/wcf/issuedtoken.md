---
title: '&lt;issuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9a8d701e0806aae0a17a1c5ff7284606dd080f85
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750228"
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="a68da-102">&lt;issuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="a68da-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="a68da-103">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="a68da-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="a68da-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a68da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a68da-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a68da-105">\<behaviors></span></span>  
<span data-ttu-id="a68da-106">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="a68da-106">endpointBehaviors section</span></span>  
<span data-ttu-id="a68da-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a68da-107">\<behavior></span></span>  
<span data-ttu-id="a68da-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a68da-108">\<clientCredentials></span></span>  
<span data-ttu-id="a68da-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="a68da-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68da-110">語法</span><span class="sxs-lookup"><span data-stu-id="a68da-110">Syntax</span></span>  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a68da-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a68da-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a68da-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a68da-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a68da-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a68da-113">Attributes</span></span>  
  
|<span data-ttu-id="a68da-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a68da-114">Attribute</span></span>|<span data-ttu-id="a68da-115">描述</span><span class="sxs-lookup"><span data-stu-id="a68da-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="a68da-116">選用性的布林值屬性，指定是否快取權杖。</span><span class="sxs-lookup"><span data-stu-id="a68da-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="a68da-117">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a68da-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="a68da-118">選用性字串屬性，這個屬性會指定交握作業要使用的亂數值 (Entropy)。</span><span class="sxs-lookup"><span data-stu-id="a68da-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="a68da-119">值包括 `ClientEntropy`、`ServerEntropy` 與 `CombinedEntropy`，預設為 `CombinedEntropy`。</span><span class="sxs-lookup"><span data-stu-id="a68da-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="a68da-120">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。</span><span class="sxs-lookup"><span data-stu-id="a68da-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="a68da-121">選用性的整數屬性，這個屬性會指定權杖更新前，可通過的有效時間範圍 (由權杖簽發者提供) 百分比。</span><span class="sxs-lookup"><span data-stu-id="a68da-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="a68da-122">值為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="a68da-122">Values are from 0 to 100.</span></span> <span data-ttu-id="a68da-123">預設為 60，表示嘗試更新前有 60% 的時間通過。</span><span class="sxs-lookup"><span data-stu-id="a68da-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="a68da-124">選用性屬性，這個屬性會指定與簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="a68da-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="a68da-125">選用性屬性，這個屬性會指定與本機簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="a68da-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="a68da-126">選用性的 Timespan 屬性，當權杖簽發者 (STS) 沒有指定時間時，指定快取發行的權杖之期間。</span><span class="sxs-lookup"><span data-stu-id="a68da-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="a68da-127">預設值是"10675199.02:48:05.4775807。 」</span><span class="sxs-lookup"><span data-stu-id="a68da-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a68da-128">子項目</span><span class="sxs-lookup"><span data-stu-id="a68da-128">Child Elements</span></span>  
  
|<span data-ttu-id="a68da-129">項目</span><span class="sxs-lookup"><span data-stu-id="a68da-129">Element</span></span>|<span data-ttu-id="a68da-130">描述</span><span class="sxs-lookup"><span data-stu-id="a68da-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a68da-131">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="a68da-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="a68da-132">指定權杖的本機簽發者位址，與用來與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="a68da-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="a68da-133">\<h ></span><span class="sxs-lookup"><span data-stu-id="a68da-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="a68da-134">指定連絡本機簽發者時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="a68da-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a68da-135">父項目</span><span class="sxs-lookup"><span data-stu-id="a68da-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a68da-136">項目</span><span class="sxs-lookup"><span data-stu-id="a68da-136">Element</span></span>|<span data-ttu-id="a68da-137">描述</span><span class="sxs-lookup"><span data-stu-id="a68da-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a68da-138">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a68da-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="a68da-139">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="a68da-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a68da-140">備註</span><span class="sxs-lookup"><span data-stu-id="a68da-140">Remarks</span></span>  
 <span data-ttu-id="a68da-141">發行的權杖會在某些情況下當做自訂認證型別使用，例如在聯合案例中與安全權杖服務 (STS) 進行驗證時。</span><span class="sxs-lookup"><span data-stu-id="a68da-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="a68da-142">根據預設，這個權杖是 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="a68da-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="a68da-143">如需詳細資訊，請參閱[同盟和發出的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="a68da-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="a68da-144">和[同盟與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="a68da-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="a68da-145">這個區段包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="a68da-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="a68da-146">如需設定用戶端使用本機簽發者的指示，請參閱[How to： 設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="a68da-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68da-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a68da-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="a68da-148">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a68da-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="a68da-149">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a68da-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a68da-150">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a68da-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a68da-151">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="a68da-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="a68da-152">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="a68da-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="a68da-153">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="a68da-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="a68da-154">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a68da-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
