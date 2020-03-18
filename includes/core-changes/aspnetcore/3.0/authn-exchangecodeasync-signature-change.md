---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394070"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="f38ac-101">身份驗證：OAuthHandler 交換代碼同步簽名已更改</span><span class="sxs-lookup"><span data-stu-id="f38ac-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="f38ac-102">在 ASP.NET Core 3.0`OAuthHandler.ExchangeCodeAsync`中，的簽名從以下更改為：</span><span class="sxs-lookup"><span data-stu-id="f38ac-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="f38ac-103">變更為：</span><span class="sxs-lookup"><span data-stu-id="f38ac-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="f38ac-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f38ac-104">Version introduced</span></span>

<span data-ttu-id="f38ac-105">3.0</span><span class="sxs-lookup"><span data-stu-id="f38ac-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f38ac-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="f38ac-106">Old behavior</span></span>

<span data-ttu-id="f38ac-107">和`code``redirectUri`字串作為單獨的參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="f38ac-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f38ac-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="f38ac-108">New behavior</span></span>

<span data-ttu-id="f38ac-109">`Code`和`RedirectUri`屬性`OAuthCodeExchangeContext`可以通過`OAuthCodeExchangeContext`建構函式設置。</span><span class="sxs-lookup"><span data-stu-id="f38ac-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="f38ac-110">新`OAuthCodeExchangeContext`類型是傳遞給`OAuthHandler.ExchangeCodeAsync`的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="f38ac-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f38ac-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="f38ac-111">Reason for change</span></span>

<span data-ttu-id="f38ac-112">此更改允許以非中斷方式提供其他參數。</span><span class="sxs-lookup"><span data-stu-id="f38ac-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="f38ac-113">無需創建新`ExchangeCodeAsync`的重載。</span><span class="sxs-lookup"><span data-stu-id="f38ac-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f38ac-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f38ac-114">Recommended action</span></span>

<span data-ttu-id="f38ac-115">構造`OAuthCodeExchangeContext`具有適當`code`和`redirectUri`值的 。</span><span class="sxs-lookup"><span data-stu-id="f38ac-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="f38ac-116">必須<xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties>提供實例。</span><span class="sxs-lookup"><span data-stu-id="f38ac-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="f38ac-117">此單個`OAuthCodeExchangeContext`實例可以傳遞給`OAuthHandler.ExchangeCodeAsync`多個參數，而不是多個參數。</span><span class="sxs-lookup"><span data-stu-id="f38ac-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="f38ac-118">類別</span><span class="sxs-lookup"><span data-stu-id="f38ac-118">Category</span></span>

<span data-ttu-id="f38ac-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f38ac-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f38ac-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f38ac-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
