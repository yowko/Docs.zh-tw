---
title: WSTrustChannelFactory 和 WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: ecc62292b2b064219127c369f43141a31ffe606d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034710"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a><span data-ttu-id="92689-102">WSTrustChannelFactory 和 WSTrustChannel</span><span class="sxs-lookup"><span data-stu-id="92689-102">WSTrustChannelFactory and WSTrustChannel</span></span>
<span data-ttu-id="92689-103">如果您已熟悉 Windows Communication Foundation (WCF)，則應該知道 WCF 已是同盟感知用戶端。</span><span class="sxs-lookup"><span data-stu-id="92689-103">If you are already familiar with Windows Communication Foundation (WCF), you know that a WCF client is already federation aware.</span></span> <span data-ttu-id="92689-104">若以 <xref:System.ServiceModel.WSFederationHttpBinding> 或類似的自訂繫結設定 WCF 用戶端，您就可以啟用對服務的同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="92689-104">By configuring a WCF client with a <xref:System.ServiceModel.WSFederationHttpBinding> or similar custom binding, you can enable federated authentication to a service.</span></span>

 <span data-ttu-id="92689-105">WCF 會在背景取得安全性權杖服務 (STS) 發行的權杖，並且使用此權杖對服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="92689-105">WCF obtains the token that is issued by the security token service (STS) behind the scenes and uses this token to authenticate to the service.</span></span> <span data-ttu-id="92689-106">這個方法的主要限制在於無法查看用戶端與伺服器的通訊。</span><span class="sxs-lookup"><span data-stu-id="92689-106">The main limitation to this approach is that there is no visibility into the client’s communications with the server.</span></span> <span data-ttu-id="92689-107">WCF 會根據繫結上發出的權杖參數，自動對 STS 產生要求安全性權杖 (RST)。</span><span class="sxs-lookup"><span data-stu-id="92689-107">WCF automatically generates the request security token (RST) to the STS based on the issued token parameters on the binding.</span></span> <span data-ttu-id="92689-108">這表示用戶端無法改變每個要求的 RST 參數，請檢查要求安全性權杖回應 (RSTR) 以取得顯示宣告這類資訊，或是快取權杖以供未來使用。</span><span class="sxs-lookup"><span data-stu-id="92689-108">This means that the client cannot vary the RST parameters per request, inspect the request security token response (RSTR) to get information such as display claims, or cache the token for future use.</span></span>

 <span data-ttu-id="92689-109">WCF 用戶端目前適用於基本同盟情節。</span><span class="sxs-lookup"><span data-stu-id="92689-109">Currently, the WCF client is suitable for basic federation scenarios.</span></span> <span data-ttu-id="92689-110">不過，Windows Identity Foundation (WIF) 支援的其中一個主要情節需要在某個層級上對 RST 進行控制，而 WCF 不會輕易允許進行這項控制。</span><span class="sxs-lookup"><span data-stu-id="92689-110">However, one of the major scenarios that Windows Identity Foundation (WIF) supports requires control over the RST at a level that WCF does not easily allow.</span></span> <span data-ttu-id="92689-111">因此，WIF 新增了幾項功能，可讓您更充分掌控與 STS 的通訊。</span><span class="sxs-lookup"><span data-stu-id="92689-111">Therefore, WIF adds features that give you more control over communication with the STS.</span></span>

 <span data-ttu-id="92689-112">WIF 支援下列同盟情節：</span><span class="sxs-lookup"><span data-stu-id="92689-112">WIF supports the following federation scenarios:</span></span>

- <span data-ttu-id="92689-113">使用不具任何 WIF 相依性的 WCF 用戶端對同盟服務進行驗證</span><span class="sxs-lookup"><span data-stu-id="92689-113">Using a WCF client without any WIF dependencies to authenticate to a federated service</span></span>

- <span data-ttu-id="92689-114">在 WCF 用戶端上啟用 WIF，將 ActAs 或 OnBehalfOf 元素插入 STS 的 RST</span><span class="sxs-lookup"><span data-stu-id="92689-114">Enabling WIF on a WCF client to insert an ActAs or OnBehalfOf element into the RST to the STS</span></span>

- <span data-ttu-id="92689-115">單獨使用 WIF 從 STS 取得權杖，然後讓 WCF 用戶端使用此權杖進行驗證。</span><span class="sxs-lookup"><span data-stu-id="92689-115">Using WIF alone to obtain a token from the STS and then enable a WCF client to authenticate with this token.</span></span> <span data-ttu-id="92689-116">如需詳細資訊，請參閱 [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) 範例。</span><span class="sxs-lookup"><span data-stu-id="92689-116">For more information, see [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) sample.</span></span>

 <span data-ttu-id="92689-117">第一個案例本身即已說明：現有的 WCF 用戶端將繼續使用 WIF 信賴憑證者和 STS。</span><span class="sxs-lookup"><span data-stu-id="92689-117">The first scenario is self-explanatory: Existing WCF clients will continue to work with WIF relying parties and STSs.</span></span> <span data-ttu-id="92689-118">本主題將討論其餘兩種情節。</span><span class="sxs-lookup"><span data-stu-id="92689-118">This topic discusses the remaining two scenarios.</span></span>

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a><span data-ttu-id="92689-119">使用 ActAs / OnBehalfOf 增強現有的 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="92689-119">Enhancing an Existing WCF Client with ActAs / OnBehalfOf</span></span>
<span data-ttu-id="92689-120">在典型的身分識別委派情節中，用戶端會呼叫中層服務，而中層服務接著會呼叫後端服務。</span><span class="sxs-lookup"><span data-stu-id="92689-120">In a typical identity delegation scenario, a client calls a middle-tier service, which then calls a back-end service.</span></span> <span data-ttu-id="92689-121">中層服務會作為用戶端或以用戶端的身分執行。</span><span class="sxs-lookup"><span data-stu-id="92689-121">The middle-tier service acts as, or acts on behalf of, the client.</span></span>

> [!TIP]
> <span data-ttu-id="92689-122">ActAs 和 OnBehalfOf 之間有何不同？</span><span class="sxs-lookup"><span data-stu-id="92689-122">What is the difference between ActAs and OnBehalfOf?</span></span>
>
> <span data-ttu-id="92689-123">從 Ws-trust 通訊協定的觀點而言：</span><span class="sxs-lookup"><span data-stu-id="92689-123">From the WS-Trust protocol standpoint:</span></span>
>
> 1. <span data-ttu-id="92689-124">ActAs RST 元素指出要求者需要包含有關兩個不同實體之宣告的權杖，這兩個實體是：要求者，以及 ActAs 元素中的權杖所代表的外部實體。</span><span class="sxs-lookup"><span data-stu-id="92689-124">An ActAs RST element indicates that the requestor wants a token that contains claims about two distinct entities: the requestor, and an external entity represented by the token in the ActAs element.</span></span>
> 2. <span data-ttu-id="92689-125">OnBehalfOf RST 元素指出要求者需要只包含有關一個實體之宣告的權杖：OnBehalfOf 元素中的權杖所代表的外部實體。</span><span class="sxs-lookup"><span data-stu-id="92689-125">An OnBehalfOf RST element indicates that the requestor wants a token that contains claims only about one entity: the external entity represented by the token in the OnBehalfOf element.</span></span>
>
> <span data-ttu-id="92689-126">ActAs 功能通常用於需要複合委派的狀況，此時收到發行權杖的最後一位收件者可以檢查整個委派鏈結，而且不只會看到用戶端，而是會看到所有的中繼媒介。</span><span class="sxs-lookup"><span data-stu-id="92689-126">The ActAs feature is typically used in scenarios that require composite delegation, where the final recipient of the issued token can inspect the entire delegation chain and see not just the client, but all intermediaries.</span></span> <span data-ttu-id="92689-127">這樣它便可執行存取控制、稽核工作，以及其他架構在整個身分識別委派鏈結上的相關活動。</span><span class="sxs-lookup"><span data-stu-id="92689-127">This lets it perform access control, auditing and other related activities based on the entire identity delegation chain.</span></span> <span data-ttu-id="92689-128">ActAs 功能一般是在多介層系統中用於在層與層之間驗證和傳遞身分識別相關資訊，而不需要將這項資訊傳遞到應用程式/商務邏輯層。</span><span class="sxs-lookup"><span data-stu-id="92689-128">The ActAs feature is commonly used in multi-tiered systems to authenticate and pass information about identities between the tiers without having to pass this information at the application/business logic layer.</span></span>
>
> <span data-ttu-id="92689-129">在必須使用原始用戶端的身分識別，以便有效執行與 Windows 身分識別模擬功能相同的功能時，就會使用 OnBehalfOf 功能。</span><span class="sxs-lookup"><span data-stu-id="92689-129">The OnBehalfOf feature is used in scenarios where only the identity of the original client is important and is effectively the same as the identity impersonation feature available in Windows.</span></span> <span data-ttu-id="92689-130">使用 OnBehalfOf 時，收到發行權杖的最後一位收件者只會看到有關原始用戶端的宣告，中繼媒介的相關資訊並未加以保留。</span><span class="sxs-lookup"><span data-stu-id="92689-130">When OnBehalfOf is used, the final recipient of the issued token can only see claims about the original client, and the information about intermediaries is not preserved.</span></span> <span data-ttu-id="92689-131">Proxy 模式是 OnBehalfOf 功能常見的一種使用模式，用戶端在這種模式下無法直接存取 STS，而是透過 Proxy 閘道進行通訊。</span><span class="sxs-lookup"><span data-stu-id="92689-131">One common pattern where the OnBehalfOf feature is used is the proxy pattern where the client cannot access the STS directly but instead communicates through a proxy gateway.</span></span> <span data-ttu-id="92689-132">Proxy 閘道會驗證呼叫者，並將該呼叫者的相關資訊放入 RST 訊息的 OnBehalfOf 元素，而該訊息接著會傳送到實際 STS 以進行處理。</span><span class="sxs-lookup"><span data-stu-id="92689-132">The proxy gateway authenticates the caller and puts information about the caller into the OnBehalfOf element of the RST message that it then sends to the real STS for processing.</span></span> <span data-ttu-id="92689-133">結果權杖僅包含與該 Proxy 用戶端相關的宣告，因此可讓 Proxy 完全透明呈現給發行權杖的接收者。請注意，WIF 不支援將 \<wsse:SecurityTokenReference> 或 \<wsa:EndpointReferences> 作為 \<wst:OnBehalfOf> 的子系。</span><span class="sxs-lookup"><span data-stu-id="92689-133">The resulting token contains only claims related to the client of the proxy, making the proxy completely transparent to the receiver of the issued token.Note that WIF does not support \<wsse:SecurityTokenReference> or \<wsa:EndpointReferences> as a child of \<wst:OnBehalfOf>.</span></span> <span data-ttu-id="92689-134">WS-Trust 規格允許使用三種方式來識別原始的要求者 (代表 Proxy 正在運作的用戶端)。</span><span class="sxs-lookup"><span data-stu-id="92689-134">The WS-Trust specification allows for three ways to identify the original requestor (on behalf of whom the proxy is acting).</span></span> <span data-ttu-id="92689-135">這些是：</span><span class="sxs-lookup"><span data-stu-id="92689-135">These are:</span></span>
>
> - <span data-ttu-id="92689-136">安全性權杖參考。</span><span class="sxs-lookup"><span data-stu-id="92689-136">Security token reference.</span></span> <span data-ttu-id="92689-137">權杖的參考出現在訊息中，或可能從頻外取得。</span><span class="sxs-lookup"><span data-stu-id="92689-137">A reference to a token, either in the message, or possibly retrieved out of band).</span></span>
> - <span data-ttu-id="92689-138">端點參考。</span><span class="sxs-lookup"><span data-stu-id="92689-138">Endpoint reference.</span></span> <span data-ttu-id="92689-139">作為用於查詢資料的索引鍵，同樣是在頻外進行。</span><span class="sxs-lookup"><span data-stu-id="92689-139">Used as a key to look up data, again out of band.</span></span>
> - <span data-ttu-id="92689-140">安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="92689-140">Security token.</span></span> <span data-ttu-id="92689-141">直接識別原始的要求者。</span><span class="sxs-lookup"><span data-stu-id="92689-141">Identifies the original requestor directly.</span></span>
>
> <span data-ttu-id="92689-142">WIF 僅支援加密或未加密的安全性權杖作為 \<wst:OnBehalfOf> 的直接子元素。</span><span class="sxs-lookup"><span data-stu-id="92689-142">WIF supports only security tokens, either encrypted or unencrypted, as a direct child element of \<wst:OnBehalfOf>.</span></span>

 <span data-ttu-id="92689-143">這項資訊會使用 RST 中的 ActAs 和 OnBehalfOf 權杖元素傳遞給 WS-Trust 簽發者。</span><span class="sxs-lookup"><span data-stu-id="92689-143">This information is conveyed to a WS-Trust issuer using the ActAs and OnBehalfOf token elements in the RST.</span></span>

 <span data-ttu-id="92689-144">WCF 會在繫結上公開能夠將任意 XML 元素加入至 RST 的擴充點。</span><span class="sxs-lookup"><span data-stu-id="92689-144">WCF exposes an extensibility point on the binding that allows arbitrary XML elements to be added to the RST.</span></span> <span data-ttu-id="92689-145">不過，由於擴充點繫於繫結，因此要求每次呼叫時 RST 內容都要改變的情節，必須針對每次呼叫重新建立用戶端，而這樣做會降低效能。</span><span class="sxs-lookup"><span data-stu-id="92689-145">However, because the extensibility point is tied to the binding, scenarios that require the RST contents to vary per call must re-create the client for every call, which decreases performance.</span></span> <span data-ttu-id="92689-146">WIF 會在 `ChannelFactory` 類別上使用擴充方法，讓開發人員能夠將透過其他方式取得的任何權杖附加至 RST。</span><span class="sxs-lookup"><span data-stu-id="92689-146">WIF uses extension methods on the `ChannelFactory` class to allow developers to attach any token that is obtained out of band to the RST.</span></span> <span data-ttu-id="92689-147">下列程式碼範例示範如何取得代表用戶端的權杖 (例如 X.509、使用者名稱或安全性聲明標記語言 (SAML) 權杖)，並且將該權杖附加至傳送給簽發者的 RST。</span><span class="sxs-lookup"><span data-stu-id="92689-147">The following code example shows how to take a token that represents the client (such as an X.509, username, or Security Assertion Markup Language (SAML) token) and attach it to the RST that is sent to the issuer.</span></span>

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 <span data-ttu-id="92689-148">WIF 提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="92689-148">WIF provides the following benefits:</span></span>

- <span data-ttu-id="92689-149">每個通道的 RST 都可以修改；因此中層服務不必為每個用戶端重新建立通道處理站，這樣就能改善效能。</span><span class="sxs-lookup"><span data-stu-id="92689-149">The RST can be modified per channel; therefore, middle-tier services do not have to re-create the channel factory for each client, which improves performance.</span></span>

- <span data-ttu-id="92689-150">這種方法適用現有的 WCF 用戶端，能為想要啟用身分識別委派語意的現有 WCF 中層服務提供輕鬆升級的管道。</span><span class="sxs-lookup"><span data-stu-id="92689-150">This works with existing WCF clients, which makes an easy upgrade path possible for existing WCF middle-tier services that want to enable identity delegation semantics.</span></span>

 <span data-ttu-id="92689-151">不過，這裡仍然無法查看用戶端與 STS 之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="92689-151">However, there is still no visibility into the client’s communication with the STS.</span></span> <span data-ttu-id="92689-152">我們將在第三個情節中檢視這點。</span><span class="sxs-lookup"><span data-stu-id="92689-152">We’ll examine this in the third scenario.</span></span>

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a><span data-ttu-id="92689-153">與簽發者直接通訊並使用發行的權杖進行驗證</span><span class="sxs-lookup"><span data-stu-id="92689-153">Communicating Directly with an Issuer and Using the Issued Token to Authenticate</span></span>
<span data-ttu-id="92689-154">對於某些進階的情節而言，只是增強 WCF 用戶端是不夠的。</span><span class="sxs-lookup"><span data-stu-id="92689-154">For some advanced scenarios, enhancing a WCF client is not enough.</span></span> <span data-ttu-id="92689-155">僅使用 WCF 的開發人員通常會使用 Message In/Message Out 合約，並且手動處理用戶端的簽發者回應剖析。</span><span class="sxs-lookup"><span data-stu-id="92689-155">Developers who use only WCF typically use Message In / Message Out contracts and handle client-side parsing of the issuer response manually.</span></span>

<span data-ttu-id="92689-156">WIF 引進了 <xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 類別，讓用戶端與 WS-Trust 簽發者能夠直接通訊。</span><span class="sxs-lookup"><span data-stu-id="92689-156">WIF introduces the <xref:System.ServiceModel.Security.WSTrustChannelFactory> and <xref:System.ServiceModel.Security.WSTrustChannel> classes to let the client communicate directly with a WS-Trust issuer.</span></span> <span data-ttu-id="92689-157"><xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 類別可讓強型別 RST 和 RSTR 物件在用戶端與簽發者之間流動，如下列程式碼範例中所示。</span><span class="sxs-lookup"><span data-stu-id="92689-157">The <xref:System.ServiceModel.Security.WSTrustChannelFactory> and <xref:System.ServiceModel.Security.WSTrustChannel> classes enable strongly typed RST and RSTR objects to flow between the client and issuer, as shown in the following code example.</span></span>

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

<span data-ttu-id="92689-158">請注意，<xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> 方法上的 `out` 參數允許存取 RSTR，以便進行用戶端檢查。</span><span class="sxs-lookup"><span data-stu-id="92689-158">Note that the `out` parameter on the <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> method allows access to the RSTR for client-side inspection.</span></span>

<span data-ttu-id="92689-159">到目前為止，您只了解如何取得權杖。</span><span class="sxs-lookup"><span data-stu-id="92689-159">So far, you’ve only seen how to obtain a token.</span></span> <span data-ttu-id="92689-160">從 <xref:System.ServiceModel.Security.WSTrustChannel> 物件傳回的權杖是 `GenericXmlSecurityToken`，其中包含對信賴憑證者進行驗證所需的全部資訊。</span><span class="sxs-lookup"><span data-stu-id="92689-160">The token that is returned from the <xref:System.ServiceModel.Security.WSTrustChannel> object is a `GenericXmlSecurityToken` that contains all of the information that is necessary for authentication to a relying party.</span></span> <span data-ttu-id="92689-161">下列程式碼範例示範如何使用這個權杖。</span><span class="sxs-lookup"><span data-stu-id="92689-161">The following code example shows how to use this token.</span></span>

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

<span data-ttu-id="92689-162">`ChannelFactory` 物件上的 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> 擴充方法會對 WIF 指出，您已透過其他方式取得權杖，因此應該停止對簽發者進行一般 WCF 呼叫，並且改用您取得的權杖對信賴憑證者進行驗證。</span><span class="sxs-lookup"><span data-stu-id="92689-162">The <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> extension method on the `ChannelFactory` object indicates to WIF that you have obtained a token out of band, and that it should stop the normal WCF call to the issuer and instead use the token that you obtained to authenticate to the relying party.</span></span> <span data-ttu-id="92689-163">這具備下列優點：</span><span class="sxs-lookup"><span data-stu-id="92689-163">This has the following benefits:</span></span>

- <span data-ttu-id="92689-164">可讓您完全掌控權杖發行程序。</span><span class="sxs-lookup"><span data-stu-id="92689-164">It gives you complete control over the token issuance process.</span></span>

- <span data-ttu-id="92689-165">透過直接在傳出的 RST 上設定這些屬性的方式支援 ActAs/OnBehalfOf 情節。</span><span class="sxs-lookup"><span data-stu-id="92689-165">It supports ActAs / OnBehalfOf scenarios by directly setting these properties on the outgoing RST.</span></span>

- <span data-ttu-id="92689-166">可根據 RSTR 的內容做出動態用戶端信任的決策。</span><span class="sxs-lookup"><span data-stu-id="92689-166">It enables dynamic client-side trust decisions to be made based on the contents of the RSTR.</span></span>

- <span data-ttu-id="92689-167">可讓您快取和重複使用從 <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> 方法傳回的權杖。</span><span class="sxs-lookup"><span data-stu-id="92689-167">It lets you cache and reuse the token that is returned from the <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> method.</span></span>

- <span data-ttu-id="92689-168"><xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 允許您根據 WCF 的最佳做法控制通道快取、錯誤和復原語意。</span><span class="sxs-lookup"><span data-stu-id="92689-168"><xref:System.ServiceModel.Security.WSTrustChannelFactory> and <xref:System.ServiceModel.Security.WSTrustChannel> allow for control of channel caching, fault, and recovery semantics according to WCF best practices.</span></span>

## <a name="see-also"></a><span data-ttu-id="92689-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92689-169">See also</span></span>

- [<span data-ttu-id="92689-170">WIF 功能</span><span class="sxs-lookup"><span data-stu-id="92689-170">WIF Features</span></span>](../../../docs/framework/security/wif-features.md)