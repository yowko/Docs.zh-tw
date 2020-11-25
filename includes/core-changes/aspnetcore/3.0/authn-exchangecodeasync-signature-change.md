---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032328"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="ebc93-101">驗證： OAuthHandler ExchangeCodeAsync 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="ebc93-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="ebc93-102">在 ASP.NET Core 3.0 中，的簽章 `OAuthHandler.ExchangeCodeAsync` 已變更為：</span><span class="sxs-lookup"><span data-stu-id="ebc93-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="ebc93-103">變更為：</span><span class="sxs-lookup"><span data-stu-id="ebc93-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="ebc93-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ebc93-104">Version introduced</span></span>

<span data-ttu-id="ebc93-105">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc93-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ebc93-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="ebc93-106">Old behavior</span></span>

<span data-ttu-id="ebc93-107">`code`和 `redirectUri` 字串以個別的引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="ebc93-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ebc93-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="ebc93-108">New behavior</span></span>

<span data-ttu-id="ebc93-109">`Code` 和 `RedirectUri` 都是上的屬性，可以透過函式來 `OAuthCodeExchangeContext` 設定 `OAuthCodeExchangeContext` 。</span><span class="sxs-lookup"><span data-stu-id="ebc93-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="ebc93-110">新 `OAuthCodeExchangeContext` 類型是唯一傳遞給的引數 `OAuthHandler.ExchangeCodeAsync` 。</span><span class="sxs-lookup"><span data-stu-id="ebc93-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ebc93-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ebc93-111">Reason for change</span></span>

<span data-ttu-id="ebc93-112">這項變更可讓您以非中斷的方式提供額外的參數。</span><span class="sxs-lookup"><span data-stu-id="ebc93-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="ebc93-113">不需要建立新的多載 `ExchangeCodeAsync` 。</span><span class="sxs-lookup"><span data-stu-id="ebc93-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ebc93-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ebc93-114">Recommended action</span></span>

<span data-ttu-id="ebc93-115">`OAuthCodeExchangeContext`使用適當的 `code` 和值來建立 `redirectUri` 。</span><span class="sxs-lookup"><span data-stu-id="ebc93-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="ebc93-116"><xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties>必須提供實例。</span><span class="sxs-lookup"><span data-stu-id="ebc93-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="ebc93-117">此單一 `OAuthCodeExchangeContext` 實例可以傳遞給， `OAuthHandler.ExchangeCodeAsync` 而不是多個引數。</span><span class="sxs-lookup"><span data-stu-id="ebc93-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="ebc93-118">類別</span><span class="sxs-lookup"><span data-stu-id="ebc93-118">Category</span></span>

<span data-ttu-id="ebc93-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ebc93-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ebc93-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ebc93-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
