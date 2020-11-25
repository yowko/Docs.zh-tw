---
title: 重大變更：安全性：已移除 Cookie 名稱編碼
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為安全性：已移除 Cookie 名稱編碼
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3cd40d2b04d0cdf0863e3a3fb6d790c2b35692bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760788"
---
# <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="66cbd-103">安全性：已移除 Cookie 名稱編碼</span><span class="sxs-lookup"><span data-stu-id="66cbd-103">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="66cbd-104">[HTTP cookie 標準](https://tools.ietf.org/html/rfc6265#section-4.1.1)只允許 cookie 名稱和值中的特定字元。</span><span class="sxs-lookup"><span data-stu-id="66cbd-104">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="66cbd-105">若要支援不允許的字元，ASP.NET Core：</span><span class="sxs-lookup"><span data-stu-id="66cbd-105">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="66cbd-106">建立回應 cookie 時進行編碼。</span><span class="sxs-lookup"><span data-stu-id="66cbd-106">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="66cbd-107">在讀取要求 cookie 時解碼。</span><span class="sxs-lookup"><span data-stu-id="66cbd-107">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="66cbd-108">在 ASP.NET Core 5.0 中，此編碼行為會因安全性考慮而改變。</span><span class="sxs-lookup"><span data-stu-id="66cbd-108">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="66cbd-109">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578)。</span><span class="sxs-lookup"><span data-stu-id="66cbd-109">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="66cbd-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="66cbd-110">Version introduced</span></span>

<span data-ttu-id="66cbd-111">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="66cbd-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="66cbd-112">舊的行為</span><span class="sxs-lookup"><span data-stu-id="66cbd-112">Old behavior</span></span>

<span data-ttu-id="66cbd-113">回應 cookie 名稱會經過編碼。</span><span class="sxs-lookup"><span data-stu-id="66cbd-113">Response cookie names are encoded.</span></span> <span data-ttu-id="66cbd-114">要求 cookie 名稱已解碼。</span><span class="sxs-lookup"><span data-stu-id="66cbd-114">Request cookie names are decoded.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="66cbd-115">新的行為</span><span class="sxs-lookup"><span data-stu-id="66cbd-115">New behavior</span></span>

<span data-ttu-id="66cbd-116">已移除 cookie 名稱的編碼和解碼。</span><span class="sxs-lookup"><span data-stu-id="66cbd-116">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="66cbd-117">針對先前 [支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 的 ASP.NET Core 版本，小組計畫就地減輕解碼問題。</span><span class="sxs-lookup"><span data-stu-id="66cbd-117">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="66cbd-118">此外， <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> 使用無效 cookie 名稱呼叫會擲回類型的例外狀況 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="66cbd-118">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="66cbd-119">Cookie 值的編碼和解碼會維持不變。</span><span class="sxs-lookup"><span data-stu-id="66cbd-119">Encoding and decoding of cookie values remains unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="66cbd-120">變更的原因</span><span class="sxs-lookup"><span data-stu-id="66cbd-120">Reason for change</span></span>

<span data-ttu-id="66cbd-121">在 [多個 web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)架構中發現問題。</span><span class="sxs-lookup"><span data-stu-id="66cbd-121">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="66cbd-122">編碼和解碼可能會讓攻擊者透過詐騙保留的前置詞（例如的編碼值）來略過安全性功能，稱為 [cookie 首碼](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) `__Host-` `__%48ost-` 。</span><span class="sxs-lookup"><span data-stu-id="66cbd-122">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="66cbd-123">攻擊需要次要惡意探索，才能在網站中插入詐騙的 cookie，例如跨網站腳本 (XSS) 弱點。</span><span class="sxs-lookup"><span data-stu-id="66cbd-123">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="66cbd-124">ASP.NET Core 或程式庫或範本中預設不會使用這些前置詞 `Microsoft.Owin` 。</span><span class="sxs-lookup"><span data-stu-id="66cbd-124">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="66cbd-125">建議的動作</span><span class="sxs-lookup"><span data-stu-id="66cbd-125">Recommended action</span></span>

<span data-ttu-id="66cbd-126">如果您要將專案移至 ASP.NET Core 5.0 或更新版本，請確定其 cookie 名稱符合 [權杖規格需求](https://tools.ietf.org/html/rfc2616#section-2.2)：不包括控制項和分隔符號的 ASCII 字元 `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` 。</span><span class="sxs-lookup"><span data-stu-id="66cbd-126">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="66cbd-127">在 cookie 名稱或其他 HTTP 標頭中使用非 ASCII 字元，可能會導致伺服器發生例外狀況，或用戶端不正確地進行錯誤的往返。</span><span class="sxs-lookup"><span data-stu-id="66cbd-127">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="66cbd-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="66cbd-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
