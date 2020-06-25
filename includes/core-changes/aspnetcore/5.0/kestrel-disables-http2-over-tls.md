---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325228"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="abcb0-101">Kestrel：在不相容的 Windows 版本上，透過 TLS 停用 HTTP/2</span><span class="sxs-lookup"><span data-stu-id="abcb0-101">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="abcb0-102">若要在 Windows 上啟用透過傳輸層安全性（TLS）的 HTTP/2，必須符合兩個需求：</span><span class="sxs-lookup"><span data-stu-id="abcb0-102">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="abcb0-103">從 Windows 8.1 和 Windows Server 2012 R2 開始提供的應用層通訊協定協商（ALPN）支援。</span><span class="sxs-lookup"><span data-stu-id="abcb0-103">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="abcb0-104">一組與 HTTP/2 相容的密碼，從 Windows 10 和 Windows Server 2016 開始提供。</span><span class="sxs-lookup"><span data-stu-id="abcb0-104">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="abcb0-105">因此，在設定 HTTP/2 over TLS 時，Kestrel 的行為已變更為：</span><span class="sxs-lookup"><span data-stu-id="abcb0-105">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="abcb0-106">`Http1` `Information` 當[listenoptions 來. HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols)設定為時，降級為，並在層級記錄訊息 `Http1AndHttp2` 。</span><span class="sxs-lookup"><span data-stu-id="abcb0-106">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="abcb0-107">`Http1AndHttp2` 是 `ListenOptions.HttpProtocols` 的預設值。</span><span class="sxs-lookup"><span data-stu-id="abcb0-107">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="abcb0-108">`NotSupportedException`當設定為時，擲回 `ListenOptions.HttpProtocols` `Http2` 。</span><span class="sxs-lookup"><span data-stu-id="abcb0-108">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="abcb0-109">如需討論，請參閱 issue [dotnet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068)。</span><span class="sxs-lookup"><span data-stu-id="abcb0-109">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="abcb0-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="abcb0-110">Version introduced</span></span>

<span data-ttu-id="abcb0-111">ASP.NET Core 5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="abcb0-111">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="abcb0-112">舊的行為</span><span class="sxs-lookup"><span data-stu-id="abcb0-112">Old behavior</span></span>

<span data-ttu-id="abcb0-113">下表概述透過 TLS 設定 HTTP/2 時的行為。</span><span class="sxs-lookup"><span data-stu-id="abcb0-113">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="abcb0-114">通訊協定</span><span class="sxs-lookup"><span data-stu-id="abcb0-114">Protocols</span></span> | <span data-ttu-id="abcb0-115">Windows 7、</span><span class="sxs-lookup"><span data-stu-id="abcb0-115">Windows 7,</span></span><br /><span data-ttu-id="abcb0-116">Windows Server 2008 R2、</span><span class="sxs-lookup"><span data-stu-id="abcb0-116">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="abcb0-117">或更早版本</span><span class="sxs-lookup"><span data-stu-id="abcb0-117">or earlier</span></span> | <span data-ttu-id="abcb0-118">Windows 8、</span><span class="sxs-lookup"><span data-stu-id="abcb0-118">Windows 8,</span></span><br /><span data-ttu-id="abcb0-119">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="abcb0-119">Windows Server 2012</span></span> | <span data-ttu-id="abcb0-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="abcb0-120">Windows 8.1,</span></span><br /><span data-ttu-id="abcb0-121">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="abcb0-121">Windows Server 2012 R2</span></span> | <span data-ttu-id="abcb0-122">Windows 10、</span><span class="sxs-lookup"><span data-stu-id="abcb0-122">Windows 10,</span></span><br /><span data-ttu-id="abcb0-123">Windows Server 2016、</span><span class="sxs-lookup"><span data-stu-id="abcb0-123">Windows Server 2016,</span></span><br /><span data-ttu-id="abcb0-124">或更新版本</span><span class="sxs-lookup"><span data-stu-id="abcb0-124">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="abcb0-125">放棄`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="abcb0-125">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="abcb0-126">TLS 交握期間發生錯誤</span><span class="sxs-lookup"><span data-stu-id="abcb0-126">Error during TLS handshake</span></span>     | <span data-ttu-id="abcb0-127">TLS 交握期間發生錯誤&ast;</span><span class="sxs-lookup"><span data-stu-id="abcb0-127">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="abcb0-128">沒有錯誤</span><span class="sxs-lookup"><span data-stu-id="abcb0-128">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="abcb0-129">降級為`Http1`</span><span class="sxs-lookup"><span data-stu-id="abcb0-129">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="abcb0-130">降級為`Http1`</span><span class="sxs-lookup"><span data-stu-id="abcb0-130">Downgrade to `Http1`</span></span>     | <span data-ttu-id="abcb0-131">TLS 交握期間發生錯誤&ast;</span><span class="sxs-lookup"><span data-stu-id="abcb0-131">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="abcb0-132">沒有錯誤</span><span class="sxs-lookup"><span data-stu-id="abcb0-132">No error</span></span> |

<span data-ttu-id="abcb0-133">&ast;設定相容的加密套件以啟用這些案例。</span><span class="sxs-lookup"><span data-stu-id="abcb0-133">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="abcb0-134">新的行為</span><span class="sxs-lookup"><span data-stu-id="abcb0-134">New behavior</span></span>

<span data-ttu-id="abcb0-135">下表概述透過 TLS 設定 HTTP/2 時的行為。</span><span class="sxs-lookup"><span data-stu-id="abcb0-135">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="abcb0-136">通訊協定</span><span class="sxs-lookup"><span data-stu-id="abcb0-136">Protocols</span></span> | <span data-ttu-id="abcb0-137">Windows 7、</span><span class="sxs-lookup"><span data-stu-id="abcb0-137">Windows 7,</span></span><br /><span data-ttu-id="abcb0-138">Windows Server 2008 R2、</span><span class="sxs-lookup"><span data-stu-id="abcb0-138">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="abcb0-139">或更早版本</span><span class="sxs-lookup"><span data-stu-id="abcb0-139">or earlier</span></span> | <span data-ttu-id="abcb0-140">Windows 8、</span><span class="sxs-lookup"><span data-stu-id="abcb0-140">Windows 8,</span></span><br /><span data-ttu-id="abcb0-141">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="abcb0-141">Windows Server 2012</span></span> | <span data-ttu-id="abcb0-142">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="abcb0-142">Windows 8.1,</span></span><br /><span data-ttu-id="abcb0-143">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="abcb0-143">Windows Server 2012 R2</span></span> | <span data-ttu-id="abcb0-144">Windows 10、</span><span class="sxs-lookup"><span data-stu-id="abcb0-144">Windows 10,</span></span><br /><span data-ttu-id="abcb0-145">Windows Server 2016、</span><span class="sxs-lookup"><span data-stu-id="abcb0-145">Windows Server 2016,</span></span><br /><span data-ttu-id="abcb0-146">或更新版本</span><span class="sxs-lookup"><span data-stu-id="abcb0-146">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="abcb0-147">放棄`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="abcb0-147">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="abcb0-148">放棄`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="abcb0-148">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="abcb0-149">Throw `NotSupportedException`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="abcb0-149">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="abcb0-150">沒有錯誤</span><span class="sxs-lookup"><span data-stu-id="abcb0-150">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="abcb0-151">降級為`Http1`</span><span class="sxs-lookup"><span data-stu-id="abcb0-151">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="abcb0-152">降級為`Http1`</span><span class="sxs-lookup"><span data-stu-id="abcb0-152">Downgrade to `Http1`</span></span>     | <span data-ttu-id="abcb0-153">降級為 `Http1`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="abcb0-153">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="abcb0-154">沒有錯誤</span><span class="sxs-lookup"><span data-stu-id="abcb0-154">No error</span></span> |

<span data-ttu-id="abcb0-155">&ast;&ast;設定相容的加密套件，並將應用程式內容切換 `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` 為， `true` 以啟用這些案例。</span><span class="sxs-lookup"><span data-stu-id="abcb0-155">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="abcb0-156">變更的原因</span><span class="sxs-lookup"><span data-stu-id="abcb0-156">Reason for change</span></span>

<span data-ttu-id="abcb0-157">這種變更可確保較舊的 Windows 版本上 HTTP/2 over TLS 的相容性錯誤，會儘早且清楚地呈現。</span><span class="sxs-lookup"><span data-stu-id="abcb0-157">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="abcb0-158">建議的動作</span><span class="sxs-lookup"><span data-stu-id="abcb0-158">Recommended action</span></span>

<span data-ttu-id="abcb0-159">請確定在不相容的 Windows 版本上停用 HTTP/2 over TLS。</span><span class="sxs-lookup"><span data-stu-id="abcb0-159">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="abcb0-160">Windows 8.1 和 Windows Server 2012 R2 不相容，因為預設不會有必要的密碼。</span><span class="sxs-lookup"><span data-stu-id="abcb0-160">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="abcb0-161">不過，您可以將電腦設定值更新為使用 HTTP/2 相容的密碼。</span><span class="sxs-lookup"><span data-stu-id="abcb0-161">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="abcb0-162">如需詳細資訊，請參閱[Windows 8.1 中的 TLS 加密套件](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1)。</span><span class="sxs-lookup"><span data-stu-id="abcb0-162">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="abcb0-163">設定好之後，您必須透過設定應用程式內容切換來啟用 Kestrel 上的 HTTP/2 over TLS `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` 。</span><span class="sxs-lookup"><span data-stu-id="abcb0-163">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="abcb0-164">例如：</span><span class="sxs-lookup"><span data-stu-id="abcb0-164">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="abcb0-165">未變更任何基礎支援。</span><span class="sxs-lookup"><span data-stu-id="abcb0-165">No underlying support has changed.</span></span> <span data-ttu-id="abcb0-166">例如，透過 TLS 的 HTTP/2 從未在 Windows 8 或 Windows Server 2012 上運作。</span><span class="sxs-lookup"><span data-stu-id="abcb0-166">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="abcb0-167">這項變更會修改這些不支援案例中的錯誤呈現方式。</span><span class="sxs-lookup"><span data-stu-id="abcb0-167">This change modifies how errors in these unsupported scenarios are presented.</span></span>

#### <a name="category"></a><span data-ttu-id="abcb0-168">類別</span><span class="sxs-lookup"><span data-stu-id="abcb0-168">Category</span></span>

<span data-ttu-id="abcb0-169">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="abcb0-169">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abcb0-170">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="abcb0-170">Affected APIs</span></span>

<span data-ttu-id="abcb0-171">無</span><span class="sxs-lookup"><span data-stu-id="abcb0-171">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
