---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394070"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="5c81c-101">驗證： OAuthHandler ExchangeCodeAsync 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="5c81c-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="5c81c-102">在 ASP.NET Core 3.0 中，`OAuthHandler.ExchangeCodeAsync` 的簽章已從：</span><span class="sxs-lookup"><span data-stu-id="5c81c-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="5c81c-103">收件者:</span><span class="sxs-lookup"><span data-stu-id="5c81c-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="5c81c-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5c81c-104">Version introduced</span></span>

<span data-ttu-id="5c81c-105">3.0</span><span class="sxs-lookup"><span data-stu-id="5c81c-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5c81c-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5c81c-106">Old behavior</span></span>

<span data-ttu-id="5c81c-107">@No__t-0 和 @no__t 1 字串已當做個別引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="5c81c-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5c81c-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="5c81c-108">New behavior</span></span>

<span data-ttu-id="5c81c-109">`Code` 和 `RedirectUri` 是 `OAuthCodeExchangeContext` 的屬性，可以透過 `OAuthCodeExchangeContext` 的函式來設定。</span><span class="sxs-lookup"><span data-stu-id="5c81c-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="5c81c-110">新的 `OAuthCodeExchangeContext` 型別是傳遞給 `OAuthHandler.ExchangeCodeAsync` 的唯一引數。</span><span class="sxs-lookup"><span data-stu-id="5c81c-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5c81c-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="5c81c-111">Reason for change</span></span>

<span data-ttu-id="5c81c-112">這項變更可讓您以不中斷的方式提供其他參數。</span><span class="sxs-lookup"><span data-stu-id="5c81c-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="5c81c-113">不需要建立新的 `ExchangeCodeAsync` 多載。</span><span class="sxs-lookup"><span data-stu-id="5c81c-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5c81c-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5c81c-114">Recommended action</span></span>

<span data-ttu-id="5c81c-115">使用適當的 `code` 和 @no__t 2 值來建立 `OAuthCodeExchangeContext`。</span><span class="sxs-lookup"><span data-stu-id="5c81c-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="5c81c-116">必須提供 <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> 實例。</span><span class="sxs-lookup"><span data-stu-id="5c81c-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="5c81c-117">這個單一 `OAuthCodeExchangeContext` 實例可以傳遞給 `OAuthHandler.ExchangeCodeAsync`，而不是多個引數。</span><span class="sxs-lookup"><span data-stu-id="5c81c-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="5c81c-118">分類</span><span class="sxs-lookup"><span data-stu-id="5c81c-118">Category</span></span>

<span data-ttu-id="5c81c-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c81c-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5c81c-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5c81c-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
