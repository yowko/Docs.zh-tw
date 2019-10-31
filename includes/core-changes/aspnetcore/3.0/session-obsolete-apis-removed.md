---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198380"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="d1a0b-101">會話狀態：已移除已淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="d1a0b-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="d1a0b-102">已移除用於設定會話 cookie 的已淘汰 Api。</span><span class="sxs-lookup"><span data-stu-id="d1a0b-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="d1a0b-103">如需詳細資訊，請參閱[aspnet/公告 # 257](https://github.com/aspnet/Announcements/issues/257)。</span><span class="sxs-lookup"><span data-stu-id="d1a0b-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1a0b-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d1a0b-104">Version introduced</span></span>

<span data-ttu-id="d1a0b-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d1a0b-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d1a0b-106">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d1a0b-106">Reason for change</span></span>

<span data-ttu-id="d1a0b-107">這種變更會在 Api 之間強制執行一致性，以設定使用 cookie 的功能。</span><span class="sxs-lookup"><span data-stu-id="d1a0b-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1a0b-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d1a0b-108">Recommended action</span></span>

<span data-ttu-id="d1a0b-109">將已移除 Api 的使用方式遷移至其較新的替代專案。</span><span class="sxs-lookup"><span data-stu-id="d1a0b-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="d1a0b-110">請考慮 `Startup.ConfigureServices` 中的下列範例：</span><span class="sxs-lookup"><span data-stu-id="d1a0b-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

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

#### <a name="category"></a><span data-ttu-id="d1a0b-111">Category</span><span class="sxs-lookup"><span data-stu-id="d1a0b-111">Category</span></span>

<span data-ttu-id="d1a0b-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d1a0b-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1a0b-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d1a0b-113">Affected APIs</span></span>

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
