---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032407"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="29813-101">會話狀態：已移除淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="29813-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="29813-102">已移除用來設定會話 cookie 的過時 Api。</span><span class="sxs-lookup"><span data-stu-id="29813-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="29813-103">如需詳細資訊，請參閱 [aspnet/公告 # 257](https://github.com/aspnet/Announcements/issues/257)。</span><span class="sxs-lookup"><span data-stu-id="29813-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="29813-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="29813-104">Version introduced</span></span>

<span data-ttu-id="29813-105">3.0</span><span class="sxs-lookup"><span data-stu-id="29813-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="29813-106">變更的原因</span><span class="sxs-lookup"><span data-stu-id="29813-106">Reason for change</span></span>

<span data-ttu-id="29813-107">這種變更會在 Api 之間強制執行一致性，以設定使用 cookie 的功能。</span><span class="sxs-lookup"><span data-stu-id="29813-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29813-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="29813-108">Recommended action</span></span>

<span data-ttu-id="29813-109">將已移除的 Api 使用方式遷移至其較新的取代。</span><span class="sxs-lookup"><span data-stu-id="29813-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="29813-110">請考慮 `Startup.ConfigureServices` 中的下列範例：</span><span class="sxs-lookup"><span data-stu-id="29813-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(ServiceCollection services)
{
    services.AddSession(options =>
    {
        // Removed obsolete APIs
        options.CookieName = "SessionCookie";
        options.CookieDomain = "contoso.com";
        options.CookiePath = "/";
        options.CookieHttpOnly = true;
        options.CookieSecure = CookieSecurePolicy.Always;

        // new API
        options.Cookie.Name = "SessionCookie";
        options.Cookie.Domain = "contoso.com";
        options.Cookie.Path = "/";
        options.Cookie.HttpOnly = true;
        options.Cookie.SecurePolicy = CookieSecurePolicy.Always;
    });
}
```

#### <a name="category"></a><span data-ttu-id="29813-111">類別</span><span class="sxs-lookup"><span data-stu-id="29813-111">Category</span></span>

<span data-ttu-id="29813-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="29813-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29813-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="29813-113">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieName?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure?displayProperty=fullName>

<!-- 

#### Affected APIs

- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieName`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure`

-->
