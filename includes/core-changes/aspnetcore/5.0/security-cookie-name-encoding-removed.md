---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401974"
---
### <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="4f34d-101">安全性：已移除 Cookie 名稱編碼</span><span class="sxs-lookup"><span data-stu-id="4f34d-101">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="4f34d-102">[HTTP cookie 標準](https://tools.ietf.org/html/rfc6265#section-4.1.1)只允許 cookie 名稱和值中的特定字元。</span><span class="sxs-lookup"><span data-stu-id="4f34d-102">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="4f34d-103">若要支援不允許的字元，請 ASP.NET Core：</span><span class="sxs-lookup"><span data-stu-id="4f34d-103">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="4f34d-104">建立回應 cookie 時進行編碼。</span><span class="sxs-lookup"><span data-stu-id="4f34d-104">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="4f34d-105">讀取要求 cookie 時進行解碼。</span><span class="sxs-lookup"><span data-stu-id="4f34d-105">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="4f34d-106">在 ASP.NET Core 5.0 中，此編碼行為會因安全性考慮而變更。</span><span class="sxs-lookup"><span data-stu-id="4f34d-106">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="4f34d-107">如需討論，請參閱 GitHub 問題[dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578)。</span><span class="sxs-lookup"><span data-stu-id="4f34d-107">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4f34d-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4f34d-108">Version introduced</span></span>

<span data-ttu-id="4f34d-109">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="4f34d-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4f34d-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="4f34d-110">Old behavior</span></span>

<span data-ttu-id="4f34d-111">回應 cookie 名稱已編碼。</span><span class="sxs-lookup"><span data-stu-id="4f34d-111">Response cookie names are encoded.</span></span> <span data-ttu-id="4f34d-112">要求 cookie 名稱已解碼。</span><span class="sxs-lookup"><span data-stu-id="4f34d-112">Request cookie names are decoded.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4f34d-113">新的行為</span><span class="sxs-lookup"><span data-stu-id="4f34d-113">New behavior</span></span>

<span data-ttu-id="4f34d-114">已移除 cookie 名稱的編碼和解碼。</span><span class="sxs-lookup"><span data-stu-id="4f34d-114">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="4f34d-115">針對先前[支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)的 ASP.NET Core 版本，小組計畫就地減輕解碼問題的風險。</span><span class="sxs-lookup"><span data-stu-id="4f34d-115">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="4f34d-116">此外，使用不正確 cookie 名稱呼叫，會擲回 <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> 類型的例外狀況 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="4f34d-116">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="4f34d-117">Cookie 值的編碼和解碼會保持不變。</span><span class="sxs-lookup"><span data-stu-id="4f34d-117">Encoding and decoding of cookie values remains unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4f34d-118">變更的原因</span><span class="sxs-lookup"><span data-stu-id="4f34d-118">Reason for change</span></span>

<span data-ttu-id="4f34d-119">在[多個 web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)架構中發現問題。</span><span class="sxs-lookup"><span data-stu-id="4f34d-119">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="4f34d-120">編碼和解碼可能會讓攻擊者藉由詐騙保留的首碼（例如的編碼值）來略過稱為[cookie 首碼](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00)的安全性功能 `__Host-` `__%48ost-` 。</span><span class="sxs-lookup"><span data-stu-id="4f34d-120">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="4f34d-121">攻擊需要次要入侵來插入詐騙 cookie，例如網站中的跨網站腳本（XSS）弱點。</span><span class="sxs-lookup"><span data-stu-id="4f34d-121">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="4f34d-122">在 ASP.NET Core 或程式庫或範本中，預設不會使用這些前置詞 `Microsoft.Owin` 。</span><span class="sxs-lookup"><span data-stu-id="4f34d-122">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f34d-123">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4f34d-123">Recommended action</span></span>

<span data-ttu-id="4f34d-124">如果您要將專案移至 ASP.NET Core 5.0 或更新版本，請確定其 cookie 名稱符合[權杖規格需求](https://tools.ietf.org/html/rfc2616#section-2.2)： ASCII 字元（不含控制項和分隔符號） `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` 。</span><span class="sxs-lookup"><span data-stu-id="4f34d-124">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="4f34d-125">在 cookie 名稱或其他 HTTP 標頭中使用非 ASCII 字元，可能會導致伺服器發生例外狀況，或用戶端不正確地進行迴圈。</span><span class="sxs-lookup"><span data-stu-id="4f34d-125">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

#### <a name="category"></a><span data-ttu-id="4f34d-126">類別</span><span class="sxs-lookup"><span data-stu-id="4f34d-126">Category</span></span>

<span data-ttu-id="4f34d-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4f34d-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f34d-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4f34d-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
