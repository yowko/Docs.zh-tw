---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198380"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="964e0-101">會話狀態：已刪除的已過期 API</span><span class="sxs-lookup"><span data-stu-id="964e0-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="964e0-102">用於配置會話 Cookie 的過時 API 已被刪除。</span><span class="sxs-lookup"><span data-stu-id="964e0-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="964e0-103">有關詳細資訊，請參閱[aspnet/公告#257](https://github.com/aspnet/Announcements/issues/257)。</span><span class="sxs-lookup"><span data-stu-id="964e0-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="964e0-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="964e0-104">Version introduced</span></span>

<span data-ttu-id="964e0-105">3.0</span><span class="sxs-lookup"><span data-stu-id="964e0-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="964e0-106">更改原因</span><span class="sxs-lookup"><span data-stu-id="964e0-106">Reason for change</span></span>

<span data-ttu-id="964e0-107">此更改強制跨 API 配置使用 Cookie 的功能的一致性。</span><span class="sxs-lookup"><span data-stu-id="964e0-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="964e0-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="964e0-108">Recommended action</span></span>

<span data-ttu-id="964e0-109">將已刪除 API 的使用遷移到其較新的替換。</span><span class="sxs-lookup"><span data-stu-id="964e0-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="964e0-110">請考慮 `Startup.ConfigureServices` 中的下列範例：</span><span class="sxs-lookup"><span data-stu-id="964e0-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

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

#### <a name="category"></a><span data-ttu-id="964e0-111">類別</span><span class="sxs-lookup"><span data-stu-id="964e0-111">Category</span></span>

<span data-ttu-id="964e0-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="964e0-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="964e0-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="964e0-113">Affected APIs</span></span>

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
