---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 83061b283c9430af7bcda9cbc832811fa805ed4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104945"
---
# <a name="issuedtoken"></a><span data-ttu-id="97d6d-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="97d6d-101">\<issuedToken></span></span>
<span data-ttu-id="97d6d-102">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="97d6d-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="97d6d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="97d6d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="97d6d-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="97d6d-104">\<behaviors></span></span>  
<span data-ttu-id="97d6d-105">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="97d6d-105">endpointBehaviors section</span></span>  
<span data-ttu-id="97d6d-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="97d6d-106">\<behavior></span></span>  
<span data-ttu-id="97d6d-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="97d6d-107">\<clientCredentials></span></span>  
<span data-ttu-id="97d6d-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="97d6d-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d6d-109">語法</span><span class="sxs-lookup"><span data-stu-id="97d6d-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97d6d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="97d6d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="97d6d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="97d6d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97d6d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="97d6d-112">Attributes</span></span>  
  
|<span data-ttu-id="97d6d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="97d6d-113">Attribute</span></span>|<span data-ttu-id="97d6d-114">描述</span><span class="sxs-lookup"><span data-stu-id="97d6d-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="97d6d-115">選用性的布林值屬性，指定是否快取權杖。</span><span class="sxs-lookup"><span data-stu-id="97d6d-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="97d6d-116">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="97d6d-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="97d6d-117">選用性字串屬性，這個屬性會指定交握作業要使用的亂數值 (Entropy)。</span><span class="sxs-lookup"><span data-stu-id="97d6d-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="97d6d-118">值包括 `ClientEntropy`、`ServerEntropy` 與 `CombinedEntropy`，預設為 `CombinedEntropy`。</span><span class="sxs-lookup"><span data-stu-id="97d6d-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="97d6d-119">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。</span><span class="sxs-lookup"><span data-stu-id="97d6d-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="97d6d-120">選用性的整數屬性，這個屬性會指定權杖更新前，可通過的有效時間範圍 (由權杖簽發者提供) 百分比。</span><span class="sxs-lookup"><span data-stu-id="97d6d-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="97d6d-121">值為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="97d6d-121">Values are from 0 to 100.</span></span> <span data-ttu-id="97d6d-122">預設為 60，表示嘗試更新前有 60% 的時間通過。</span><span class="sxs-lookup"><span data-stu-id="97d6d-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="97d6d-123">選用性屬性，這個屬性會指定與簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="97d6d-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="97d6d-124">選用性屬性，這個屬性會指定與本機簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="97d6d-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="97d6d-125">選用性的 Timespan 屬性，當權杖簽發者 (STS) 沒有指定時間時，指定快取發行的權杖之期間。</span><span class="sxs-lookup"><span data-stu-id="97d6d-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="97d6d-126">預設值是"10675199.02:48:05.4775807。 」</span><span class="sxs-lookup"><span data-stu-id="97d6d-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97d6d-127">子元素</span><span class="sxs-lookup"><span data-stu-id="97d6d-127">Child Elements</span></span>  
  
|<span data-ttu-id="97d6d-128">項目</span><span class="sxs-lookup"><span data-stu-id="97d6d-128">Element</span></span>|<span data-ttu-id="97d6d-129">描述</span><span class="sxs-lookup"><span data-stu-id="97d6d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97d6d-130">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="97d6d-130">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="97d6d-131">指定權杖的本機簽發者位址，與用來與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="97d6d-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="97d6d-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="97d6d-132">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="97d6d-133">指定連絡本機簽發者時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="97d6d-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97d6d-134">父項目</span><span class="sxs-lookup"><span data-stu-id="97d6d-134">Parent Elements</span></span>  
  
|<span data-ttu-id="97d6d-135">項目</span><span class="sxs-lookup"><span data-stu-id="97d6d-135">Element</span></span>|<span data-ttu-id="97d6d-136">描述</span><span class="sxs-lookup"><span data-stu-id="97d6d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97d6d-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="97d6d-137">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="97d6d-138">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="97d6d-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97d6d-139">備註</span><span class="sxs-lookup"><span data-stu-id="97d6d-139">Remarks</span></span>  
 <span data-ttu-id="97d6d-140">發行的權杖會在某些情況下當做自訂認證型別使用，例如在聯合案例中與安全權杖服務 (STS) 進行驗證時。</span><span class="sxs-lookup"><span data-stu-id="97d6d-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="97d6d-141">根據預設，這個權杖是 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="97d6d-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="97d6d-142">如需詳細資訊，請參閱 <<c0> [ 聯合與發行權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="97d6d-142">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="97d6d-143">並[聯合與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="97d6d-143">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="97d6d-144">這個區段包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="97d6d-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="97d6d-145">如需設定用戶端使用本機簽發者的指示，請參閱[How to:設定本機簽發者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="97d6d-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d6d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97d6d-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="97d6d-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="97d6d-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="97d6d-148">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="97d6d-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="97d6d-149">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="97d6d-149">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="97d6d-150">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="97d6d-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="97d6d-151">如何：建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="97d6d-151">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="97d6d-152">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="97d6d-152">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="97d6d-153">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="97d6d-153">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
