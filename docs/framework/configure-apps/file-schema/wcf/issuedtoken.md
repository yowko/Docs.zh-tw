---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925386"
---
# <a name="issuedtoken"></a><span data-ttu-id="d9b15-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="d9b15-101">\<issuedToken></span></span>
<span data-ttu-id="d9b15-102">指定用來向服務驗證用戶端的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="d9b15-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="d9b15-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d9b15-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9b15-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="d9b15-104">\<behaviors></span></span>  
<span data-ttu-id="d9b15-105">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="d9b15-105">endpointBehaviors section</span></span>  
<span data-ttu-id="d9b15-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="d9b15-106">\<behavior></span></span>  
<span data-ttu-id="d9b15-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d9b15-107">\<clientCredentials></span></span>  
<span data-ttu-id="d9b15-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="d9b15-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b15-109">語法</span><span class="sxs-lookup"><span data-stu-id="d9b15-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9b15-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d9b15-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d9b15-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d9b15-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9b15-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d9b15-112">Attributes</span></span>  
  
|<span data-ttu-id="d9b15-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d9b15-113">Attribute</span></span>|<span data-ttu-id="d9b15-114">描述</span><span class="sxs-lookup"><span data-stu-id="d9b15-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="d9b15-115">選用性的布林值屬性，指定是否快取權杖。</span><span class="sxs-lookup"><span data-stu-id="d9b15-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="d9b15-116">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d9b15-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="d9b15-117">選用性字串屬性，這個屬性會指定交握作業要使用的亂數值 (Entropy)。</span><span class="sxs-lookup"><span data-stu-id="d9b15-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="d9b15-118">值包括 `ClientEntropy`、`ServerEntropy` 與 `CombinedEntropy`，預設為 `CombinedEntropy`。</span><span class="sxs-lookup"><span data-stu-id="d9b15-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="d9b15-119">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。</span><span class="sxs-lookup"><span data-stu-id="d9b15-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="d9b15-120">選用性的整數屬性，這個屬性會指定權杖更新前，可通過的有效時間範圍 (由權杖簽發者提供) 百分比。</span><span class="sxs-lookup"><span data-stu-id="d9b15-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="d9b15-121">值為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="d9b15-121">Values are from 0 to 100.</span></span> <span data-ttu-id="d9b15-122">預設為 60，表示嘗試更新前有 60% 的時間通過。</span><span class="sxs-lookup"><span data-stu-id="d9b15-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="d9b15-123">選用性屬性，這個屬性會指定與簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="d9b15-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="d9b15-124">選用性屬性，這個屬性會指定與本機簽發者通訊時所用的通道行為。</span><span class="sxs-lookup"><span data-stu-id="d9b15-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="d9b15-125">選用性的 Timespan 屬性，當權杖簽發者 (STS) 沒有指定時間時，指定快取發行的權杖之期間。</span><span class="sxs-lookup"><span data-stu-id="d9b15-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="d9b15-126">預設值為 "10675199.02:48: 05.4775807"。</span><span class="sxs-lookup"><span data-stu-id="d9b15-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9b15-127">子元素</span><span class="sxs-lookup"><span data-stu-id="d9b15-127">Child Elements</span></span>  
  
|<span data-ttu-id="d9b15-128">項目</span><span class="sxs-lookup"><span data-stu-id="d9b15-128">Element</span></span>|<span data-ttu-id="d9b15-129">描述</span><span class="sxs-lookup"><span data-stu-id="d9b15-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9b15-130">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="d9b15-130">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="d9b15-131">指定權杖的本機簽發者位址，與用來與端點通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="d9b15-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="d9b15-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="d9b15-132">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="d9b15-133">指定連絡本機簽發者時要使用的端點行為。</span><span class="sxs-lookup"><span data-stu-id="d9b15-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9b15-134">父項目</span><span class="sxs-lookup"><span data-stu-id="d9b15-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d9b15-135">項目</span><span class="sxs-lookup"><span data-stu-id="d9b15-135">Element</span></span>|<span data-ttu-id="d9b15-136">描述</span><span class="sxs-lookup"><span data-stu-id="d9b15-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9b15-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d9b15-137">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="d9b15-138">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="d9b15-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9b15-139">備註</span><span class="sxs-lookup"><span data-stu-id="d9b15-139">Remarks</span></span>  
 <span data-ttu-id="d9b15-140">發行的權杖會在某些情況下當做自訂認證型別使用，例如在聯合案例中與安全權杖服務 (STS) 進行驗證時。</span><span class="sxs-lookup"><span data-stu-id="d9b15-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="d9b15-141">根據預設，這個權杖是 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="d9b15-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="d9b15-142">如需詳細資訊, 請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="d9b15-142">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="d9b15-143">和[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="d9b15-143">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="d9b15-144">這個區段包含用以設定權杖之本機簽發者的項目，或搭配安全性權杖服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="d9b15-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="d9b15-145">如需設定用戶端使用本機簽發者的指示, 請[參閱如何:設定本機簽發者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="d9b15-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b15-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9b15-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="d9b15-147">安全性行為</span><span class="sxs-lookup"><span data-stu-id="d9b15-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d9b15-148">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d9b15-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d9b15-149">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="d9b15-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d9b15-150">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="d9b15-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d9b15-151">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="d9b15-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d9b15-152">如何：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="d9b15-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d9b15-153">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="d9b15-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
